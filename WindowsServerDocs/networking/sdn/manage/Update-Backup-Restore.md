---
title: "Обновления, резервного копирования и восстановления программного обеспечения инфраструктура конфигурируемой сети"
description: "Этот раздел является частью программного обеспечения определены сети руководство о том, как инфраструктуры обновления, резервное копирование и восстановление SDN в Windows Server 2016."
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-sdn
ms.topic: article
ms.assetid: e9a8f2fd-48fe-4a90-9250-f6b32488b7a4
ms.author: grcusanz
author: grcusanz
ms.openlocfilehash: bb7194ec865db980962853b87d68a84a5446269e
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="update-backup-and-restore-software-defined-networking-infrastructure"></a>Обновления, резервного копирования и восстановления программного обеспечения инфраструктура конфигурируемой сети

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Этот раздел содержит следующие разделы.

- [Обновление инфраструктуры SDN](#bkmk_Updating)
- [Резервное копирование инфраструктуры SDN](#bkmk_backup)
- [Восстановление из резервной копии инфраструктуры SDN](#bkmk_restore)

## <a name="bkmk_Updating"></a>Обновление инфраструктуры SDN

Обновление — это процесс установки обновлений Windows на всех компонентов операционной системы, системы программно-конфигурируемые сети (SDN).  Это включает в себя SDN включена узлов Hyper-V, виртуальных машин сетевой контроллер, программного обеспечения балансировки нагрузки Mux, виртуальные машины и виртуальные машины шлюза RAS-сервера.  Очень важно, что все эти компоненты имеют одинаковые наборы установленные обновления.  Если используется System Center Virtual Machine Manager также рекомендуется также обновить его с последние накопительные пакеты обновления также.

Обновления каждого компонента выполняется с помощью стандартных методов для установки обновлений windows, тем не менее действия, описанные ниже необходимо выполнить для обеспечения минимальный простоев для рабочих нагрузок и для обеспечения целостности базы данных сетевого контроллера.

### <a name="step-1-update-the-management-consoles"></a>Шаг 1: Обновление консолей управления
Установите необходимые обновления на всех компьютерах, где вы используете модуль Powershell сетевого контроллера.  Это включает в себя в любом наличие RSAT NetworkController ролью само по себе.  Это не не включая самих контроллера сети виртуальных машин, как они будут обновлены в шаге 2.

### <a name="step-2-update-the-network-controllers"></a>Шаг 2: Обновление контроллеров сети
Это является наиболее важным этапом в цикле обновления, поскольку каждой виртуальной Машины контроллера сети должны быть обновлены и будет полностью восстановлена, в кластере сетевой контроллер перед переходом к следующему.

Начните с одной виртуальной Машиной контроллер сети и установите все необходимые обновления.  Перезапустите виртуальную Машину, при необходимости.

Перед переходом к следующему виртуальной Машины контроллера сети использовать get-networkcontrollernode для проверки состояния узла, который был обновлен и перезагрузки.  Подождите, пока узел сетевой контроллер отключается во время цикла перезагрузки и затем вернуться еще раз.  После перезагрузки виртуальной Машины, он по-прежнему может занять несколько минут для того, чтобы вернуться в состояние вверх.

#### <a name="example-using-get-networkcontrollernode-to-check-the-status-of-network-controller-nodes"></a>Пример: С помощью get-networkcontrollernode для проверки состояния сетевого контроллера узлов

В этом примере показаны выходные данные get-networkcontrollernode из одного контроллера сети виртуальных машин под управлением.  Она показывает, что NCNode1.contoso.com не работает, а два других узлах находятся в работоспособном состоянии.  Необходимо подождать несколько минут до состояния, для изменения этого узла до продолжения обновления дополнительные узлы.

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

Только после все узлы сетевой контроллер находятся в состоянии вверх можно можно повторить эти действия для всех дополнительных узлов сетевого контроллера.  Продолжайте обновлять каждый узел, одной за раз.

После обновления всех узлов сетевой контроллер сетевой контроллер обновит микрослужбами, работающие в кластере сетевого контроллера в течение одного часа.  Вы можете активировать немедленного обновления с помощью командлета update-networkcontroller.

#### <a name="example-using-update-networkcontroller-to-force-network-controller-to-update"></a>Пример Использования networkcontroller обновления, чтобы принудительно обновить сетевой контроллер

Эта команда показывает результат networkcontroller обновления, когда не осталось для установки обновлений.

```Powershell
PS C:\> update-networkcontroller
NetworkControllerClusterVersion NetworkControllerVersion
------------------------------- ------------------------
10.1.1                          10.1.15
```

### <a name="step-3-update-slb-muxes"></a>Шаг 3: Обновление SLB Muxes

Установите обновления на каждой виртуальной Машины с мультиплексированием SLB один во время, чтобы обеспечить постоянную доступность инфраструктуры подсистемы балансировки нагрузки.

### <a name="step-4-update-hyper-v-hosts-and-ras-gateways"></a>Шаг 4: Обновление узлов Hyper-V и шлюзов RAS.

Так как виртуальные машины шлюза RAS-сервера не удается выполнить динамическую миграцию без потери подключения клиента, чтобы свести к минимуму количество раз, клиентов, подключения не будет выполнен по для нового шлюзов RAS во время цикла обновления необходимо уделить внимание.  Координирует обновления узлов и шлюзов RAS каждого клиента будет только отработка отказа не более одного раза.  

Выполните следующие действия для каждого узла, начиная с узлов, которые содержат шлюзов RAS, которые в режиме ожидания.

1.  Эвакуируйте узлов виртуальных машин, которые поддерживают динамическую миграцию.  Виртуальные машины шлюза RAS-сервера должно оставаться на узле.
2.  Установите обновления на каждой виртуальной Машины шлюза на этом узле.
3.  Если шлюз виртуальной Машины, чтобы перезагрузить, а затем перезагрузите виртуальную Машину, требуется обновление.  
4.  Установите обновления на узел, содержащий шлюз виртуальной Машины, который только что был обновлен.
5.  Перезагрузите узел, при необходимости обновления.
6.  Повторите для каждого дополнительных узла, содержащего ожидания шлюза.  Если остаются без ожидания шлюзы, выполните такие же действия для всех остальных узлов.

## <a name="bkmk_backup"></a>Резервное копирование инфраструктуры SDN

Регулярное создание резервных копий базы данных контроллера сети критически важны для обеспечения непрерывности бизнес-процессов в случае сбоя или потери данных.  Резервное копирование виртуальных машин контроллера сети недостаточно, так как он не убедитесь, что что кворума сохраняется по нескольким узлам сетевого контроллера.
Существуют следующие требования:
 * Общий ресурс SMB и учетные данные с разрешениями чтения и записи к ресурсу и файловой системы.
 * Если сетевой контроллер была установлена с использованием групповой управляемой учетной записи также можно дополнительно использовать группы управляемых учетная запись службы (GMSA).

Выполните следующие действия для создания резервной копии.

1. Резервное копирование виртуальные машины контроллера сети, используя метод резервного копирования виртуальных Машин по вашему выбору, и позволяет экспортировать копию каждой виртуальной Машины контроллера сети Hyper-V.  Это гарантирует, что выполняется полного перестроения, включая восстановление инфраструктуры виртуальных машин, сертификатов, необходимых для расшифровки базы данных, присутствуют ли.
2. Если вы используете System Center Virtual Machine Manager (SCVMM), остановите службу SCVMM и создать его резервную копию через SQL Server, чтобы убедиться, что в SCVMM обновления не вносятся в течение этого времени, создающие несогласованность резервного копирования сетевой контроллер и SCVMM.  Не повторно запустите службу SCVMM до завершения резервного копирования сетевого контроллера.
3. Создайте резервную копию базы данных сетевого контроллера, с помощью нового networkcontrollerbackup.

 #### <a name="example-backing-up-the-network-controller-database"></a>Пример: Резервное копирование базы данных сетевого контроллера
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

4. Используйте get-networkcontrollerbackup для проверки выполнения и успешностью резервной копии.

 #### <a name="example-checking-the-status-of-a-network-controller-backup-operation"></a>Пример: Проверка состояния сетевого контроллера операции резервного копирования

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

5.  Если использует SCVMM теперь вы можете начать SCVMM службы.

## <a name="bkmk_restore"></a>Восстановление из резервной копии инфраструктуры SDN

Восстановление — это процесс восстановления всех необходимых компонентов из резервной копии для возврата среды SDN в операционное состояние.  Действия будет немного меняться в зависимости от объема компоненты, которые подлежат восстановлению.

1. При необходимости повторного развертывания узлов Hyper-V и хранилище.

2. При необходимости восстановите из резервной копии виртуальных машин сетевой контроллер, виртуальные машины шлюза RAS-сервера и виртуальные машины с мультиплексированием. 

3. Остановить агент узла контекста Именования и SLB агента узла на всех узлах Hyper-V

    ```
    stop-service slbhostagent

    stop-service nchostagent
    ```

4. Остановить виртуальные машины шлюза RAS-сервера

5. Остановить ВМ мультиплексора SLB

6. Восстановление сетевого контроллера с помощью командлета новый networkcontrollerrestore.

 #### <a name="example-restoring-a-network-controller-database"></a>Пример: Восстановление базы данных сетевого контроллера
 
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

7. Проверьте восстановления ProvisioningState знать, когда восстановления успешно завершена.

 #### <a name="example-checking-the-status-of-a-network-controller-database-restore"></a>Пример: Проверка состояния восстановления базы данных сетевого контроллера

    ```
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

8. Если использует SCVMM, восстановите базу данных SCVMM, с помощью резервной копии, которая была создана в то же время, как резервное копирование сетевого контроллера.

9. Если рабочая нагрузка виртуальные машины восстанавливается из резервной копии, можно сделать это сейчас.

10. Используйте командлет debug-networkcontrollerconfigurationstate для проверки работоспособности системы.

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

Сведения о конфигурации сообщений о состоянии, могут отображаться в разделе [Диагностика Windows Server 2016 стека программно-определенные сетевые](https://docs.microsoft.com/windows-server/networking/sdn/troubleshoot/troubleshoot-windows-server-software-defined-networking-stack).