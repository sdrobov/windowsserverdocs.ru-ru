---
title: Межрегиональная межкластерная репликация хранилища в Azure
description: Межкластерная репликация хранилища cross регион Azure
keywords: Реплика хранилища, диспетчер серверов, Windows Server, Azure, кластер межрегиональная другой регион
author: arduppal
ms.author: arduppal
ms.date: 12/19/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: storage-replica
manager: mchad
ms.openlocfilehash: 41f435c3d537cbfd204dfa869d750b22200deb33
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59891135"
---
# <a name="cluster-to-cluster-storage-replica-cross-region-in-azure"></a>Межрегиональная межкластерная репликация хранилища в Azure
Можно настроить кластер-кластер реплики хранилища для приложений между регионами в Azure. В приведенных ниже примерах мы используем кластер из двух узлов, но реплики хранилища в Межкластерной не ограничены двухузлового кластера. На приведенном ниже рисунке является пространства дисковыми двухузлового кластера, могут взаимодействовать друг с другом в одном домене и которые являются между регионами.

Просмотрите следующий видеоролик, полные пошаговые процесса.
> [!video https://www.microsoft.com/en-us/videoplayer/embed/RE26xeW]

![Архитектура диаграмма с отображением SR C2C в пределах Azure том же регионе.](media\Cluster-to-cluster-azure-cross-region\architecture.png)
> [!IMPORTANT]
> Все примеры, на которую указывает ссылка относятся только к приведенной выше иллюстрации.


1. На портале Azure, создайте [групп ресурсов](https://ms.portal.azure.com/#create/Microsoft.ResourceGroup) в двух разных регионах.

    Например **SR-AZ2AZ** в **Западная часть США 2** и **SR-AZCROSS** в **Центрально-Западная**, как показано выше.

2. Создайте две [группы доступности](https://ms.portal.azure.com/#create/Microsoft.AvailabilitySet-ARM), один в каждой группе ресурсов для каждого кластера
    - Группы доступности (**az2azAS1**) в (**SR-AZ2AZ**)
    - Группы доступности (**azcross-AS**) в (**SR-AZCROSS**)

3. Создать две виртуальные сети
   - Создание [виртуальной сети](https://ms.portal.azure.com/#create/Microsoft.VirtualNetwork-ARM) (**az2az-Vnet**) в первой группы ресурсов (**SR-AZ2AZ**), с одной подсетью и одну подсеть шлюза.
   - Создание [виртуальной сети](https://ms.portal.azure.com/#create/Microsoft.VirtualNetwork-ARM) (**azcross-VNET**) второй группы ресурсов (**SR-AZCROSS**), с одной подсетью и одну подсеть шлюза.

4. Создайте две группы безопасности сети
   - Создание [группы безопасности сети](https://ms.portal.azure.com/#create/Microsoft.NetworkSecurityGroup-ARM) (**az2az-NSG**) в первой группы ресурсов (**SR-AZ2AZ**).
   - Создание [группы безопасности сети](https://ms.portal.azure.com/#create/Microsoft.NetworkSecurityGroup-ARM) (**azcross-NSG**) второй группы ресурсов (**SR-AZCROSS**). 

   Добавьте одно правило безопасности для входящего трафика для RDP:3389 в обе группы безопасности сети. Вы можете удалить это правило после завершения установки.

5. Создание сервера Windows [виртуальных машин](https://ms.portal.azure.com/#create/Microsoft.WindowsServer2016Datacenter-ARM) в группах ранее созданного ресурса.

   Контроллер домена (**az2azDC**). Вы можете создать набор доступности 3-й для контроллера домена или добавить контроллер домена в одном из двух доступности. Если вы добавляете в группу доступности, созданные для двух кластеров, назначьте его стандартный общедоступный IP-адрес во время создания виртуальной Машины.
      - Установите доменные службы Active Directory.
      - Создание домена (contoso.com)
      - Создание пользователя с правами администратора (contosoadmin)

   Создайте две виртуальные машины (**az2az1**, **az2az2**) в группе ресурсов (**SR-AZ2AZ**) с помощью виртуальной сети (**az2az-Vnet**) и Группа безопасности сети (**az2az-NSG**) в группе доступности (**az2azAS1**). Назначьте стандартный общедоступный IP-адрес каждой виртуальной машины во время создания самого.
      - Добавить хотя бы два управляемых дисков для каждой машины
      - Установка отказоустойчивой кластеризации и компонент реплики хранилища

   Создайте две виртуальные машины (**azcross1**, **azcross2**) в группе ресурсов (**SR-AZCROSS**) с помощью виртуальной сети (**azcross-VNET**) и группу безопасности сети (**azcross-NSG**) в группе доступности (**azcross-AS**). Назначить стандартный общедоступный IP-адрес каждой виртуальной машине во время создания самого
      - Добавить по крайней мере два управляемых дисков для каждой машины
      - Установка отказоустойчивой кластеризации и компонент реплики хранилища

   Подключите все узлы к домену и предоставить права администратора для ранее созданного пользователя.

   Сменить сервер DNS виртуальной сети частный IP-адрес домена контроллера.
   - В примере, контроллер домена **az2azDC** имеет частный IP-адрес (10.3.0.8). В виртуальной сети (**az2az-Vnet** и **azcross — виртуальная сеть**) Изменение DNS-сервера 10.3.0.8. 

    В примере подключены все узлы «Contoso.com» и предоставить права администратора для «contosoadmin».
   - Войдите в систему как contosoadmin из всех узлов. 
 
6. Создание кластеров (**SRAZC1**, **SRAZCross**).

   Ниже приведен пример команды PowerShell
   ```powershell
      New-Cluster -Name SRAZC1 -Node az2az1,az2az2 – StaticAddress 10.3.0.100
   ```
   ```powershell
      New-Cluster -Name SRAZCross -Node azcross1,azcross2 – StaticAddress 10.0.0.10
   ```

7. Включите дисковые пространства.

   ```powershell
      Enable-clusterS2D
   ```

   > [!NOTE]
   > Для каждого кластера Создание виртуального диска и тома. Один для данных, а другой для журнала.

8. Создание внутренней SKU "стандартный" [подсистемы балансировки нагрузки](https://ms.portal.azure.com/#create/Microsoft.LoadBalancer-ARM) для каждого кластера (**azlbr1**, **azlbazcross**).

   Укажите адрес IP-адреса кластера как статический частный IP-адрес для подсистемы балансировки нагрузки.
      - azlbr1 => Frontend IP: 10.3.0.100 (взять неиспользуемый IP-адрес из виртуальной сети (**az2az — виртуальная сеть**) подсети)
      - Создайте внутренний пул для каждой подсистемы балансировки нагрузки. Добавьте связанными узлами кластера.
      - Создайте пробу работоспособности: порта 59999
      - Создайте правило балансировки нагрузки: Разрешите портов высокой ДОСТУПНОСТИ с поддержкой плавающего IP-адреса.

   Укажите адрес IP-адреса кластера как статический частный IP-адрес для подсистемы балансировки нагрузки. 
      - azlbazcross = > интерфейсный IP-адрес: 10.0.0.10 (взять неиспользуемый IP-адрес из виртуальной сети (**azcross — виртуальная сеть**) подсети)
      - Создайте внутренний пул для каждой подсистемы балансировки нагрузки. Добавьте связанными узлами кластера.
      - Создайте пробу работоспособности: порта 59999
      - Создайте правило балансировки нагрузки: Разрешите портов высокой ДОСТУПНОСТИ с поддержкой плавающего IP-адреса. 

9. Создание [шлюз виртуальной сети](https://ms.portal.azure.com/#create/Microsoft.VirtualNetworkGateway-ARM) для подключения к сети.

 - Создание первого шлюза виртуальной сети (**az2az VNetGateway**) в первой группы ресурсов (**SR-AZ2AZ**)
 - Тип шлюза = VPN и VPN введите = на основе маршрутов

 - Создание второго шлюза виртуальной сети (**azcross VNetGateway**) второй группы ресурсов (**SR-AZCROSS**)
 - Тип шлюза = VPN и VPN введите = на основе маршрутов

 - Создайте подключение к сети из первого шлюза виртуальной сети для второй шлюз виртуальной сети. Укажите общий ключ

 - Создайте подключение к сети из второй шлюз виртуальной сети, чтобы первый шлюз виртуальной сети. Укажите тот же общий ключ, как указано в предыдущем шаге. 

10. На каждом узле кластера откройте порт 59999 (пробы работоспособности).

   На каждом узле, выполните следующую команду:

   ```powershell
      netsh advfirewall firewall add rule name=PROBEPORT dir=in protocol=tcp action=allow localport=59999 remoteip=any profile=any 
   ```

11. Указание кластера для прослушивания сообщений проверки работоспособности на порта 59999 и ответ от узла, который в данный момент владеет этим ресурсом.

   Запустите его из любой узел кластера, для каждого кластера. 
    
   В нашем примере не забудьте заменить «ILBIP» в соответствии с ваших значений конфигурации. Выполните следующую команду из одного из узлов **az2az1**/**az2az2**

   ```PowerShell
     $ClusterNetworkName = "Cluster Network 1" # Cluster network name (Use Get-ClusterNetwork on Windows Server 2012 or higher to find the name. And use Get-ClusterResource to find the IPResourceName).
     $IPResourceName = "Cluster IP Address" # IP Address cluster resource name.
     $ILBIP = "10.3.0.100" # IP Address in Internal Load Balancer (ILB) - The static IP address for the load balancer configured in the Azure portal.
     [int]$ProbePort = 59999
     Get-ClusterResource $IPResourceName | Set-ClusterParameter -Multiple @{"Address"="$ILBIP";"ProbePort"=$ProbePort;"SubnetMask"="255.255.255.255";"Network"="$ClusterNetworkName";”ProbeFailureThreshold”=5;"EnableDhcp"=0}  
   ```

12. Выполните следующую команду из одного из узлов **azcross1**/**azcross2**
   ```PowerShell
     $ClusterNetworkName = "Cluster Network 1" # Cluster network name (Use Get-ClusterNetwork on Windows Server 2012 or higher to find the name. And use Get-ClusterResource to find the IPResourceName).
     $IPResourceName = "Cluster IP Address" # IP Address cluster resource name.
     $ILBIP = "10.0.0.10" # IP Address in Internal Load Balancer (ILB) - The static IP address for the load balancer configured in the Azure portal.
     [int]$ProbePort = 59999
     Get-ClusterResource $IPResourceName | Set-ClusterParameter -Multiple @{"Address"="$ILBIP";"ProbePort"=$ProbePort;"SubnetMask"="255.255.255.255";"Network"="$ClusterNetworkName";”ProbeFailureThreshold”=5;"EnableDhcp"=0}  
   ```

   Убедитесь в том, что оба кластера можно подключиться и взаимодействовать друг с другом.

   Либо использовать функцию «Подключиться к кластеру» в диспетчере отказоустойчивости кластеров для подключения к другому кластеру, или убедитесь, что другие кластера реагирует в одном из узлов текущего кластера.

   Из примера мы используем:
   ```powershell
      Get-Cluster -Name SRAZC1 (ran from azcross1)
   ```
   ```powershell
      Get-Cluster -Name SRAZCross (ran from az2az1) 
   ```

13. Создайте облако-свидетель для обоих кластеров. Создайте две [учетные записи хранения](https://ms.portal.azure.com/#create/Microsoft.StorageAccount-ARM) (**az2azcw**,**azcrosssa**) в Azure, по одному для каждого кластера в каждой группе ресурсов (**SR-AZ2AZ**,  **SR-AZCROSS**).
   
   - Скопируйте имя учетной записи хранения и ключ из «ключи доступа»
   - Создайте облако-свидетель из «Диспетчер отказоустойчивости кластеров» и используйте выше имя учетной записи и ключа для его создания. 

14. Запустите [тестах для проверки кластеров](../../failover-clustering/create-failover-cluster.md#validate-the-configuration) перед переходом к следующему шагу

15. Запустите Windows PowerShell и используйте командлет [Test-SRTopology](https://docs.microsoft.com/powershell/module/storagereplica/test-srtopology?view=win10-ps), чтобы определить, все ли требования для реплики хранилища выполнены. Этот командлет можно запустить в режиме быстрой проверки требований или в режиме длительной оценки производительности.
 
16. Настройте реплику хранилища для кластера.
Предоставление доступа из одного кластера на другой кластер в обоих направлениях:

   В нашем примере:
   ```powershell
     Grant-SRAccess -ComputerName az2az1 -Cluster SRAZCross
   ```
Если вы используете Windows Server 2016, также выполните следующую команду:

   ```powershell
     Grant-SRAccess -ComputerName azcross1 -Cluster SRAZC1
   ```

17. Создайте SR-партнерство для двух кластеров:</ol>

   - Для кластера **SRAZC1**
      - Местоположение тома:-c:\ClusterStorage\DataDisk1
      - Расположение журнала:-g:
   - Для кластера **SRAZCross**
      - Местоположение тома:-c:\ClusterStorage\DataDiskCross
      - Расположение журнала:-g:

Выполните команду:

```powershell
PowerShell

New-SRPartnership -SourceComputerName SRAZC1 -SourceRGName rg01 -SourceVolumeName c:\ClusterStorage\DataDisk1 -SourceLogVolumeName  g: -DestinationComputerName SRAZCross -DestinationRGName rg02 -DestinationVolumeName c:\ClusterStorage\DataDiskCross -DestinationLogVolumeName  g:
```