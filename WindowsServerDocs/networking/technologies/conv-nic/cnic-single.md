---
title: Конфигурация с согласованным СЕТЕВЫМ адаптером с одним сетевым адаптером
description: В этом разделе приведены инструкции по настройке Объединенных сетевых адаптеров с одной сетевой картой на узле Hyper-V.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: eed5c184-fa55-43a8-a879-b1610ebc70ca
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/14/2018
ms.openlocfilehash: 2ad7592fd9faf1e92893e6271daabdad907d3aaa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405796"
---
# <a name="converged-nic-configuration-with-a-single-network-adapter"></a>Конфигурация с согласованным СЕТЕВЫМ адаптером с одним сетевым адаптером

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе приведены инструкции по настройке Объединенных сетевых адаптеров с одной сетевой картой на узле Hyper-V.

В примере конфигурации в этом разделе описывается два узла Hyper-v, **узел а**и узел Hyper-v **B**. На обоих узлах установлен один физический сетевой адаптер (ПНИК), а сетевые карты подключены к верхнему физическому коммутатору в стойке \(ToR @ no__t-1. Кроме того, узлы расположены в той же подсети, что и 192.168.1. x/24.

![Узлы Hyper-V.](../../media/Converged-NIC/1-single-test-conn.jpg)


## <a name="step-1-test-the-connectivity-between-source-and-destination"></a>Шаг 1. Проверка подключения между источником и назначением

Убедитесь, что физический сетевой адаптер может подключаться к целевому узлу. В этом тесте демонстрируется подключение с использованием уровня 3 \(L3 @ no__t-1 или уровня IP, а также уровня 2 \(L2 @ no__t-3.

1. Просмотр свойств сетевого адаптера.

   ```PowerShell
   Get-NetAdapter
   ```

   _**Результаты**_  


   | Имя |    интерфацедескриптион     | ifIndex | Состояние |    macAddress     | LinkSpeed |
   |------|-----------------------------|---------|--------|-------------------|-----------|
   |  M1  | Mellanox ConnectX-3 Pro... |    4    |   Вверх   | 7C-FE-90-93-8F-A1 |  40 Гбит/с  |

   ---

2. Просмотр дополнительных свойств адаптера, включая IP-адрес.

   ```PowerShell
   Get-NetAdapter M1 | fl *
   ```

   _**Результаты**_

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

## <a name="step-2-ensure-that-source-and-destination-can-communicate"></a>Шаг 2. Убедитесь, что источник и назначение могут обмениваться данными

На этом шаге мы используем команду Windows PowerShell **Test-NetConnection** , но если хотите, можно использовать команду **ping** . 

>[!TIP]
>Если вы уверены, что узлы могут взаимодействовать друг с другом, этот шаг можно пропустить.

1. Проверьте двунаправленный обмен данными.

   ```PowerShell
   Test-NetConnection 192.168.1.5
   ```

   _**Результаты**_


   |        Параметр         |    Значение    |
   |--------------------------|-------------|
   |       имя_компьютера       | 192.168.1.5 |
   |      RemoteAddress       | 192.168.1.5 |
   |      интерфацеалиас      |     M1      |
   |      саурцеаддресс       | 192.168.1.3 |
   |      пингсукцеедед       |    True     |
   | RTT \(пингреплидетаилс\) |    0 мс     |

   ---

   В некоторых случаях для успешного выполнения этого теста может потребоваться отключить брандмауэр Windows в расширенной безопасности. При отключении брандмауэра учитывайте безопасность и убедитесь, что ваша конфигурация соответствует требованиям безопасности вашей организации.

2. Отключите все профили брандмауэра.

   ```PowerShell
   Set-NetFirewallProfile -All -Enabled False
   ```

3. После отключения профилей брандмауэра снова проверьте подключение. 

   ```PowerShell
   Test-NetConnection 192.168.1.5
   ```

   _**Результаты**_


   |        Параметр         |    Значение    |
   |--------------------------|-------------|
   |       имя_компьютера       | 192.168.1.5 |
   |      RemoteAddress       | 192.168.1.5 |
   |      интерфацеалиас      | Test-40G-1  |
   |      саурцеаддресс       | 192.168.1.3 |
   |      пингсукцеедед       |    False    |
   | RTT \(пингреплидетаилс\) |    0 мс     |

   ---



## <a name="step-3-optional-configure-the-vlan-ids-for-nics-installed-in-your-hyper-v-hosts"></a>Шаг 3. Используемых Настройка идентификаторов виртуальных ЛС для сетевых адаптеров, установленных на узлах Hyper-V

Многие конфигурации сети используют виртуальные ЛС, и если вы планируете использовать виртуальные ЛС в сети, необходимо повторить предыдущий тест с настроенными виртуальными ЛС. Кроме того, если вы планируете использовать Роце для служб RDMA, необходимо включить виртуальные ЛС.

Для этого шага сетевые карты находятся в режиме **доступа** . Однако при создании виртуального коммутатора \(vSwitch\) Hyper-V позднее в этом пошаговом окне Свойства VLAN применяются на уровне порта vSwitch. 

Так как коммутатор может содержать несколько виртуальных ЛС, для верхней части физического коммутатора Tor \(\) в стойке необходимо, чтобы порт, к которому подключен узел, был настроен в режиме магистрали.

>[!NOTE]
>Дополнительные сведения о настройке режима магистрали для коммутатора см. в документации по коммутатору ToR.

На следующем рисунке показаны два узла Hyper-V с одним физическим сетевым адаптером, каждый из которых настроен для взаимодействия с виртуальной ЛС 101.

![Настройка виртуальных локальных сетей](../../media/Converged-NIC/2-single-configure-vlans.jpg)


>[!IMPORTANT]
>Выполните эту команду как на локальном, так и на целевом серверах. Если на целевом сервере не настроен тот же идентификатор виртуальной ЛС, что и на локальном сервере, связь между ними не будет выполнена.


1. Настройте идентификатор виртуальной ЛС для сетевых адаптеров, установленных на узлах Hyper-V.

   >[!IMPORTANT]
   >Не выполняйте эту команду, если вы подключены к узлу удаленно через этот интерфейс, так как это приводит к утрате доступа к узлу.

   ```PowerShell
   Set-NetAdapterAdvancedProperty -Name M1 -RegistryKeyword VlanID -RegistryValue "101"
   Get-NetAdapterAdvancedProperty -Name M1 | Where-Object {$_.RegistryKeyword -eq "VlanID"} 
   ```

   _**Результаты**_


   | Имя | DisplayName | дисплайвалуе | регистрикэйворд | RegistryValue |
   |------|-------------|--------------|-----------------|---------------|
   |  M1  |   ИД виртуальной ЛС   |     101      |     VlanID      |     {101}     |

   ---

2. Перезапустите сетевой адаптер, чтобы применить идентификатор виртуальной ЛС.

   ```PowerShell
   Restart-NetAdapter -Name "M1"
   ```

3. Убедитесь, что состояние **имеет значение работает.**

   ```PowerShell
   Get-NetAdapter -Name "M1"
   ```

   _**Результаты**_


   | Имя |          интерфацедескриптион           | ifIndex | Состояние |    macAddress     | LinkSpeed |
   |------|-----------------------------------------|---------|--------|-------------------|-----------|
   |  M1  | Mellanox ConnectX-3 Pro Ethernet Ada... |    4    |   Вверх   | 7C-FE-90-93-8F-A1 |  40 Гбит/с  |

   ---

   >[!IMPORTANT]
   >Перезапуск и доступность устройства в сети может занять несколько секунд. 

4. Проверьте подключение.<p>Если подключение не работает, проверьте конфигурацию виртуальной ЛС коммутатора или участие назначения в одной виртуальной ЛС. 

   ```PowerShell
   Test-NetConnection 192.168.1.5
   ```

## <a name="step-4-configure-quality-of-service-qos"></a>Шаг 4. Настройка качества \(обслуживания QoS\)

>[!NOTE]
>Необходимо выполнить все этапы настройки DCB и QoS на всех узлах, предназначенных для взаимодействия друг с другом.

1. Установите мосты \(\) центра обработки данных на каждом узле Hyper-V.

   - **Необязательно** для конфигураций сети, использующих iWarp для служб RDMA.
   - **Требуется** для сетевых конфигураций, использующих\) роце \(любую версию служб RDMA.

   ```PowerShell
   Install-WindowsFeature Data-Center-Bridging
   ```

2. Задайте политики качества обслуживания для протокола SMB Direct:

   - **Необязательно** для сетевых конфигураций, использующих iWarp.
   - **Требуется** для сетевых конфигураций, использующих роце.

   В приведенной ниже команде примера значение «3» является произвольным. Можно использовать любое значение от 1 до 7, если одно и то же значение постоянно используется во всей конфигурации политик качества обслуживания.

   ```PowerShell
   New-NetQosPolicy "SMB" -NetDirectPortMatchCondition 445 -PriorityValue8021Action 3
   ```

   _**Результаты**_


   |   Параметр    |          Значение           |
   |----------------|--------------------------|
   |      Имя      |           SMB            |
   |     Владелец      | Групповая политика \(машины\) |
   | NetworkProfile |           Все            |
   |   Precedence   |           127            |
   |   жобобжект    |          &nbsp;          |
   | нетдиректпорт  |           445            |
   | приоритивалуе  |            3             |

   ---

3. Для развертываний Роце включите **Управление потоком приоритета** для трафика SMB, который не требуется для iWarp.

   ```PowerShell
   Enable-NetQosFlowControl -priority 3
   Get-NetQosFlowControl
   ```

   _**Результаты**_


   | Priority | Enabled | Параметр Policy | ifIndex | ифалиас |
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

4. Включите качество обслуживания для локальных и целевых сетевых адаптеров.

   - **Не требуется** для сетевых конфигураций, использующих iWarp.
   - **Требуется** для сетевых конфигураций, использующих роце.

   ```PowerShell
   Enable-NetAdapterQos -InterfaceAlias "M1"
   Get-NetAdapterQos -Name "M1"
   ```

   _**Результаты**_

   **Имя**: M1  
   **Включено**: True  

   _**Речь**_   


   |      Параметр      |   Оборудование   |   Данном    |
   |---------------------|--------------|--------------|
   |    максекбипасс     | NotSupported | NotSupported |
   |     дкбкссуппорт     |     Нет     |     Нет     |
   | Нумткс (Max/ETS/коэффициент мощности) |    8/8/8     |    8/8/8     |

   ---

   _**Оператионалтраффикклассес:**_ 


   | ТЕХНИЧЕСКИ | TSA | Связи | Приоритеты |
   |----|-----|-----------|------------|
   | 0  | ETS |    70%    |  0 – 2, 4 – 7   |
   | 1  | ETS |    30 %    |     3      |

   ---

   _**Оператионалфловконтрол:**_  

   Приоритет 3 включен  

   _**Оператионалклассификатионс:**_  


   | Protocol  | Порт/тип | Priority |
   |-----------|-----------|----------|
   |  Значение по умолчанию  |  &nbsp;   |    0     |
   | нетдирект |    445    |    3     |

   ---

5. Зарезервируйте процент пропускной способности для SMB Direct \(RDMA @ no__t-1.

    В этом примере используется резервирование с пропускной способностью 30%. Следует выбрать значение, представляющее предполагаемый объем трафика хранилища. 

   ```PowerShell
   New-NetQosTrafficClass "SMB" -Priority 3 -BandwidthPercentage 30 -Algorithm ETS
   ```

   _**Результаты**_


   | Имя | Алгоритм | Пропускная способность (%) | Priority | Параметр Policy | ifIndex | ифалиас |
   |------|-----------|--------------|----------|-----------|---------|---------|
   | SMB  |    ETS    |      30      |    3     |  Глобальная   | &nbsp;  | &nbsp;  |

   ---                                      

6. Просмотр параметров резервирования пропускной способности.  

   ```PowerShell
   Get-NetQosTrafficClass
   ```

   _**Результаты**_


   |   Имя    | Алгоритм | Пропускная способность (%) | Priority | Параметр Policy | ifIndex | ифалиас |
   |-----------|-----------|--------------|----------|-----------|---------|---------|
   | Параметры |    ETS    |      70      | 0 – 2, 4 – 7  |  Глобальная   | &nbsp;  | &nbsp;  |
   |    SMB    |    ETS    |      30      |    3     |  Глобальная   | &nbsp;  | &nbsp;  |

   ---

## <a name="step-5-optional-resolve-the-mellanox-adapter-debugger-conflict"></a>Шаг 5. Используемых Устранение конфликта отладчика адаптера Mellanox 

По умолчанию при использовании адаптера Mellanox подключенный отладчик блокирует NetQos, который является известной проблемой. Поэтому, если вы используете адаптер из Mellanox и планируете подключить отладчик, используйте следующую команду для устранения этой проблемы. Этот шаг не требуется, если не требуется подключать отладчик или адаптер Mellanox не используется.

   ```PowerShell    
   Set-ItemProperty HKLM:"\SYSTEM\CurrentControlSet\Services\NDIS\Parameters" AllowFlowControlUnderDebugger -type DWORD -Value 1 –Force
   ``` 

## <a name="step-6-verify-the-rdma-configuration-native-host"></a>Шаг 6. Проверка конфигурации RDMA (собственный узел)

Перед созданием vSwitch и переходом на RDMA (выходящий сетевой адаптер) необходимо убедиться, что структура настроена правильно. 

На следующем рисунке показано текущее состояние узлов Hyper-V.

![Тест RDMA](../../media/Converged-NIC/4-single-test-rdma.jpg)

1. Проверьте конфигурацию RDMA.

   ```PowerShell
   Get-NetAdapterRdma
   ```
   _**Результаты**_


   | Имя |           интерфацедескриптион           | Enabled |
   |------|------------------------------------------|---------|
   |  M1  | Ethernet-адаптер Mellanox ConnectX-3 Pro |  True   |

   ---

2. Определите значение **ifIndex** для целевого адаптера.<p>Это значение используется в последующих шагах при запуске скачанного скрипта.

   ```PowerShell
   Get-NetIPConfiguration -InterfaceAlias "M*" | ft InterfaceAlias,InterfaceIndex,IPv4Address
   ```

   _**Результаты**_ 


   | интерфацеалиас | InterfaceIndex |  IPv4-адрес  |
   |----------------|----------------|---------------|
   |       M2       |       14       | {192.168.1.5} |

   ---

3. Скачайте [служебную программу DiskSpd. exe](https://aka.ms/diskspd) и извлеките ее в файл C:\TEST.\.

4. Скачайте [сценарий PowerShell Test-RDMA](https://github.com/Microsoft/SDN/blob/master/Diagnostics/Test-Rdma.ps1) в тестовую папку на локальном диске, например C:\TEST @ no__t-1.

5. Запустите сценарий PowerShell **тест-рдма. ps1** , чтобы передать значение ifIndex в скрипт, а также IP-адрес удаленного адаптера в той же виртуальной ЛС.<p>В этом примере сценарий передает значение **ifIndex** , равное 14, на IP-адрес удаленного сетевого адаптера 192.168.1.5.

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
   >Если трафик RDMA завершается неудачно, в Роце случае проверьте конфигурацию коммутатора ToR на соответствие параметрам коэффициента мощности или ETS, которые должны соответствовать параметрам узла. Справочные сведения см. в разделе "качество обслуживания" этого документа.

## <a name="step-7-remove-the-access-vlan-setting"></a>Шаг 7. Удаление параметра Access VLAN

При подготовке к созданию коммутатора Hyper-V необходимо удалить установленные ранее параметры виртуальной ЛС.  

1. Удалите параметр доступа к виртуальной ЛС из физического сетевого адаптера, чтобы не допустить автоматического добавления тегов в исходящий трафик с неправильным ИДЕНТИФИКАТОРом виртуальной ЛС.<p>Удаление этого параметра также предотвращает фильтрацию входящего трафика, который не соответствует ИДЕНТИФИКАТОРу виртуальной ЛС доступа.

   ```PowerShell
   Set-NetAdapterAdvancedProperty -Name M1 -RegistryKeyword VlanID -RegistryValue "0"
   ```    

2. Убедитесь, что **параметр VlanID** ОТОБРАЖАЕТ значение идентификатора виртуальной ЛС равным нулю.

   ```PowerShell    
   Get-NetAdapterAdvancedProperty -name m1 | Where-Object {$_.RegistryKeyword -eq 'VlanID'} 
   ```  


## <a name="step-8-create-a-hyper-v-vswitch-on-your-hyper-v-hosts"></a>Шаг 8. Создание Hyper-V vSwitch на узлах Hyper-V

На следующем рисунке показан узел Hyper-V 1 с vSwitch.

![Создание виртуального коммутатора Hyper-V](../../media/Converged-NIC/5-single-create-vswitch.jpg)


1. Создайте внешний Hyper-V vSwitch в Hyper-V на узле A Hyper-v. <p>В этом примере параметр называется ВМСТЕСТ. Кроме того, параметр **алловманажементос** создает узел vNIC, который наследует Mac и IP-адреса физического сетевого адаптера.

   ```PowerShell
   New-VMSwitch -Name VMSTEST -NetAdapterName "M1" -AllowManagementOS $true
   ```
   _**Результаты**_


   |  Имя   | свитчтипе |      нетадаптеринтерфацедескриптион      |
   |---------|------------|------------------------------------------|
   | ВМСТЕСТ |  Внешняя  | Ethernet-адаптер Mellanox ConnectX-3 Pro |

   ---

2. Просмотр свойств сетевого адаптера.

   ```PowerShell
   Get-NetAdapter | ft -AutoSize
   ```

   _**Результаты**_


   |         Имя          |        интерфацедескриптион         | ifIndex | Состояние |    macAddress     | LinkSpeed |
   |-----------------------|-------------------------------------|---------|--------|-------------------|-----------|
   | Адаптера vethernet \(VMSTEST @ no__t-1 | #2 адаптера виртуальной сети Ethernet Hyper-V |   27    |   Вверх   | E4-1D-2D-07-40-71 |  40 Гбит/с  |

   ---

3. Управление узлом vNIC осуществляется одним из двух способов. 

   - Представление **NetAdapter** работает на основе имени адаптера vethernet \(VMSTEST @ no__t-2. Не все свойства сетевого адаптера отображаются в этом представлении.
   - Представление **VMNetworkAdapter** удаляет префикс "адаптера vethernet" и просто использует имя коммутатора виртуальной машины. (рекомендуется) 

   ```PowerShell
   Get-VMNetworkAdapter –ManagementOS | ft -AutoSize
   ```

   _**Результаты**_


   |         Имя         | исманажементос |        VMName        |  SwitchName  | macAddress | Состояние | IPAddresses |
   |----------------------|----------------|----------------------|--------------|------------|--------|-------------|
   | CORP — внешний коммутатор |      True      | CORP — внешний коммутатор | 001B785768AA |    '    | &nbsp; |             |
   |       ВМСТЕСТ        |      True      |       ВМСТЕСТ        | E41D2D074071 |    '    | &nbsp; |             |

   ---

4. Проверьте подключение.

   ```Powershell    
   Test-NetConnection 192.168.1.5
   ```

   _**Результаты**_ 

   ```
    ComputerName   : 192.168.1.5
    RemoteAddress  : 192.168.1.5
    InterfaceAlias : vEthernet (CORP-External-Switch)
    SourceAddress  : 192.168.1.3
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms
   ```

5. Назначение и Просмотр параметров виртуальной ЛС сетевого адаптера.

   ```PowerShell
   Set-VMNetworkAdapterVlan -VMNetworkAdapterName "VMSTEST" -VlanId "101" -Access -ManagementOS
   Get-VMNetworkAdapterVlan -ManagementOS -VMNetworkAdapterName "VMSTEST"
   ```    

   _**Результаты**_


   | VMName | вмнетворкадаптернаме |  Режим  | вланлист |
   |--------|----------------------|--------|----------|
   | &nbsp; |       ВМСТЕСТ        | Доступ |   101    |

   ---  

6. Проверьте подключение.<p>Для успешного выполнения проверки связи с другим адаптером может потребоваться несколько секунд.  

   ```PowerShell    
   Test-NetConnection 192.168.1.5
   ```

   _**Результаты**_

   ```
    ComputerName   : 192.168.1.5
    RemoteAddress  : 192.168.1.5
    InterfaceAlias : vEthernet (VMSTEST)
    SourceAddress  : 192.168.1.3
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms
   ```

## <a name="step-9-test-hyper-v-virtual-switch-rdma-mode-2"></a>Шаг 9. Проверка RDMA виртуального коммутатора Hyper-V (режим 2)

На следующем рисунке показано текущее состояние узлов Hyper-V, включая vSwitch на узле Hyper-V 1.

![Тестирование виртуального коммутатора Hyper-V](../../media/Converged-NIC/6-single-test-vswitch-rdma.jpg)


1. Задайте Теги приоритета на узле vNIC.

   ```PowerShell    
   Set-VMNetworkAdapter -ManagementOS -Name "VMSTEST" -IeeePriorityTag on
   Get-VMNetworkAdapter -ManagementOS -Name "VMSTEST" | fl Name,IeeePriorityTag
   ```  

   _**Результаты**_

    Имя: ВМСТЕСТ Ииеприорититаг: Включено


2. Просмотрите сведения о RDMA сетевого адаптера. 

   ```PowerShell
   Get-NetAdapterRdma
   ```   

   _**Результаты**_


   |         Имя          |        интерфацедескриптион         | Enabled |
   |-----------------------|-------------------------------------|---------|
   | Адаптера vethernet \(VMSTEST @ no__t-1 | #2 адаптера виртуальной сети Ethernet Hyper-V |  False  |

   ---

   >[!NOTE]
   >Если параметр **Enabled** имеет значение **false**, это означает, что RDMA не включен.


3. Просмотр сведений о сетевом адаптере.

   ```PowerShell
   Get-NetAdapter
   ```

   _**Результаты**_   


   |        Имя         |        интерфацедескриптион         | ifIndex | Состояние |    macAddress     | LinkSpeed |
   |---------------------|-------------------------------------|---------|--------|-------------------|-----------|
   | Адаптера vethernet (ВМСТЕСТ) | #2 адаптера виртуальной сети Ethernet Hyper-V |   27    |   Вверх   | E4-1D-2D-07-40-71 |  40 Гбит/с  |

   ---


4. Включите RDMA на узле vNIC.

   ```PowerShell
   Enable-NetAdapterRdma -Name "vEthernet (VMSTEST)"
   Get-NetAdapterRdma -Name "vEthernet (VMSTEST)"
   ```

   _**Результаты**_


   |         Имя          |        интерфацедескриптион         | Enabled |
   |-----------------------|-------------------------------------|---------|
   | Адаптера vethernet \(VMSTEST @ no__t-1 | #2 адаптера виртуальной сети Ethernet Hyper-V |  True   |

   ---

   >[!NOTE]
   >Если параметр **Enabled** имеет значение **true**, это означает, что RDMA включен.

5. Выполните проверку трафика RDMA.

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

Последняя строка в этом выходных данных: "Проверка трафика RDMA выполнена успешно. Трафик RDMA был отправлен в 192.168.1.5, "показывает, что в адаптере успешно настроены согласованные сетевые адаптеры.

## <a name="related-topics"></a>См. также
- [Конфигурация сетевого адаптера Объединенных сетевых адаптеров](cnic-datacenter.md)
- [Конфигурация физического коммутатора для Объединенных сетевых адаптеров](cnic-app-switch-config.md)
- [Устранение неполадок конфигураций Объединенных сетевых адаптеров](cnic-app-troubleshoot.md)
