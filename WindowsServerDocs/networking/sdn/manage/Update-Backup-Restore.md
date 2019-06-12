---
title: Обновления, резервное копирование и восстановление инфраструктуры SDN
description: В этом разделе вы узнаете, как обновления, резервное копирование и восстановление инфраструктуры SDN.
manager: dougkim
ms.prod: windows-server-threshold
ms.technology: networking-sdn
ms.topic: article
ms.assetid: e9a8f2fd-48fe-4a90-9250-f6b32488b7a4
ms.author: grcusanz
author: shortpatti
ms.date: 08/27/2018
ms.openlocfilehash: 7916377f58261d0ccaa3fa24f135fccca3d5e79b
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66446331"
---
# <a name="upgrade-backup-and-restore-sdn-infrastructure"></a>Обновления, резервное копирование и восстановление инфраструктуры SDN

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе вы узнаете, как обновления, резервное копирование и восстановление инфраструктуры SDN. 

## <a name="upgrade-the-sdn-infrastructure"></a>Обновление инфраструктуры SDN
Инфраструктуры SDN из Windows Server 2016 можно обновить до Windows Server 2019. Порядок обновления выполните же последовательность действий, как уже упоминалось в разделе «Обновление инфраструктуры SDN». До обновления рекомендуется создать резервную копию базы данных сетевого контроллера.

Для машин сетевого контроллера используйте командлет Get-NetworkControllerNode для проверки состояния узла, после завершения обновления. Убедитесь, что узел возвращается на «Вверх» состояния перед обновлением на другие узлы. После обновления всех узлов сетевого контроллера, сетевой контроллер обновляет микрослужб, выполняющихся в кластере сетевого контроллера, в течение часа. Вы можете активировать немедленное обновление с помощью командлета update-networkcontroller. 

Установите те же обновления Windows на всех компонентов операционной системы, системы программно определяемой сети (SDN), которая включает в себя:

- Узлы Hyper-V включена SDN
- Виртуальные машины сетевого контроллера
- Виртуальным машинам мультиплексора подсистемы балансировки нагрузки программного обеспечения
- Виртуальные машины шлюза RAS 

>[!IMPORTANT]
>При использовании виртуального диспетчера System Center, необходимо обновить его с последние накопительные пакеты обновления.

При обновлении каждого компонента, можно использовать любой из стандартных методов для установки обновлений Windows. Тем не менее чтобы сократить время простоя для рабочих нагрузок и целостность базы данных сетевого контроллера, выполните следующие действия:

1. Обновление консолей управления.<p>Установите обновления на всех компьютерах, где используется модуль Powershell для сетевого контроллера.  В том числе в любом наличие NetworkController средства удаленного администрирования сервера, ролью сама по себе. За исключением виртуальные машины сетевого контроллера отдельно. Замените их на следующем шаге.

2. На первой виртуальной Машине контроллера сети установить все обновления и перезапустить.

3. Прежде чем переходить к следующей виртуальной Машины сетевого контроллера, используйте `get-networkcontrollernode` командлет, чтобы проверить состояние узла, обновляются и перезапускаются.

4. В цикле перезагрузки Подождите узле сетевого контроллера вышли из строя и затем восстановлен еще раз.<p>После перезагрузки виртуальной Машины может занять несколько минут, прежде чем он возвращается в **_вверх_** состояния. Пример выходных данных см. в разделе 

5. Установите обновления на каждой виртуальной Машины мультиплексора SLB, один за раз, чтобы обеспечить постоянную доступность инфраструктуры подсистемы балансировки нагрузки.

6. Обновление узлов Hyper-V и шлюзов RAS, начиная с узлами, которые содержат шлюзов удаленного доступа, которые находятся в **Standby** режим.<p>Виртуальные машины шлюза RAS невозможно перенести динамическую без потери подключения клиента. Во время цикла обновления, необходимо соблюдать осторожность свести к минимуму количество клиента подключения отработки отказа в новый шлюз RAS. За счет координированной обновления узлов и шлюзов RAS, каждый клиент выполняет отработку отказа один раз, не более.

    1. Эвакуировать узел виртуальных машин, которые поддерживают динамическую миграцию.<p>Виртуальные машины шлюза RAS должны оставаться на узле.

    2. Установите обновления на каждой виртуальной Машины шлюза на этом узле.

    В. Если обновление требуется шлюз к перезапуску виртуальной Машины, затем перезагрузите виртуальную Машину.  

    Г. Установите обновления на узел, содержащий шлюза виртуальной Машины, который был только что обновили.

    Д. Перезагрузите узел, если это требуется для обновления.

    f. Повторите для каждый дополнительный узел, содержащий резервный шлюз.<p>Если шлюзы не резервный остаются, выполните те же шаги для всех остальных узлов.


### <a name="example-use-the-get-networkcontrollernode-cmdlet"></a>Пример. Используйте командлет get-networkcontrollernode 

В этом примере вы видите выходные данные для `get-networkcontrollernode` командлет запускать из в одном из виртуальные машины сетевого контроллера.  

Находится в состоянии узлы, которые вы видите в приведенном примере:

- NCNode1.contoso.com = Down
- NCNode2.contoso.com = Up
- NCNode3.contoso.com = Up

>[!IMPORTANT]
>Необходимо подождать несколько минут, пока состояние узла изменений в _**вверх**_ перед обновлением дополнительные узлы, по одному.

После обновления всех узлов сетевого контроллера, сетевой контроллер обновляет микрослужб, выполняющихся в кластере сетевого контроллера, в течение часа. 

>[!TIP]
>Вы можете активировать немедленное обновление с помощью `update-networkcontroller` командлета.


```Powershell
PS C:\> get-networkcontrollernode
Name            : NCNode1.contoso.com
Server          : NCNode1.Contoso.com
FaultDomain     : fd:/NCNode1.Contoso.com
RestInterface   : Ethernet
NodeCertificate :
Status          : Down

Name            : NCNode2.Contoso.com
Server          : NCNode2.contoso.com
FaultDomain     : fd:/ NCNode2.Contoso.com
RestInterface   : Ethernet
NodeCertificate :
Status          : Up

Name            : NCNode3.Contoso.com
Server          : NCNode3.Contoso.com
FaultDomain     : fd:/ NCNode3.Contoso.com
RestInterface   : Ethernet
NodeCertificate :
Status          : Up
```

### <a name="example-use-the-update-networkcontroller-cmdlet"></a>Пример. С помощью командлета update-networkcontroller
В этом примере вы видите выходные данные для `update-networkcontroller` для принудительного сетевого контроллера для обновления. 

>[!IMPORTANT]
>Используйте этот командлет, когда у вас есть дополнительные обновления для установки отсутствуют.


```Powershell
PS C:\> update-networkcontroller
NetworkControllerClusterVersion NetworkControllerVersion
------------------------------- ------------------------
10.1.1                          10.1.15
```

## <a name="backup-the-sdn-infrastructure"></a>Резервное копирование инфраструктуры SDN

Регулярное резервное копирование базы данных сетевой контроллер обеспечивает непрерывность бизнес-процессов в случае сбоя или потери данных.  Резервное копирование виртуальные машины сетевого контроллера недостаточно, так как он не гарантирует, что сеанс продолжается на нескольких узлах сетевого контроллера.

**Требования:**
* SMB-ресурса и учетные данные с разрешениями на чтение и запись для общей папки и файловой системы.
* При необходимости можно использовать группы управляемых запись службы (GMSA), если сетевой контроллер был установлен с помощью Управляемой также.

**Процедура.**

1. Используйте метод резервного копирования виртуальной Машины по своему усмотрению, или Hyper-V для экспорта копии каждой виртуальной Машины сетевого контроллера.<p>Резервное копирование виртуальной Машины сетевого контроллера гарантирует, что имеются сертификаты, необходимые для расшифровки базы данных.  

2. При использовании System Center Virtual Machine Manager (SCVMM), остановите службу SCVMM и создать ее резервную копию с помощью SQL Server.<p>Здесь наша цель — гарантировать обновления не получить SCVMM в течение этого времени, в результате может возникнуть несогласованность между сетевым контроллером резервного копирования и SCVMM.  

   >[!IMPORTANT]
   >Не повторно запустить службу SCVMM до завершения резервного копирования сетевого контроллера.

3. Создать резервную копию базы данных сетевого контроллера с `new-networkcontrollerbackup` командлета.

4. Проверка завершения и успешного резервного копирования с `get-networkcontrollerbackup` командлета.

5. Если с использованием диспетчера SCVMM, запустите службу SCVMM.



### <a name="example-backing-up-the-network-controller-database"></a>Пример. Резервное копирование базы данных сетевого контроллера

```Powershell
$URI = "https://NC.contoso.com"
$Credential = Get-Credential

# Get or Create Credential object for File share user

$ShareUserResourceId = "BackupUser"

$ShareCredential = Get-NetworkControllerCredential -ConnectionURI $URI -Credential $Credential | Where {$_.ResourceId -eq $ShareUserResourceId }
If ($ShareCredential -eq $null) {
    $CredentialProperties = New-Object Microsoft.Windows.NetworkController.CredentialProperties
    $CredentialProperties.Type = "usernamePassword"
    $CredentialProperties.UserName = "contoso\alyoung"
    $CredentialProperties.Value = "<Password>"

    $ShareCredential = New-NetworkControllerCredential -ConnectionURI $URI -Credential $Credential -Properties $CredentialProperties -ResourceId $ShareUserResourceId -Force
}

# Create backup

$BackupTime = (get-date).ToString("s").Replace(":", "_")

$BackupProperties = New-Object Microsoft.Windows.NetworkController.NetworkControllerBackupProperties
$BackupProperties.BackupPath = "\\fileshare\backups\NetworkController\$BackupTime"
$BackupProperties.Credential = $ShareCredential

$Backup = New-NetworkControllerBackup -ConnectionURI $URI -Credential $Credential -Properties $BackupProperties -ResourceId $BackupTime -Force
```

### <a name="example-checking-the-status-of-a-network-controller-backup-operation"></a>Пример. Проверка состояния операции резервного копирования сетевого контроллера

```Powershell
PS C:\ > Get-NetworkControllerBackup -ConnectionUri $URI -Credential $Credential -ResourceId $Backup.ResourceId
| ConvertTo-JSON -Depth 10
{
    "Tags":  null,
    "ResourceRef":  "/networkControllerBackup/2017-04-25T16_53_13",
    "InstanceId":  "c3ea75ae-2892-4e10-b26c-a2243b755dc8",
    "Etag":  "W/\"0dafea6c-39db-401b-bda5-d2885ded470e\"",
    "ResourceMetadata":  null,
    "ResourceId":  "2017-04-25T16_53_13",
    "Properties":  {
                    "BackupPath":  "\\\\fileshare\backups\NetworkController\\2017-04-25T16_53_13",
                    "ErrorMessage":  "",
                    "FailedResourcesList":  [

                                            ],
                    "SuccessfulResourcesList":  [
                                                    "/networking/v1/credentials/11ebfc10-438c-4a96-a1ee-8a048ce675be",
                                                    "/networking/v1/credentials/41229069-85d4-4352-be85-034d0c5f4658",
                                                    "/networking/v1/credentials/b2a82c93-2583-4a1f-91f8-232b801e11bb",
                                                    "/networking/v1/credentials/BackupUser",
                                                    "/networking/v1/credentials/fd5b1b96-b302-4395-b6cd-ed9703435dd1",
                                                    "/networking/v1/virtualNetworkManager/configuration",
                                                    "/networking/v1/virtualSwitchManager/configuration",
                                                    "/networking/v1/accessControlLists/f8b97a4c-4419-481d-b757-a58483512640",
                                                    "/networking/v1/logicalnetworks/24fa1af9-88d6-4cdc-aba0-66e38c1a7bb8",
                                                    "/networking/v1/logicalnetworks/48610528-f40b-4718-938e-99c2be76f1e0",
                                                    "/networking/v1/logicalnetworks/89035b49-1ee3-438a-8d7a-f93cbae40619",
                                                    "/networking/v1/logicalnetworks/a9c8eaa0-519c-4988-acd6-11723e9efae5",
                                                    "/networking/v1/logicalnetworks/d4ea002c-c926-4c57-a178-461d5768c31f",
                                                    "/networking/v1/macPools/11111111-1111-1111-1111-111111111111",
                                                    "/networking/v1/loadBalancerManager/config",
                                                    "/networking/v1/publicIPAddresses/2c502b2d-b39a-4be1-a85a-55ef6a3a9a1d",
                                                    "/networking/v1/GatewayPools/Default",
                                                    "/networking/v1/servers/4c4c4544-0058-5810-8056-b4c04f395931",
                                                    "/networking/v1/servers/4c4c4544-0058-5810-8057-b4c04f395931",
                                                    "/networking/v1/servers/4c4c4544-0058-5910-8056-b4c04f395931",
                                                    "/networking/v1/networkInterfaces/058430d3-af43-4328-a440-56540f41da50",
                                                    "/networking/v1/networkInterfaces/08756090-6d55-4dec-98d5-80c4c5a47db8",
                                                    "/networking/v1/networkInterfaces/2175d74a-aacd-44e2-80d3-03f39ea3bc5d",
                                                    "/networking/v1/networkInterfaces/2400c2c3-2291-4b0b-929c-9bb8da55851a",
                                                    "/networking/v1/networkInterfaces/4c695570-6faa-4e4d-a552-0b36ed3e0962",
                                                    "/networking/v1/networkInterfaces/7e317638-2914-42a8-a2dd-3a6d966028d6",
                                                    "/networking/v1/networkInterfaces/834e3937-f43b-4d3c-88be-d79b04e63bce",
                                                    "/networking/v1/networkInterfaces/9d668fe6-b1c6-48fc-b8b1-b3f98f47d508",
                                                    "/networking/v1/networkInterfaces/ac4650ac-c3ef-4366-96e7-d9488fb661ba",
                                                    "/networking/v1/networkInterfaces/b9f23e35-d79e-495f-a1c9-fa626b85ae13",
                                                    "/networking/v1/networkInterfaces/fdd929f1-f64f-4463-949a-77b67fe6d048",
                                                    "/networking/v1/virtualServers/15a891ee-7509-4e1d-878d-de0cb4fa35fd",
                                                    "/networking/v1/virtualServers/57416993-b410-44fd-9675-727cd4e98930",
                                                    "/networking/v1/virtualServers/5f8aebdc-ee5b-488f-ac44-dd6b57bd316a",
                                                    "/networking/v1/virtualServers/6c812217-5931-43dc-92a8-1da3238da893",
                                                    "/networking/v1/virtualServers/d78b7fa3-812d-4011-9997-aeb5ded2b431",
                                                    "/networking/v1/virtualServers/d90820a5-635b-4016-9d6f-bf3f1e18971d",
                                                    "/networking/v1/loadBalancerMuxes/5f8aebdc-ee5b-488f-ac44-dd6b57bd316a_suffix",
                                                    "/networking/v1/loadBalancerMuxes/d78b7fa3-812d-4011-9997-aeb5ded2b431_suffix",
                                                    "/networking/v1/loadBalancerMuxes/d90820a5-635b-4016-9d6f-bf3f1e18971d_suffix",
                                                    "/networking/v1/Gateways/15a891ee-7509-4e1d-878d-de0cb4fa35fd_suffix",
                                                    "/networking/v1/Gateways/57416993-b410-44fd-9675-727cd4e98930_suffix",
                                                    "/networking/v1/Gateways/6c812217-5931-43dc-92a8-1da3238da893_suffix",
                                                    "/networking/v1/virtualNetworks/b3dbafb9-2655-433d-b47d-a0e0bbac867a",
                                                    "/networking/v1/virtualNetworks/d705968e-2dc2-48f2-a263-76c7892fb143",
                                                    "/networking/v1/loadBalancers/24fa1af9-88d6-4cdc-aba0-66e38c1a7bb8_10.127.132.2",
                                                    "/networking/v1/loadBalancers/24fa1af9-88d6-4cdc-aba0-66e38c1a7bb8_10.127.132.3",
                                                    "/networking/v1/loadBalancers/24fa1af9-88d6-4cdc-aba0-66e38c1a7bb8_10.127.132.4"
                                                ],
                    "InProgressResourcesList":  [

                                                ],
                    "ProvisioningState":  "Succeeded",
                    "Credential":  {
                                        "Tags":  null,
                                        "ResourceRef":  "/credentials/BackupUser",
                                        "InstanceId":  "00000000-0000-0000-0000-000000000000",
                                        "Etag":  null,
                                        "ResourceMetadata":  null,
                                        "ResourceId":  null,
                                        "Properties":  null
                                    }
                }
}
```

## <a name="restore-the-sdn-infrastructure-from-a-backup"></a>Восстановление инфраструктуры SDN из резервной копии

При восстановлении из резервной копии все необходимые компоненты SDN среда возвращается в рабочее состояние.  

>[!IMPORTANT]
>Действия зависят от числа компонентов восстановлена.


1. При необходимости, повторное развертывание узлов Hyper-V и хранилище.

2. При необходимости восстановите виртуальные машины сетевого контроллера, виртуальные машины шлюза RAS и виртуальным машинам мультиплексора из резервной копии. 

3. Агент узла Stop сетевого Контроллера и SLB узлов агент на всех узлах Hyper-V.

    ```
    stop-service slbhostagent

    stop-service nchostagent
    ```

4. Остановка виртуальных машин шлюза RAS.

5. Остановите виртуальные машины SLB/Mux.

6. Восстановление сетевого контроллера с `new-networkcontrollerrestore` командлета.

7. Проверка восстановления **ProvisioningState** знать, когда восстановление успешно завершена.

8. Если с использованием диспетчера SCVMM, восстановите базу данных SCVMM с помощью резервной копии, который был создан в то же время, как резервное копирование сетевого контроллера.

9. Если вы хотите восстановить из резервной копии виртуальных машин рабочей нагрузки, сделайте это сейчас.

10. Проверьте работоспособность системы с помощью командлета debug-networkcontrollerconfigurationstate.

```Powershell
$cred = Get-Credential
Debug-NetworkControllerConfigurationState -NetworkController "https://NC.contoso.com" -Credential $cred

Fetching ResourceType:     accessControlLists
Fetching ResourceType:     servers
Fetching ResourceType:     virtualNetworks
Fetching ResourceType:     networkInterfaces
Fetching ResourceType:     virtualGateways
Fetching ResourceType:     loadbalancerMuxes
Fetching ResourceType:     Gateways
```

### <a name="example-restoring-a-network-controller-database"></a>Пример. Восстановление базы данных сетевого контроллера
 
```Powershell
$URI = "https://NC.contoso.com"
$Credential = Get-Credential

$ShareUserResourceId = "BackupUser"
$ShareCredential = Get-NetworkControllerCredential -ConnectionURI $URI -Credential $Credential | Where {$_.ResourceId -eq $ShareUserResourceId }

$RestoreProperties = New-Object Microsoft.Windows.NetworkController.NetworkControllerRestoreProperties
$RestoreProperties.RestorePath = "\\fileshare\backups\NetworkController\2017-04-25T16_53_13"
$RestoreProperties.Credential = $ShareCredential

$RestoreTime = (Get-Date).ToString("s").Replace(":", "_")
New-NetworkControllerRestore -ConnectionURI $URI -Credential $Credential -Properties $RestoreProperties -ResourceId $RestoreTime -Force
```

### <a name="example-checking-the-status-of-a-network-controller-database-restore"></a>Пример. Проверка состояния восстановления базы данных сетевого контроллера

```PowerShell
PS C:\ > get-networkcontrollerrestore -connectionuri $uri -credential $cred -ResourceId $restoreTime | convertto-json -depth 10
{
    "Tags":  null,
    "ResourceRef":  "/networkControllerRestore/2017-04-26T15_04_44",
    "InstanceId":  "22edecc8-a613-48ce-a74f-0418789f04f6",
    "Etag":  "W/\"f14f6b84-80a7-4b73-93b5-59a9c4b5d98e\"",
    "ResourceMetadata":  null,
    "ResourceId":  "2017-04-26T15_04_44",
    "Properties":  {
                    "RestorePath":  "\\\\sa18fs\\sa18n22\\NetworkController\\2017-04-25T16_53_13",
                    "ErrorMessage":  null,
                    "FailedResourcesList":  null,
                    "SuccessfulResourcesList":  null,
                    "ProvisioningState":  "Succeeded",
                    "Credential":  null
                }
}
```


Сведения о сообщения о состоянии конфигурации, которые могут появиться, см. в разделе [Диагностика Windows Server 2016 стека программно-определенные сетевые подключения](https://docs.microsoft.com/windows-server/networking/sdn/troubleshoot/troubleshoot-windows-server-software-defined-networking-stack).