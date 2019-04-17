---
title: Подключения контейнеров к виртуальной сети
description: Этот раздел является частью программного обеспечения определены сетевые руководство о том, как управление рабочими нагрузками клиента и виртуальные сети в Windows Server 2016.
manager: ravirao
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7af1eb6-d035-4f74-a25b-d4b7e4ea9329
ms.author: pashort
author: jmesser81
ms.openlocfilehash: 801cf4b8f71935eb72d820d47e523a310fa64562
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="connect-container-endpoints-to-a-tenant-virtual-network"></a>Подключение конечных точек контейнера к виртуальной сети клиента

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе показано, как для подключения конечных точек контейнера к существующей виртуальной сети клиента, созданное с помощью стека Microsoft программного обеспечения определяемая сеть (SDN). Мы будем использовать *l2bridge* (и при необходимости *l2tunnel*) драйвер с надстройкой libnetwork Windows для Docker для создания контейнера сети на виртуальной машине (клиент) узла контейнера.

Как описано в [сети контейнера](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/management/container_networking) разделе на сайте MSDN нескольких сетевых драйверов доступны через Docker в Windows. Драйверы являются драйверами, наиболее подходящий для SDN *l2bridge* и *l2tunnel*. Для обоих драйверы каждая конечная точка контейнера находится в одной виртуальной подсети в виртуальной машине узла (клиентов) контейнера. IP-адреса для конечных точек контейнера назначаются динамически по сети служба узлов (HNS) через подключаемый модуль частного облака. Конечные точки контейнера имеют уникальный IP-адреса, но имеют одинаковый MAC-адрес виртуальной машине узла (клиентов) контейнера, из-за преобразования адресов второго уровня. Сетевой политики (например: списки управления доступом, инкапсуляция и качество обслуживания) для эти конечные точки контейнера имеют принудительно применяться на физическом узле Hyper-V, как полученных сетевой контроллер и определены в системы управления верхнего уровня. Существует небольшие различия между *l2bridge* и *l2tunnel* драйверы, как описано ниже.

- **Режим моста L2** -конечные точки контейнера, которые располагаются в той же виртуальной машине узла контейнера и находятся в одной подсети имеют весь сетевой трафик между виртуального коммутатора Hyper-V. Конечные точки контейнера, расположенных на другой узел контейнера виртуальные машины или находящихся в разных подсетях имеют их трафика, отправляемого на физическом узле Hyper-V. Поскольку сетевого трафика между контейнерами на одном узле и в той же подсети не переходит на физическом узле, политика сети не применяется. Политика применяется только для сетевой трафик контейнеров кросс host или между подсетями.  
 
- **Туннельный режим L2** - *все* сетевой трафик между двумя конечными точками контейнера перенаправляется на физическом узле Hyper-V независимо от узла или подсети. Политики сети применяется для сетевого трафика между подсетями и кросс host.   

>[!NOTE]
>Эти сетевые режимы не работают для подключения конечных точек контейнера windows в виртуальную сеть клиента в общедоступное облако Azure

## <a name="prerequistes"></a>Условия
 * Была развернута инфраструктура SDN с помощью сетевого контроллера
 * Будет создан виртуальную сеть клиента
 * Виртуальная машина клиента развернут с включенной функцией контейнера Windows, Docker установлена и включена функция Hyper-V

>[!Note]
>[Вложенная виртуализация](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/nesting) и предоставление расширения виртуализации не требуется, если только с помощью функции Hyper-V контейнеры Hyper-v требуется установить несколько двоичных файлов в сетях l2bridge и l2tunnel

```powershell
# To install HyperV feature without checks for nested virtualization
dism /Online /Enable-Feature /FeatureName:Microsoft-Hyper-V /All 
```

 

## <a name="workflow"></a>Рабочий процесс

1. [Добавить несколько IP-конфигурации на существующий ресурс сетевой Адаптер виртуальной Машины посредством сетевого контроллера](#Add) (узла Hyper-V)
2. [Включение сетевого прокси-сервера на узле, чтобы выделить ЦС IP-адреса для конечных точек контейнера](#Enable) (узла Hyper-V) 
3. [Установка частного облака, подключаемый модуль, чтобы присвоить ЦС IP-адреса конечных точек контейнера](#Install) (виртуальной Машины узла контейнера) 
4. [Создание *l2bridge* или *l2tunnel* сети с помощью docker](#Create) (виртуальной Машины узла контейнера) 
 
>[!NOTE]
>Несколько IP-конфигурации, не поддерживается на сетевой Адаптер виртуальной Машины ресурсы, созданные до System Center Virtual Machine Manager. Для этих типов развертывания рекомендуется создавать ресурс сетевой Адаптер виртуальной Машины аппаратный контроллер управления с помощью сетевого контроллера PowerShell.

### <a name="Add"></a>1. Добавьте несколько IP-конфигурации

В этом примере предполагается, что сетевой Адаптер виртуальной Машины из виртуальной машины клиента уже имеет один IP-конфигурации с IP-адресом 192.168.1.9 и присоединен к VNet идентификатор ресурса «VNet1» и «Subnet1» ресурс подсети виртуальных Машин в 192.168.1.0/24 IP-подсети. Мы будем добавлять 10 IP-адресов для контейнеров из 192.168.1.101 - 192.168.1.110.

```powershell
Import-Module NetworkController

# Specify Network Controller REST IP or FQDN
$uri = "<NC REST IP or FQDN>"
$vnetResourceId = "VNet1"
$vsubnetResourceId = "Subnet1"

$vmnic= Get-NetworkControllerNetworkInterface -ConnectionUri $uri | where {$_.properties.IpConfigurations.Properties.PrivateIPAddress -eq "192.168.1.9" }
$vmsubnet = Get-NetworkControllerVirtualSubnet -VirtualNetworkId $vnetResourceId -ResourceId $vsubnetResourceId -ConnectionUri $uri

# For this demo, we will assume an ACL has already been defined; any ACL can be applied here
$allowallacl = Get-NetworkControllerAccessControlList -ConnectionUri $uri -ResourceId "AllowAll"


foreach ($i in 1..10)
{
    $newipconfig = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfiguration
    $props = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfigurationProperties

    $resourceid = "IP_192_168_1_1"
    if ($i -eq 10) 
    {
        $resourceid += "10"
        $ipstr = "192.168.1.110"
    }
    else
    {
        $resourceid += "0$i"
        $ipstr = "192.168.1.10$i"
    }
    
    $newipconfig.ResourceId = $resourceid
    $props.PrivateIPAddress = $ipstr    
    
    $props.PrivateIPAllocationMethod = "Static"
    $props.Subnet = new-object Microsoft.Windows.NetworkController.Subnet
    $props.Subnet.ResourceRef = $vmsubnet.ResourceRef
    $props.AccessControlList = new-object Microsoft.Windows.NetworkController.AccessControlList
    $props.AccessControlList.ResourceRef = $allowallacl.ResourceRef

    $newipconfig.Properties = $props
    $vmnic.Properties.IpConfigurations += $newipconfig
}

New-NetworkControllerNetworkInterface -ResourceId $vmnic.ResourceId -Properties $vmnic.Properties -ConnectionUri $uri
```

### <a name="Enable"></a>2. Включение сетевого прокси-сервера

[ConfigureMCNP.ps1](https://github.com/Microsoft/SDN/blob/master/Containers/ConfigureMCNP.ps1>)

Запустите этот сценарий **узла Hyper-V** которой размещается виртуальная машина узла (клиентов) контейнера для включения сетевого прокси-сервера выделить несколько IP-адресов для виртуальной машины узла контейнера.

```powershell
PS C:\> ConfigureMCNP.ps1
```

### <a name="Install"></a>3. Установка подключаемого модуля частного облака

[InstallPrivateCloudPlugin.ps1](https://github.com/Microsoft/SDN/blob/master/Containers/InstallPrivateCloudPlugin.ps1)

Запустите этот сценарий внутри **виртуальной машине узла (клиентов) контейнера** позволяет сети служба узлов (HNS) для связи с сетевого прокси-сервера на узле Hyper-V.

```powershell
PS C:\> InstallPrivateCloudPlugin.ps1
```

### <a name="Create"></a>4. Создание *l2bridge* сеть контейнера

На **виртуальной машине узла (клиентов) контейнера** использовать `docker network create` команду для создания сети l2bridge

```powershell
# Create the container network
C:\> docker network create -d l2bridge --subnet="192.168.1.0/24" --gateway="192.168.1.1" MyContainerOverlayNetwork

# Attach a container to the MyContainerOverlayNetwork 
C:\> docker run -it --network=MyContainerOverlayNetwork <image> <cmd>
```

>[!NOTE]
>Назначение статических IP-адресов не поддерживается в *l2bridge* или *l2tunnel* сетей контейнера при использовании со стеком Microsoft SDN.

## <a name="more-information"></a>Дополнительные сведения
Дополнительные infortation о развертывании инфраструктуры SDN см [развертывание инфраструктуры программно-определенные сети](https://technet.microsoft.com/en-us/windows-server-docs/networking/sdn/deploy/deploy-a-software-defined-network-infrastructure).

