---
title: Со схождением конфигурации сетевого Адаптера с одним сетевым адаптером
description: В этом разделе мы предоставляют инструкции для настройки сетевых Адаптеров со схождением с одним сетевым Адаптером на узле Hyper-V.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: eed5c184-fa55-43a8-a879-b1610ebc70ca
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/14/2018
ms.openlocfilehash: 93d317534af46c87c4b2e874a5a5475687e2efa0
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66447067"
---
# <a name="converged-nic-configuration-with-a-single-network-adapter"></a>Со схождением конфигурации сетевого Адаптера с одним сетевым адаптером

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе мы предоставляют инструкции для настройки сетевых Адаптеров со схождением с одним сетевым Адаптером на узле Hyper-V.

Пример конфигурации в этом разделе описаны два узла Hyper-V, **узла Hyper-V A**, и **Hyper-V Host B**. Они имеют один физический сетевой Адаптер (pNIC) установлен, и сетевых адаптеров, подключенных к верхней части стойки \(ToR\) физическом коммутаторе. Кроме того узлы, находятся в той же подсети, который является 192.168.1.x/24.

![Узлы Hyper-V.](../../media/Converged-NIC/1-single-test-conn.jpg)


## <a name="step-1-test-the-connectivity-between-source-and-destination"></a>Шаг 1. Проверьте возможность подключения между источником и назначением

Подключите физический сетевой Адаптер на узел назначения. Данный тест демонстрирует подключение с помощью третьего уровня \(L3\) - или уровень IP - а также уровня 2 \(L2\).

1. Просмотр свойств сетевого адаптера.

   ```PowerShell
   Get-NetAdapter
   ```

   _**Результаты:** _  


   | Имя |    InterfaceDescription     | ifIndex | Состояние |    macAddress     | Скорость линии |
   |------|-----------------------------|---------|--------|-------------------|-----------|
   |  M1  | Mellanox ConnectX-3 Pro ... |    4    |   Вверх   | 7C-FE-90-93-8F-A1 |  40 Гбит/с  |

   ---

2. Просмотр свойств дополнительный сетевой адаптер, включая IP-адрес.

   ```PowerShell
   Get-NetAdapter M1 | fl *
   ```

   _**Результаты:** _

   ```PowerShell   
    MacAddress   : 7C-FE-90-93-8F-A1
    Status   : Up
    LinkSpeed: 40 Gbps
    MediaType: 802.3
    PhysicalMediaType: 802.3
    AdminStatus  : Up
    MediaConnectionState : Connected
    DriverInformation: Driver Date 2016-08-28 Version 5.25.12665.0 NDIS 6.60
    DriverFileName   : mlx4eth63.sys
    NdisVersion  : 6.60
    ifOperStatus : Up
    ifAlias  : M1
    InterfaceAlias   : M1
    ifIndex  : 4
    ifDesc   : Mellanox ConnectX-3 Pro Ethernet Adapter
    ifName   : ethernet_32773
    DriverVersion: 5.25.12665.0
    LinkLayerAddress : 7C-FE-90-93-8F-A1
    Caption  :
    Description  :
    ElementName  :
    InstanceID   : {39B58B4C-8833-4ED2-A2FD-E105E7146D43}
    CommunicationStatus  :
    DetailedStatus   :
    HealthState  :
    InstallDate  :
    Name : M1
    OperatingStatus  :
    OperationalStatus:
    PrimaryStatus:
    StatusDescriptions   :
    AvailableRequestedStates :
    EnabledDefault   : 2
    EnabledState : 5
    OtherEnabledState:
    RequestedState   : 12
    TimeOfLastStateChange:
    TransitioningToState : 12
    AdditionalAvailability   :
    Availability :
    CreationClassName: MSFT_NetAdapter
   ``` 

## <a name="step-2-ensure-that-source-and-destination-can-communicate"></a>Шаг 2. Источник и назначение могли обмениваться данными

На этом шаге мы используем **Test-NetConnection** команды Windows PowerShell, однако если вы можете использовать **ping** команды, если вы предпочитаете. 

>[!TIP]
>Если вы не уверены, что узлы могут взаимодействовать друг с другом, этот шаг можно пропустить.

1. Проверьте двунаправленный обмен данными.

   ```PowerShell
   Test-NetConnection 192.168.1.5
   ```

   _**Результаты:** _


   |        Параметр         |    Значение    |
   |--------------------------|-------------|
   |       имя_компьютера       | 192.168.1.5 |
   |      RemoteAddress       | 192.168.1.5 |
   |      InterfaceAlias      |     M1      |
   |      SourceAddress       | 192.168.1.3 |
   |      PingSucceeded       |    True     |
   | PingReplyDetails \(время приема-Передачи\) |    0 мс     |

   ---

   В некоторых случаях может потребоваться отключить брандмауэр Windows в режиме повышенной безопасности, для успешного выполнения этого теста. Если вы отключите брандмауэр, имейте в виду безопасности и убедитесь, что конфигурацию соответствует требованиям безопасности вашей организации.

2. Отключите все профили брандмауэра.

   ```PowerShell
   Set-NetFirewallProfile -All -Enabled False
   ```

3. После отключения в профилях брандмауэра, повторите проверку. 

   ```PowerShell
   Test-NetConnection 192.168.1.5
   ```

   _**Результаты:** _


   |        Параметр         |    Значение    |
   |--------------------------|-------------|
   |       имя_компьютера       | 192.168.1.5 |
   |      RemoteAddress       | 192.168.1.5 |
   |      InterfaceAlias      | Test-40G-1  |
   |      SourceAddress       | 192.168.1.3 |
   |      PingSucceeded       |    False    |
   | PingReplyDetails \(время приема-Передачи\) |    0 мс     |

   ---



## <a name="step-3-optional-configure-the-vlan-ids-for-nics-installed-in-your-hyper-v-hosts"></a>Шаг 3. (Необязательно) Настройка идентификаторов виртуальной локальной сети для сетевых адаптеров, которые установлены на узлах Hyper-V

Множество конфигураций сети с помощью виртуальных локальных сетей, и если вы планируете использовать виртуальные локальные сети в вашей сети, необходимо повторить предыдущий тест настроен виртуальные ЛС. Кроме того Если вы планируете использовать RoCE для служб RDMA необходимо включить виртуальные локальные сети.

Для выполнения этого шага сетевые адаптеры, находятся в **доступа** режим. Тем не менее, при создании виртуального коммутатора Hyper-V \(vSwitch\) далее в этом руководстве свойства виртуальной ЛС применяются на уровне порта виртуального коммутатора. 

Так как переключатель можно разместить несколько виртуальных ЛС, это необходимо для верхнего \(ToR\) физического коммутатора, чтобы обеспечить порт, который узел подключен к настроен магистральный режим.

>[!NOTE]
>Инструкции по настройке магистральный режим на коммутаторе обратитесь к документации коммутатора ToR.

На следующем рисунке показаны два узла Hyper-V, каждый из которых один физический сетевой адаптер, и каждый из которых настроен для передачи данных на 101 виртуальной локальной сети.

![Настройка виртуальных локальных сетей](../../media/Converged-NIC/2-single-configure-vlans.jpg)


>[!IMPORTANT]
>Выполните на серверах, как локальных, так и назначения. Если конечный сервер не имеет тот же идентификатор виртуальной локальной сети, что и локальный сервер, два не могут обмениваться данными.


1. Настройте идентификатор виртуальной сети для сетевых адаптеров, которые установлены на узлах Hyper-V.

   >[!IMPORTANT]
   >Не выполнить эту команду при подключении к узлу удаленно через этот интерфейс, так как это приводит к утрате доступа к узлу.

   ```PowerShell
   Set-NetAdapterAdvancedProperty -Name M1 -RegistryKeyword VlanID -RegistryValue "101"
   Get-NetAdapterAdvancedProperty -Name M1 | Where-Object {$_.RegistryKeyword -eq "VlanID"} 
   ```

   _**Результаты:** _


   | Имя | DisplayName | DisplayValue | RegistryKeyword | RegistryValue |
   |------|-------------|--------------|-----------------|---------------|
   |  M1  |   ИД виртуальной ЛС   |     101      |     VlanID      |     {101}     |

   ---

2. Перезапустите сетевой адаптер для применения ИД виртуальной ЛС.

   ```PowerShell
   Restart-NetAdapter -Name "M1"
   ```

3. Убедитесь, находится в состоянии **вверх**.

   ```PowerShell
   Get-NetAdapter -Name "M1"
   ```

   _**Результаты:** _


   | Имя |          InterfaceDescription           | ifIndex | Состояние |    macAddress     | Скорость линии |
   |------|-----------------------------------------|---------|--------|-------------------|-----------|
   |  M1  | Mellanox ConnectX-3 Pro Ethernet Ada... |    4    |   Вверх   | 7C-FE-90-93-8F-A1 |  40 Гбит/с  |

   ---

   >[!IMPORTANT]
   >Он может занять несколько секунд для устройства, для перезапуска и становятся доступными в сети. 

4. Проверьте сетевое подключение.<p>В случае сбоя подключения проверьте параметр виртуальной локальной сети конфигурации или назначение участия в той же виртуальной сети. 

   ```PowerShell
   Test-NetConnection 192.168.1.5
   ```

## <a name="step-4-configure-quality-of-service-qos"></a>Шаг 4. Настройка качества обслуживания \(QoS\)

>[!NOTE]
>Все перечисленные ниже этапы конфигурации DCB и качества обслуживания следует выполнять на всех узлах, которые должны взаимодействовать друг с другом.

1. Установить мост для центра обработки данных \(DCB\) на каждом из узлов Hyper-V.

   - **Необязательный** для сетевых конфигураций, использующие iWarp для служб RDMA.
   - **Требуется** для сетевых конфигураций, использующих RoCE \(любой версии\) для служб RDMA.

   ```PowerShell
   Install-WindowsFeature Data-Center-Bridging
   ```

2. Настроить политики качества обслуживания для SMB Direct:

   - **Необязательный** для сетевых конфигураций, использующих iWarp.
   - **Требуется** для сетевых конфигураций, использующих RoCE.

   В примере команды ниже значение «3» является произвольным. Можно использовать любое значение от 1 до 7 до тех пор, пока последовательно использовать то же значение в конфигурации политик качества обслуживания.

   ```PowerShell
   New-NetQosPolicy "SMB" -NetDirectPortMatchCondition 445 -PriorityValue8021Action 3
   ```

   _**Результаты:** _


   |   Параметр    |          Значение           |
   |----------------|--------------------------|
   |      Имя      |           SMB            |
   |     Владелец      | Групповая политика \(машины\) |
   | NetworkProfile |           Все            |
   |   Precedence   |           127            |
   |   JobObject    |          &nbsp;          |
   | NetDirectPort  |           445            |
   | PriorityValue  |            3             |

   ---

3. Для развертываний RoCE, включите **управление потоком приоритет** для трафика SMB, который не является обязательным для iWarp.

   ```PowerShell
   Enable-NetQosFlowControl -priority 3
   Get-NetQosFlowControl
   ```

   _**Результаты:** _


   | Priority | Enabled | PolicySet | ifIndex | IfAlias |
   |----------|---------|-----------|---------|---------|
   |    0     |  False  |  Глобальная   | &nbsp;  | &nbsp;  |
   |    1     |  False  |  Глобальная   | &nbsp;  | &nbsp;  |
   |    2     |  False  |  Глобальная   | &nbsp;  | &nbsp;  |
   |    3     |  True   |  Глобальная   | &nbsp;  | &nbsp;  |
   |    4     |  False  |  Глобальная   | &nbsp;  | &nbsp;  |
   |    5     |  False  |  Глобальная   | &nbsp;  | &nbsp;  |
   |    6     |  False  |  Глобальная   | &nbsp;  | &nbsp;  |
   |    7     |  False  |  Глобальная   | &nbsp;  | &nbsp;  |

   ---

4. Настроить службу качества обслуживания для локальной и конечных сетевых адаптеров.

   - **Не требуется** для сетевых конфигураций, использующих iWarp.
   - **Требуется** для сетевых конфигураций, использующих RoCE.

   ```PowerShell
   Enable-NetAdapterQos -InterfaceAlias "M1"
   Get-NetAdapterQos -Name "M1"
   ```

   _**Результаты:** _

   **Имя**: M1  
   **Включено**: True  

   _**Возможности:** _   


   |      Параметр      |   Оборудование   |   Текущий    |
   |---------------------|--------------|--------------|
   |    MacSecBypass     | NotSupported | NotSupported |
   |     DcbxSupport     |     Нет     |     Нет     |
   | NumTCs(Max/ETS/PFC) |    8/8/8     |    8/8/8     |

   ---

   _**OperationalTrafficClasses:** _ 


   | TC | TSA | Пропускная способность | Приоритеты |
   |----|-----|-----------|------------|
   | 0  | ETS |    70%    |  0-2,4-7   |
   | 1  | ETS |    30 %    |     3      |

   ---

   _**OperationalFlowControl:** _  

   Приоритет 3 включена  

   _**OperationalClassifications:** _  


   | Protocol  | / Тип порта | Priority |
   |-----------|-----------|----------|
   |  Значение по умолчанию  |  &nbsp;   |    0     |
   | NetDirect |    445    |    3     |

   ---

5. Зарезервировать процент пропускной способности для SMB Direct \(RDMA\).

    В этом примере используется 30% резервирование пропускной способности. Следует выбрать значение, представляющее ожидаемым требует ваш трафик хранилища. 

   ```PowerShell
   New-NetQosTrafficClass "SMB" -Priority 3 -BandwidthPercentage 30 -Algorithm ETS
   ```

   _**Результаты:** _


   | Имя | Алгоритм | Bandwidth(%) | Priority | PolicySet | ifIndex | IfAlias |
   |------|-----------|--------------|----------|-----------|---------|---------|
   | SMB  |    ETS    |      30      |    3     |  Глобальная   | &nbsp;  | &nbsp;  |

   ---                                      

6. Просмотрите параметры резервирования пропускной способности.  

   ```PowerShell
   Get-NetQosTrafficClass
   ```

   _**Результаты:** _


   |   Имя    | Алгоритм | Bandwidth(%) | Priority | PolicySet | ifIndex | IfAlias |
   |-----------|-----------|--------------|----------|-----------|---------|---------|
   | [Default] |    ETS    |      70      | 0-2,4-7  |  Глобальная   | &nbsp;  | &nbsp;  |
   |    SMB    |    ETS    |      30      |    3     |  Глобальная   | &nbsp;  | &nbsp;  |

   ---

## <a name="step-5-optional-resolve-the-mellanox-adapter-debugger-conflict"></a>Шаг 5. (Необязательно) Разрешить конфликт отладчик адаптера Mellanox 

По умолчанию, при использовании адаптера Mellanox присоединенному отладчику блокирует NetQos, что это известная проблема. Таким образом Если вы используете на адаптер Mellanox и планируется подключить отладчик, используйте следующие команды разрешения этой проблемы. Этот шаг не является обязательным, если вы не планируете присоединить отладчик, или если вы не используете адаптер Mellanox.

   ```PowerShell    
   Set-ItemProperty HKLM:"\SYSTEM\CurrentControlSet\Services\NDIS\Parameters" AllowFlowControlUnderDebugger -type DWORD -Value 1 –Force
   ``` 

## <a name="step-6-verify-the-rdma-configuration-native-host"></a>Шаг 6. Проверка конфигурации RDMA (собственный узел)

Вы хотите убедитесь в правильности настройки структуры до создания виртуальный коммутатор и переход к RDMA (со схождением NIC). 

Ниже показано текущее состояние указанных узлах Hyper-V.

![Тест RDMA](../../media/Converged-NIC/4-single-test-rdma.jpg)

1. Проверьте конфигурацию RDMA.

   ```PowerShell
   Get-NetAdapterRdma
   ```
   _**Результаты:** _


   | Имя |           InterfaceDescription           | Enabled |
   |------|------------------------------------------|---------|
   |  M1  | Адаптер Mellanox ConnectX 3 Pro Ethernet |  True   |

   ---

2. Определить **ifIndex** значение целевой адаптера.<p>Это значение используется в последующих шагах, при запуске скрипта, который можно скачать.

   ```PowerShell
   Get-NetIPConfiguration -InterfaceAlias "M*" | ft InterfaceAlias,InterfaceIndex,IPv4Address
   ```

   _**Результаты:** _ 


   | InterfaceAlias | InterfaceIndex |  IPv4-адрес  |
   |----------------|----------------|---------------|
   |       M2       |       14       | {192.168.1.5} |

   ---

3. Скачайте [DiskSpd.exe программа](https://aka.ms/diskspd) и извлеките его содержимое в C:\TEST\.

4. Скачайте [RDMA тестового сценария powershell](https://github.com/Microsoft/SDN/blob/master/Diagnostics/Test-Rdma.ps1) в тестовой папке на локальном диске, например, C:\TEST\.

5. Запустите **Rdma.ps1 теста** сценарий PowerShell для передачи значения ifIndex в сценарий, а также IP-адрес удаленного адаптера в той же виртуальной сети.<p>В этом примере передает сценарий **ifIndex** значения 14 удаленной сети адаптера IP-адресом 192.168.1.5.

   ```PowerShell
    C:\TEST\Test-RDMA.PS1 -IfIndex 14 -IsRoCE $true -RemoteIpAddress 192.168.1.5 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\

    VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\\diskspd.exe
    VERBOSE: The adapter M2 is a physical adapter
    VERBOSE: Underlying adapter is RoCE. Checking if QoS/DCB/PFC is configured on each physical adapter(s)
    VERBOSE: QoS/DCB/PFC configuration is correct.
    VERBOSE: RDMA configuration is correct.
    VERBOSE: Checking if remote IP address, 192.168.1.5, is reachable.
    VERBOSE: Remote IP 192.168.1.5 is reachable.
    VERBOSE: Disabling RDMA on adapters that are not part of this test. RDMA will be enabled on them later.
    VERBOSE: Testing RDMA traffic now for. Traffic will be sent in a parallel job. Job details:
    VERBOSE: 0 RDMA bytes written per second
    VERBOSE: 0 RDMA bytes sent per second
    VERBOSE: 662979201 RDMA bytes written per second
    VERBOSE: 37561021 RDMA bytes sent per second
    VERBOSE: 1023098948 RDMA bytes written per second
    VERBOSE: 8901349 RDMA bytes sent per second
    VERBOSE: Enabling RDMA on adapters that are not part of this test. RDMA was disabled on them prior to sending RDMA traffic.
    VERBOSE: RDMA traffic test SUCCESSFUL: RDMA traffic was sent to 192.168.1.5
   ```

   >[!NOTE]
   >При сбое трафика RDMA, в случае RoCE в частности, см. конфигурацию коммутатора ToR правильных настроек PFC/ETS, должен соответствовать параметрам узла. См. раздел службы QoS в этом документе для значения по ссылке.

## <a name="step-7-remove-the-access-vlan-setting"></a>Шаг 7. Удалите параметр доступа VLAN

В процессе подготовки для создания Hyper-V переключения, необходимо удалить параметры виртуальной локальной сети, установленный ранее.  

1. Удалить параметр доступа VLAN из физический сетевой Адаптер для предотвращения автоматического присвоения тегов исходящий трафик с неправильный идентификатор виртуальной ЛС сетевого Адаптера<p>Удалять этот параметр также предотвращает его фильтрацию входящего трафика, не соответствующий идентификатор виртуальной ЛС доступа

   ```PowerShell
   Set-NetAdapterAdvancedProperty -Name M1 -RegistryKeyword VlanID -RegistryValue "0"
   ```    

2. Убедитесь, что **параметр VlanID** отображается значение идентификатора виртуальной локальной сети как ноль.

   ```PowerShell    
   Get-NetAdapterAdvancedProperty -name m1 | Where-Object {$_.RegistryKeyword -eq 'VlanID'} 
   ```  


## <a name="step-8-create-a-hyper-v-vswitch-on-your-hyper-v-hosts"></a>Шаг 8. Создание виртуального коммутатора Hyper-V на узлах Hyper-V

На следующем рисунке изображены узле 1 Hyper-V с виртуальный коммутатор.

![Создание виртуального коммутатора Hyper-V](../../media/Converged-NIC/5-single-create-vswitch.jpg)


1. Создайте внешний виртуальный коммутатор Hyper-V в Hyper-V на узле Hyper-V A. <p>В этом примере параметр называется VMSTEST. Кроме того, параметр **AllowManagementOS** создает виртуальный сетевой адаптер узла, который наследует MAC и IP-адреса физического сетевого адаптера.

   ```PowerShell
   New-VMSwitch -Name VMSTEST -NetAdapterName "M1" -AllowManagementOS $true
   ```
   _**Результаты:** _


   |  Имя   | SwitchType |      NetAdapterInterfaceDescription      |
   |---------|------------|------------------------------------------|
   | VMSTEST |  Внешняя  | Адаптер Mellanox ConnectX 3 Pro Ethernet |

   ---

2. Просмотр свойств сетевого адаптера.

   ```PowerShell
   Get-NetAdapter | ft -AutoSize
   ```

   _**Результаты:** _


   |         Имя          |        InterfaceDescription         | ifIndex | Состояние |    macAddress     | Скорость линии |
   |-----------------------|-------------------------------------|---------|--------|-------------------|-----------|
   | vEthernet \(VMSTEST\) | Hyper-V виртуального сетевого адаптера #2 |   27    |   Вверх   | E4-1D-2D-07-40-71 |  40 Гбит/с  |

   ---

3. Управление виртуальной сетевой карты узла в одном из двух способов. 

   - **NetAdapter** представление будет функционировать при «vEthernet \(VMSTEST\)"имя. В этом представлении отображаться не все свойства сетевого адаптера.
   - **VMNetworkAdapter** представление удаляет префикс «vEthernet» и просто использует имя vmswitch. (рекомендуется) 

   ```PowerShell
   Get-VMNetworkAdapter –ManagementOS | ft -AutoSize
   ```

   _**Результаты:** _


   |         Имя         | IsManagementOs |        VMName        |  SwitchName  | macAddress | Состояние | IPAddresses |
   |----------------------|----------------|----------------------|--------------|------------|--------|-------------|
   | CORP-внешний коммутатор |      True      | CORP-внешний коммутатор | 001B785768AA |    {ОК}    | &nbsp; |             |
   |       VMSTEST        |      True      |       VMSTEST        | E41D2D074071 |    {ОК}    | &nbsp; |             |

   ---

4. Проверка соединения.

   ```Powershell    
   Test-NetConnection 192.168.1.5
   ```

   _**Результаты:** _ 

   ```
    ComputerName   : 192.168.1.5
    RemoteAddress  : 192.168.1.5
    InterfaceAlias : vEthernet (CORP-External-Switch)
    SourceAddress  : 192.168.1.3
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms
   ```

5. Назначение и просмотр параметров сетевого адаптера виртуальной локальной сети.

   ```PowerShell
   Set-VMNetworkAdapterVlan -VMNetworkAdapterName "VMSTEST" -VlanId "101" -Access -ManagementOS
   Get-VMNetworkAdapterVlan -ManagementOS -VMNetworkAdapterName "VMSTEST"
   ```    

   _**Результаты:** _


   | VMName | VMNetworkAdapterName |  Режим  | VlanList |
   |--------|----------------------|--------|----------|
   | &nbsp; |       VMSTEST        | Доступ |   101    |

   ---  

6. Проверка соединения.<p>Может занять несколько секунд для завершения, прежде чем успешно проверить связь с другой.  

   ```PowerShell    
   Test-NetConnection 192.168.1.5
   ```

   _**Результаты:** _

   ```
    ComputerName   : 192.168.1.5
    RemoteAddress  : 192.168.1.5
    InterfaceAlias : vEthernet (VMSTEST)
    SourceAddress  : 192.168.1.3
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms
   ```

## <a name="step-9-test-hyper-v-virtual-switch-rdma-mode-2"></a>Шаг 9. Тестирование виртуального коммутатора Hyper-V RDMA (режим 2)

На следующем рисунке изображены текущее состояние узлов Hyper-V, включая виртуальный коммутатор на узле 1 Hyper-V.

![Тестирование виртуального коммутатора Hyper-V](../../media/Converged-NIC/6-single-test-vswitch-rdma.jpg)


1. Задайте приоритет, добавление тегов на виртуальном сетевом адаптере узла.

   ```PowerShell    
   Set-VMNetworkAdapter -ManagementOS -Name "VMSTEST" -IeeePriorityTag on
   Get-VMNetworkAdapter -ManagementOS -Name "VMSTEST" | fl Name,IeeePriorityTag
   ```  

   _**Результаты:** _

    Имя: VMSTEST IeeePriorityTag: Включено


2. Просмотрите сведения RDMA сетевого адаптера. 

   ```PowerShell
   Get-NetAdapterRdma
   ```   

   _**Результаты:** _


   |         Имя          |        InterfaceDescription         | Enabled |
   |-----------------------|-------------------------------------|---------|
   | vEthernet \(VMSTEST\) | Hyper-V виртуального сетевого адаптера #2 |  False  |

   ---

   >[!NOTE]
   >Если параметр **включено** имеет значение **False**, это означает, что RDMA отключен.


3. Просмотрите сведения о сетевых адаптерах.

   ```PowerShell
   Get-NetAdapter
   ```

   _**Результаты:** _   


   |        Имя         |        InterfaceDescription         | ifIndex | Состояние |    macAddress     | Скорость линии |
   |---------------------|-------------------------------------|---------|--------|-------------------|-----------|
   | vEthernet (VMSTEST) | Hyper-V виртуального сетевого адаптера #2 |   27    |   Вверх   | E4-1D-2D-07-40-71 |  40 Гбит/с  |

   ---


4. Включите RDMA на виртуальном сетевом адаптере узла.

   ```PowerShell
   Enable-NetAdapterRdma -Name "vEthernet (VMSTEST)"
   Get-NetAdapterRdma -Name "vEthernet (VMSTEST)"
   ```

   _**Результаты:** _


   |         Имя          |        InterfaceDescription         | Enabled |
   |-----------------------|-------------------------------------|---------|
   | vEthernet \(VMSTEST\) | Hyper-V виртуального сетевого адаптера #2 |  True   |

   ---

   >[!NOTE]
   >Если параметр **включено** имеет значение **True**, это означает, что включено RDMA.

5. Выполнение тестирования трафика RDMA.

   ```PowerShell    
    C:\TEST\Test-RDMA.PS1 -IfIndex 27 -IsRoCE $true -RemoteIpAddress 192.168.1.5 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
    VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\\diskspd.exe
    VERBOSE: The adapter vEthernet (VMSTEST) is a virtual adapter
    VERBOSE: Retrieving vSwitch bound to the virtual adapter
    VERBOSE: Found vSwitch: VMSTEST
    VERBOSE: Found the following physical adapter(s) bound to vSwitch: TEST-40G-1
    VERBOSE: Underlying adapter is RoCE. Checking if QoS/DCB/PFC is configured on each physical adapter(s)
    VERBOSE: QoS/DCB/PFC configuration is correct.
    VERBOSE: RDMA configuration is correct.
    VERBOSE: Checking if remote IP address, 192.168.1.5, is reachable.
    VERBOSE: Remote IP 192.168.1.5 is reachable.
    VERBOSE: Disabling RDMA on adapters that are not part of this test. RDMA will be enabled on them later.
    VERBOSE: Testing RDMA traffic now for. Traffic will be sent in a parallel job. Job details:
    VERBOSE: 0 RDMA bytes written per second
    VERBOSE: 0 RDMA bytes sent per second
    VERBOSE: 0 RDMA bytes written per second
    VERBOSE: 0 RDMA bytes sent per second
    VERBOSE: 0 RDMA bytes written per second
    VERBOSE: 0 RDMA bytes sent per second
    VERBOSE: 0 RDMA bytes written per second
    VERBOSE: 9162492 RDMA bytes sent per second
    VERBOSE: 938797258 RDMA bytes written per second
    VERBOSE: 34621865 RDMA bytes sent per second
    VERBOSE: 933572610 RDMA bytes written per second
    VERBOSE: 35035861 RDMA bytes sent per second
    VERBOSE: Enabling RDMA on adapters that are not part of this test. RDMA was disabled on them prior to sending RDMA traffic.
    VERBOSE: RDMA traffic test SUCCESSFUL: RDMA traffic was sent to 192.168.1.5
   ```

Последняя строка в эти выходные данные «тестирования трафика RDMA успешно: Трафика RDMA было отправлено 192.168.1.5,» показывает, что вы успешно настроили сетевой Адаптер, специализирующимся на адаптере.

## <a name="related-topics"></a>См. также
- [Конфигурация сетевой карты группы сетевых Адаптеров со схождением](cnic-datacenter.md)
- [Конфигурация физического коммутатора для сетевых Адаптеров со схождением](cnic-app-switch-config.md)
- [Устранение неполадок со схождением конфигурации сетевых Адаптеров](cnic-app-troubleshoot.md)
