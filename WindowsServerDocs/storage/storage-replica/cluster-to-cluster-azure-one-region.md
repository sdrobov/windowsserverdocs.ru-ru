---
title: Межкластерная реплики хранилища в том же регионе, в Azure
description: Межкластерная репликация хранилища в том же регионе, в Azure
keywords: Реплика хранилища, диспетчер серверов, Windows Server, Azure, кластер, том же регионе
author: arduppal
ms.author: arduppal
ms.date: 04/26/2019
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: storage-replica
manager: mchad
ms.openlocfilehash: 4371192d44878d3c953374b8d307b4d5612869f5
ms.sourcegitcommit: 7e54a1bcd31cd2c6b18fd1f21b03f5cfb6165bf3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461978"
---
# <a name="cluster-to-cluster-storage-replica-within-the-same-region-in-azure"></a>Межкластерная реплики хранилища в том же регионе, в Azure

> Относится к: Windows Server 2019 г., Windows Server 2016, Windows Server (Semi-Annual Channel)

Вы можете настроить репликацию кластера для кластера хранилища в одном регионе, в Azure. В приведенных ниже примерах мы используем кластер из двух узлов, но реплики хранилища в межкластерной не ограничены двухузлового кластера. На приведенном ниже рисунке является пространства дисковыми двухузлового кластера, могут взаимодействовать друг с другом, находятся в том же домене, а также в одном регионе.

Смотреть видео ниже полные пошаговые процесса.

В первой части
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE26f2Y]

Часть 2
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE269Pq]

![Схема архитектуры, демонстрации реплики хранилища кластер кластер в Azure в том же регионе.](media\Cluster-to-cluster-azure-one-region\architecture.png)
> [!IMPORTANT]
> Все примеры, на которую указывает ссылка относятся только к приведенной выше иллюстрации.

1. Создание [группы ресурсов](https://ms.portal.azure.com/#create/Microsoft.ResourceGroup) на портале Azure в регионе (**SR-AZ2AZ** в **Западная часть США 2**). 
2. Создайте две [группы доступности](https://ms.portal.azure.com/#create/Microsoft.AvailabilitySet-ARM) в группе ресурсов (**SR-AZ2AZ**) выше, созданной для каждого кластера. 
    1. Группы доступности (**az2azAS1**) b. Группы доступности (**az2azAS2**)
3. Создание [виртуальной сети](https://ms.portal.azure.com/#create/Microsoft.VirtualNetwork-ARM) (**az2az-Vnet**) в группе ресурсов, ранее созданный (**SR-AZ2AZ**), наличие хотя бы одну подсеть. 
4. Создание [группы безопасности сети](https://ms.portal.azure.com/#create/Microsoft.NetworkSecurityGroup-ARM) (**az2az-NSG**) и добавьте одно правило безопасности для входящего трафика для RDP:3389. Вы можете удалить это правило после завершения установки. 
5. Создание сервера Windows [виртуальных машин](https://ms.portal.azure.com/#create/Microsoft.WindowsServer2016Datacenter-ARM) в ранее созданной группе ресурсов (**SR-AZ2AZ**). Используйте ранее созданную виртуальную сеть (**az2az-Vnet**) и группу безопасности сети (**az2az-NSG**). 
   
   Контроллер домена (**az2azDC**). Вы можете создать третьей группе доступности для контроллера домена или добавить контроллер домена в одном из двух наборов доступности. Если вы добавляете в группу доступности, созданные для двух кластеров, назначьте его стандартный общедоступный IP-адрес во время создания виртуальной Машины. 
   - Установите доменные службы Active Directory.
   - Создание домена (Contoso.com)
   - Создание пользователя с правами администратора (contosoadmin) 
   - Создайте две виртуальные машины (**az2az1**, **az2az2**) в группе доступности первой (**az2azAS1**). Назначьте стандартный общедоступный IP-адрес каждой виртуальной машины во время создания самого.
   - Добавить хотя бы 2 управляемых дисков для каждой машины
   - Установите компонент отказоустойчивой кластеризации и реплике хранилища
   - Создайте две виртуальные машины (**az2az3**, **az2az4**) в группе доступности второй (**az2azAS2**). Назначьте стандартный общедоступный IP-адрес каждой виртуальной машины во время создания самого. 
   - Добавьте хотя бы 2 управляемого диска на каждом компьютере. 
   - Установите компонент отказоустойчивой кластеризации и реплике хранилища. 
   
6. Подключите все узлы к домену и предоставить права администратора для ранее созданного пользователя. 

7. Сменить сервер DNS виртуальной сети частный IP-адрес домена контроллера. 
8. В нашем примере, контроллер домена **az2azDC** имеет частный IP-адрес (10.3.0.8). В виртуальной сети (**az2az — виртуальная сеть**) Изменение DNS-сервера 10.3.0.8. Подключите все узлы «Contoso.com» и предоставить права администратора для «contosoadmin».
   - Войдите в систему как contosoadmin из всех узлов. 
    
9. Создание кластеров (**SRAZC1**, **SRAZC2**). Ниже приведен команды PowerShell для нашего примера
```PowerShell
    New-Cluster -Name SRAZC1 -Node az2az1,az2az2 –StaticAddress 10.3.0.100
```
```PowerShell
    New-Cluster -Name SRAZC2 -Node az2az3,az2az4 –StaticAddress 10.3.0.101
```
10. Включить дисковые пространства
```PowerShell
    Enable-clusterS2D
```   
   
   Для каждого кластера Создание виртуального диска и тома. Один для данных, а другой для журнала. 
   
11. Создание внутренней SKU "стандартный" [подсистемы балансировки нагрузки](https://ms.portal.azure.com/#create/Microsoft.LoadBalancer-ARM) для каждого кластера (**azlbr1**,**azlbr2**). 
   
   Укажите адрес IP-адреса кластера как статический частный IP-адрес для подсистемы балансировки нагрузки.
   - azlbr1 => Frontend IP: 10.3.0.100 (взять неиспользуемый IP-адрес из виртуальной сети (**az2az — виртуальная сеть**) подсети)
   - Создайте внутренний пул для каждой подсистемы балансировки нагрузки. Добавьте связанными узлами кластера.
   - Создайте пробу работоспособности: порта 59999
   - Создайте правило балансировки нагрузки: Разрешите портов высокой ДОСТУПНОСТИ с поддержкой плавающего IP-адреса. 
   
   Укажите адрес IP-адреса кластера как статический частный IP-адрес для подсистемы балансировки нагрузки.
   - azlbr2 => Frontend IP: 10.3.0.101 (взять неиспользуемый IP-адрес из виртуальной сети (**az2az — виртуальная сеть**) подсети)
   - Создайте внутренний пул для каждой подсистемы балансировки нагрузки. Добавьте связанными узлами кластера.
   - Создайте пробу работоспособности: порта 59999
   - Создайте правило балансировки нагрузки: Разрешите портов высокой ДОСТУПНОСТИ с поддержкой плавающего IP-адреса. 
   
12. На каждом узле кластера откройте порт 59999 (пробы работоспособности). 
   
    На каждом узле, выполните следующую команду:
```PowerShell
netsh advfirewall firewall add rule name=PROBEPORT dir=in protocol=tcp action=allow localport=59999 remoteip=any profile=any 
```   
13. Указание кластера для прослушивания сообщений проверки работоспособности на порта 59999 и ответ от узла, который в данный момент владеет этим ресурсом. Запустите его из любой узел кластера, для каждого кластера. 
    
    В нашем примере не забудьте заменить «ILBIP» в соответствии с ваших значений конфигурации. Выполните следующую команду из одного из узлов **az2az1**/**az2az2**:

    ```PowerShell
     $ClusterNetworkName = "Cluster Network 1" # Cluster network name (Use Get-ClusterNetwork on Windows Server 2012 or higher to find the name. And use Get-ClusterResource to find the IPResourceName).
     $IPResourceName = "Cluster IP Address" # IP Address cluster resource name.
     $ILBIP = "10.3.0.100" # IP Address in Internal Load Balancer (ILB) - The static IP address for the load balancer configured in the Azure portal.
     [int]$ProbePort = 59999
     Get-ClusterResource $IPResourceName | Set-ClusterParameter -Multiple @{"Address"="$ILBIP";"ProbePort"=$ProbePort;"SubnetMask"="255.255.255.255";"Network"="$ClusterNetworkName";”ProbeFailureThreshold”=5;"EnableDhcp"=0}
    ```

14. Выполните следующую команду из одного из узлов **az2az3**/**az2az4**. 

    ```PowerShell
    $ClusterNetworkName = "Cluster Network 1" # Cluster network name (Use Get-ClusterNetwork on Windows Server 2012 or higher to find the name. And use Get-ClusterResource to find the IPResourceName).
    $IPResourceName = "Cluster IP Address" # IP Address cluster resource name.
    $ILBIP = "10.3.0.101" # IP Address in Internal Load Balancer (ILB) - The static IP address for the load balancer configured in the Azure portal.
    [int]$ProbePort = 59999
    Get-ClusterResource $IPResourceName | Set-ClusterParameter -Multiple @{"Address"="$ILBIP";"ProbePort"=$ProbePort;"SubnetMask"="255.255.255.255";"Network"="$ClusterNetworkName";”ProbeFailureThreshold”=5;"EnableDhcp"=0}  
    ```   
   Убедитесь в том, что оба кластера можно подключиться и взаимодействовать друг с другом. 

   Либо использовать функцию «Подключиться к кластеру» в диспетчере отказоустойчивости кластеров для подключения к другому кластеру, или убедитесь, что другие кластера реагирует в одном из узлов текущего кластера.  
   
   ```PowerShell
     Get-Cluster -Name SRAZC1 (ran from az2az3)
   ```
   ```PowerShell
     Get-Cluster -Name SRAZC2 (ran from az2az1)
   ```   

15. Создание облачных следящие серверы для обоих кластерах. Создайте две [учетные записи хранения](https://ms.portal.azure.com/#create/Microsoft.StorageAccount-ARM) (**az2azcw**, **az2azcw2**) в azure для каждого кластера в ту же группу ресурсов (**SR-AZ2AZ**).

    - Скопируйте имя учетной записи хранения и ключ из «ключи доступа»
    - Создайте облако-свидетель из «Диспетчер отказоустойчивости кластеров» и используйте выше имя учетной записи и ключа для его создания.

16. Запустите [тестах для проверки кластеров](../../failover-clustering/create-failover-cluster.md#validate-the-configuration) перед переходом к следующему шагу.

17. Запустите Windows PowerShell и используйте командлет [Test-SRTopology](https://docs.microsoft.com/powershell/module/storagereplica/test-srtopology?view=win10-ps), чтобы определить, все ли требования для реплики хранилища выполнены. Командлет можно использовать в режиме только для требований для быстрой проверки, а также режим оценки производительности выполняющейся длительное время.

18. Настройте реплику хранилища для кластера.
   
   Предоставление доступа из одного кластера на другой кластер в обоих направлениях:

   В нашем примере:

   ```PowerShell
      Grant-SRAccess -ComputerName az2az1 -Cluster SRAZC2
   ```
Если вы используете Windows Server 2016, также выполните следующую команду:

   ```PowerShell
      Grant-SRAccess -ComputerName az2az3 -Cluster SRAZC1
   ```   
   
19. Создайте SRPartnership для кластеров:</ol>

 - Для кластера **SRAZC1**.
   - Местоположение тома:-c:\ClusterStorage\DataDisk1
   - Расположение журнала:-g:
 - Для кластера **SRAZC2**
    - Местоположение тома:-c:\ClusterStorage\DataDisk2
    - Расположение журнала:-g:

Выполните следующую команду:

```PowerShell

New-SRPartnership -SourceComputerName SRAZC1 -SourceRGName rg01 -SourceVolumeName c:\ClusterStorage\DataDisk1 -SourceLogVolumeName  g: -DestinationComputerName **SRAZC2** -DestinationRGName rg02 -DestinationVolumeName c:\ClusterStorage\DataDisk2 -DestinationLogVolumeName  g:
```