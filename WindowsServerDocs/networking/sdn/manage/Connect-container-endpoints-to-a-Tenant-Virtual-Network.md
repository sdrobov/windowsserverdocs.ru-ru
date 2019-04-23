---
title: Подключение конечных точек контейнера к виртуальной сети клиента
description: В этом разделе мы покажем, как для подключения конечных точек контейнера к существующей клиента виртуальной сети созданы с помощью SDN. Использование l2bridge (и при необходимости l2tunnel) драйвер сети, доступные с помощью подключаемого модуля libnetwork Windows для Docker, создайте сеть контейнера на виртуальную Машину клиента.
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
ms.date: 08/24/2018
ms.openlocfilehash: 1968a4db9231459fe5858d9a0f3ba5e8f317ed1b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59872745"
---
# <a name="connect-container-endpoints-to-a-tenant-virtual-network"></a>Подключение конечных точек контейнера к виртуальной сети клиента

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе мы покажем, как для подключения конечных точек контейнера к существующей клиента виртуальной сети созданы с помощью SDN. Использовании *l2bridge* (и при необходимости *l2tunnel*) драйвер сети, доступные с помощью подключаемого модуля libnetwork Windows для Docker, создайте сеть контейнера на виртуальную Машину клиента.

В [контейнера сетевые драйверы](https://docs.microsoft.com/virtualization/windowscontainers/container-networking/network-drivers-topologies) разделе мы рассмотрели несколько сетевых драйверов доступны через Docker в Windows. SDN, использовать *l2bridge* и *l2tunnel* драйверы. Для обоих драйверов каждая конечная точка контейнера находится в той же виртуальной подсети, как виртуальная машина узла (клиент) контейнера. 

Узел сети службы (HNS), через подключаемый модуль частного облака, сетевому интерфейсу динамически назначается IP-адресов для конечных точек контейнера. Конечные точки контейнера имеют уникальные IP-адреса, но совместно использовать одинаковый MAC-адрес контейнера узла (клиент) виртуальной машины из-за преобразования адресов второго уровня. 

Политики сети (списки управления доступом, инкапсуляцию и QoS) для этих конечных точек контейнера имеют принудительно в физическом узле Hyper-V, по мере получения сетевым контроллером и определены в системах управления верхнего уровня. 

Разница между *l2bridge* и *l2tunnel* драйверы:

| l2bridge | l2tunnel |
| --- | --- |
|Конечные точки контейнера, которые находятся на: <ul><li>Тот же контейнер размещения виртуальной машины и в той же подсети имеют весь сетевой трафик между виртуального коммутатора Hyper-V. </li><li>Другой контейнер размещения виртуальных машин или в разных подсетях их трафик, перенаправленный на физический узел Hyper-V. </li></ul>Политики сети не применяются, так как сетевой трафик между контейнерами на одном узле и в той же подсети не перемещается в физическом узле. Политики сети применяется только для кросс узла или между подсетями контейнера сетевого трафика. | *ВСЕ* сетевой трафик между двумя конечными точками контейнера перенаправляется на физический узел Hyper-V, независимо от узла или подсети. Политики сети применяется к сетевой трафик между подсетями и кросс host. |
---

>[!NOTE]
>Эти сетевые режимы не работают для подключающегося конечные точки контейнера windows в виртуальной сети клиента в общедоступное облако Azure.


## <a name="prerequisites"></a>предварительные требования
-  Развернутой инфраструктуре SDN с помощью сетевого контроллера.
-  Виртуальной сети клиента будет создана.
-  Развернутый клиент виртуальной машины с контейнерами Windows включен, установленный Docker и включена функция Hyper-V. Компонент Hyper-V является обязательным для установки несколько двоичных файлов для сетей l2bridge и l2tunnel.

   ```powershell
   # To install HyperV feature without checks for nested virtualization
   dism /Online /Enable-Feature /FeatureName:Microsoft-Hyper-V /All 
   ```

>[!Note]
>[Вложенная виртуализация](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/nesting) и предоставление расширения виртуализации является не обязательным, если с помощью контейнеров Hyper-V. 


## <a name="workflow"></a>Рабочий процесс

[1. Добавить несколько IP-конфигураций для существующего ресурса сетевой КАРТЫ виртуальной Машины через сетевой контроллер (узел Hyper-V)](#1-add-multiple-ip-configurations)
[2. Включить прокси-сервер сети на узле, чтобы выделить ЦС IP-адресов для конечных точек контейнера (узел Hyper-V) ](#2-enable-the-network-proxy) 
 [3. Установка подключаемого модуля для назначения адресов IP ак конечные точки контейнера (виртуальной Машины узла контейнера) частного облака ](#3-install-the-private-cloud-plug-in) 
 [4. Создание *l2bridge* или *l2tunnel* сети с помощью docker (виртуальной Машины узла контейнера) ](#4-create-an-l2bridge-container-network)
 
>[!NOTE]
>Несколько IP-конфигураций не поддерживается на сетевой Адаптер виртуальной Машины ресурсы, созданные через System Center Virtual Machine Manager. Для этих типов развертываний рекомендуется создавать ресурс сетевой КАРТЫ виртуальной Машины вне диапазона, с помощью сетевого контроллера PowerShell.

### <a name="1-add-multiple-ip-configurations"></a>1. Добавить несколько IP-конфигураций
На этом шаге мы предполагаем, сетевому Адаптеру виртуальной Машины на виртуальную машину клиента имеет один IP-конфигурации с IP-адресом 192.168.1.9 и подключен к «VNet1» идентификатор ресурса виртуальной сети и подсети ресурса виртуальной Машины из подсети «1» в IP-подсети 192.168.1.0/24. Мы добавим 10 IP-адресов для контейнеров из 192.168.1.101 - 192.168.1.110.

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

### <a name="2-enable-the-network-proxy"></a>2. Включение сетевой прокси-сервер
В этом шаге вы включите сетевой прокси-сервер выделить несколько IP-адресов для виртуальной машины узла контейнера. 

Чтобы включить сетевой прокси-сервер, запустите [ConfigureMCNP.ps1](https://github.com/Microsoft/SDN/blob/master/Containers/ConfigureMCNP.ps1) -скрипта на **узла Hyper-V** размещена виртуальная машина контейнера узла (клиента).

```powershell
PS C:\> ConfigureMCNP.ps1
```

### <a name="3-install-the-private-cloud-plug-in"></a>3. Установка подключаемого модуля частного облака
На этом шаге вы установить подключаемый модуль позволяет HNS для связи с прокси-сервер сети на узле Hyper-V.

Чтобы установить подключаемый модуль, запустите [InstallPrivateCloudPlugin.ps1](https://github.com/Microsoft/SDN/blob/master/Containers/InstallPrivateCloudPlugin.ps1) скрипта внутри **виртуальная машина узла (клиент) контейнера**.


```powershell
PS C:\> InstallPrivateCloudPlugin.ps1
```

### <a name="4-create-an-l2bridge-container-network"></a>4. Создание *l2bridge* сеть контейнера
На этом шаге используется `docker network create` команды **виртуальная машина узла (клиент) контейнера** для создания сети l2bridge. 

```powershell
# Create the container network
C:\> docker network create -d l2bridge --subnet="192.168.1.0/24" --gateway="192.168.1.1" MyContainerOverlayNetwork

# Attach a container to the MyContainerOverlayNetwork 
C:\> docker run -it --network=MyContainerOverlayNetwork <image> <cmd>
```

>[!NOTE]
>Назначение статических IP-адресов не поддерживается с *l2bridge* или *l2tunnel* сетей контейнера при использовании со стеком Microsoft SDN.

## <a name="more-information"></a>Дополнительные сведения
Дополнительные сведения о развертывании инфраструктуры SDN см. в разделе [развертывание инфраструктуры программно-определяемой сети](https://docs.microsoft.com/windows-server/networking/sdn/deploy/deploy-a-software-defined-network-infrastructure).

