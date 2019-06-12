---
title: Конвергентную сетевую КАРТУ в конфигурации сетевого Адаптера, объединенные в группу (datacenter)
description: В этом разделе мы предоставляют инструкции для развертывания сетевых Адаптеров со схождением в конфигурации сетевого Адаптера, объединенные в группу с коммутатора внедренных коммутаторов (SET).
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: f01546f8-c495-4055-8492-8806eee99862
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/17/2018
ms.openlocfilehash: 58c4483c092c30a892ea6bdde20794270340fa8e
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66447022"
---
# <a name="converged-nic-in-a-teamed-nic-configuration-datacenter"></a>Конвергентную сетевую КАРТУ в конфигурации сетевого Адаптера, объединенные в группу (datacenter)

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе мы предоставляем пошаговые инструкции по развертыванию сетевых Адаптеров со схождением в конфигурации сетевого Адаптера, объединенные в группу с Switch Embedded Teaming \(ЗАДАТЬ\). 

Пример конфигурации в этом разделе описаны два узла Hyper-V, **узле 1 Hyper-V** и **узел 2 Hyper-V**. Они имеют два сетевых адаптера. На каждом узле один адаптер подключается к подсети 192.168.1.x/24 и один адаптер подключается к подсети 192.168.2.x/24.

![Узлы Hyper-V.](../../media/Converged-NIC/1-datacenter-test-conn.jpg)

## <a name="step-1-test-the-connectivity-between-source-and-destination"></a>Шаг 1. Проверьте возможность подключения между источником и назначением

Подключите физический сетевой Адаптер на узел назначения.  Данный тест демонстрирует подключение с помощью третьего уровня \(L3\) - или уровень IP -, а также уровня 2 \(L2\) виртуальные локальные сети \(виртуальной ЛС\).

1. Просмотр свойств первого сетевого адаптера.

   ```PowerShell
   Get-NetAdapter -Name "Test-40G-1" | ft -AutoSize
   ```

   _**Результаты:** _


   |    Имя    |           InterfaceDescription           | ifIndex | Состояние |    macAddress     | Скорость линии |
   |------------|------------------------------------------|---------|--------|-------------------|-----------|
   | Test-40G-1 | Адаптер Mellanox ConnectX 3 Pro Ethernet |   11    |   Вверх   | E4-1D-2D-07-43-D0 |  40 Гбит/с  |

   ---

2. Просмотр свойств для первый адаптер, включая IP-адрес. 

   ```PowerShell
   Get-NetIPAddress -InterfaceAlias "Test-40G-1"
   Get-NetIPAddress -InterfaceAlias "TEST-40G-1" | Where-Object {$_.AddressFamily -eq "IPv4"} | fl InterfaceAlias,IPAddress
   ```

   _**Результаты:** _


   |   Параметр    |    Значение    |
   |----------------|-------------|
   |   IPAddress    | 192.168.1.3 |
   | InterfaceIndex |     11      |
   | InterfaceAlias | Test-40G-1  |
   | Свойство AddressFamily  |    IPv4     |
   |      Тип      |   Одноадресная рассылка   |
   |  PrefixLength  |     24      |

   ---

3. Просмотрите свойства второго сетевого адаптера.

   ```PowerShell
   Get-NetAdapter -Name "Test-40G-2" | ft -AutoSize
   ```

   _**Результаты:** _


   |    Имя    |          InterfaceDescription           | ifIndex | Состояние |    macAddress     | Скорость линии |
   |------------|-----------------------------------------|---------|--------|-------------------|-----------|
   | ТЕСТ-40G-2 | Mellanox ConnectX 3 Pro Ethernet A... 2 |   13    |   Вверх   | E4-1D-2D-07-40-70 |  40 Гбит/с  |

   ---

4. Просмотр свойств для второго адаптера, включая IP-адрес.

   ```PowerShell
   Get-NetIPAddress -InterfaceAlias "Test-40G-2"
   Get-NetIPAddress -InterfaceAlias "Test-40G-2" | Where-Object {$_.AddressFamily -eq "IPv4"} | fl InterfaceAlias,IPAddress
   ```

   _**Результаты:** _


   |   Параметр    |    Значение    |
   |----------------|-------------|
   |   IPAddress    | 192.168.2.3 |
   | InterfaceIndex |     13      |
   | InterfaceAlias | ТЕСТ-40G-2  |
   | Свойство AddressFamily  |    IPv4     |
   |      Тип      |   Одноадресная рассылка   |
   |  PrefixLength  |     24      |

   ---

5. Убедитесь, что этого других Сетевых карт или НАБОРА элементов pNICs имеет допустимый IP-адрес.<p>Используйте отдельную подсеть, \(xxx.xxx. **2**.xxx vs xxx.xxx. **1**.xxx\), для упрощения отправки из этого адаптера в место назначения. Если оба pNICs найти в той же подсети, равномерно распределяет нагрузку стек Windows TCP/IP по среди интерфейсов и простой проверки становится более сложным.


## <a name="step-2-ensure-that-source-and-destination-can-communicate"></a>Шаг 2. Источник и назначение могли обмениваться данными

На этом шаге мы используем **Test-NetConnection** команды Windows PowerShell, однако если вы можете использовать **ping** команды, если вы предпочитаете. 

1. Проверьте двунаправленный обмен данными.

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


4. Проверьте сетевое подключение для дополнительных сетевых карт. Повторите предыдущие шаги для всех последующих pNICs, включенных в группе сетевой Адаптер или НАБОР.

   ```PowerShell    
   Test-NetConnection 192.168.2.5
   ```

   _**Результаты:** _


   |        Параметр         |    Значение    |
   |--------------------------|-------------|
   |       имя_компьютера       | 192.168.2.5 |
   |      RemoteAddress       | 192.168.2.5 |
   |      InterfaceAlias      | Тест-40G-2  |
   |      SourceAddress       | 192.168.2.3 |
   |      PingSucceeded       |    False    |
   | PingReplyDetails \(время приема-Передачи\) |    0 мс     |

   ---

## <a name="step-3-configure-the-vlan-ids-for-nics-installed-in-your-hyper-v-hosts"></a>Шаг 3. Настройка идентификаторов виртуальной локальной сети для сетевых адаптеров, которые установлены на узлах Hyper-V

Множество конфигураций сети с помощью виртуальных локальных сетей, и если вы планируете использовать виртуальные локальные сети в вашей сети, необходимо повторить предыдущий тест настроен виртуальные ЛС.

Для выполнения этого шага сетевые адаптеры, находятся в **доступа** режим. Тем не менее, при создании виртуального коммутатора Hyper-V \(vSwitch\) далее в этом руководстве свойства виртуальной ЛС применяются на уровне порта виртуального коммутатора. 

Так как переключатель можно разместить несколько виртуальных ЛС, это необходимо для верхнего \(ToR\) физического коммутатора, чтобы обеспечить порт, который узел подключен к настроен магистральный режим.

>[!NOTE]
>Инструкции по настройке магистральный режим на коммутаторе обратитесь к документации коммутатора ToR.

На следующем рисунке показана два узла Hyper-V с двумя сетевыми адаптерами, каждый с виртуальной ЛС 101 и 102 виртуальной локальной сети, настроенным в свойствах сетевого адаптера.

![Настройка виртуальных локальных сетей](../../media/Converged-NIC/2-datacenter-configure-vlans.jpg)


>[!TIP]
>В соответствии с Institute of Electrical и инженеров Electronics \(IEEE\) стандартов качества обслуживания сети \(QoS\) свойств в физический сетевой Адаптер действовать в заголовке 802.1 p, которое внедрено в рамках 802.1Q \(виртуальной ЛС\) заголовка при настройке ИД виртуальной ЛС.

1. Настройте идентификатор виртуальной ЛС для первого сетевого Адаптера, Test-40G-1.

   ```PowerShell    
   Set-NetAdapterAdvancedProperty -Name "Test-40G-1" -RegistryKeyword VlanID -RegistryValue "101"
   Get-NetAdapterAdvancedProperty -Name "Test-40G-1" | Where-Object {$_.RegistryKeyword -eq "VlanID"} | ft -AutoSize
   ```

   _**Результаты:** _   


   |    Имя    | DisplayName | DisplayValue | RegistryKeyword | RegistryValue |
   |------------|-------------|--------------|-----------------|---------------|
   | TEST-40G-1 |   ИД виртуальной ЛС   |     101      |     VlanID      |     {101}     |

   ---

2. Перезапустите сетевой адаптер для применения ИД виртуальной ЛС.

   ```PowerShell
   Restart-NetAdapter -Name "Test-40G-1"
   ```

3. Убедитесь, находится в состоянии **вверх**.

   ```PowerShell
   Get-NetAdapter -Name "Test-40G-1" | ft -AutoSize
   ```

   _**Результаты:** _


   |    Имя    |          InterfaceDescription           | ifIndex | Состояние |    macAddress     | Скорость линии |
   |------------|-----------------------------------------|---------|--------|-------------------|-----------|
   | Test-40G-1 | Mellanox ConnectX-3 Pro Ethernet Ada... |   11    |   Вверх   | E4-1D-2D-07-43-D0 |  40 Гбит/с  |

   ---

4. Настройте идентификатор виртуальной локальной сети на вторую сетевую КАРТУ, тест-40G-2.

   ```PowerShell    
   Set-NetAdapterAdvancedProperty -Name "Test-40G-2" -RegistryKeyword VlanID -RegistryValue "102"
   Get-NetAdapterAdvancedProperty -Name "Test-40G-2" | Where-Object {$_.RegistryKeyword -eq "VlanID"} | ft -AutoSize
   ``` 

   _**Результаты:** _


   |    Имя    | DisplayName | DisplayValue | RegistryKeyword | RegistryValue |
   |------------|-------------|--------------|-----------------|---------------|
   | ТЕСТ-40G-2 |   ИД виртуальной ЛС   |     102      |     VlanID      |     {102}     |

   ---

5. Перезапустите сетевой адаптер для применения ИД виртуальной ЛС.

   ```PowerShell
   Restart-NetAdapter -Name "Test-40G-2" 
   ```

6. Убедитесь, находится в состоянии **вверх**.

   ```PowerShell
   Get-NetAdapter -Name "Test-40G-1" | ft -AutoSize
   ```

   _**Результаты:** _


   |    Имя    |          InterfaceDescription           | ifIndex | Состояние |    macAddress     | Скорость линии |
   |------------|-----------------------------------------|---------|--------|-------------------|-----------|
   | Тест-40G-2 | Mellanox ConnectX-3 Pro Ethernet Ada... |   11    |   Вверх   | E4-1D-2D-07-43-D1 |  40 Гбит/с  |

   ---

   >[!IMPORTANT]
   >Он может занять несколько секунд для устройства, для перезапуска и становятся доступными в сети. 

7. Проверьте сетевое подключение для первого сетевого Адаптера, Test-40G-1.<p>В случае сбоя подключения проверьте параметр виртуальной локальной сети конфигурации или назначение участия в той же виртуальной сети. 

   ```PowerShell
   Test-NetConnection 192.168.1.5
   ```

   _**Результаты:** _   


   |        Параметр         |    Значение    |
   |--------------------------|-------------|
   |       имя_компьютера       | 192.168.1.5 |
   |      RemoteAddress       | 192.168.1.5 |
   |      InterfaceAlias      | Test-40G-1  |
   |      SourceAddress       | 192.168.1.5 |
   |      PingSucceeded       |    True     |
   | PingReplyDetails \(время приема-Передачи\) |    0 мс     |

   ---

8. Проверьте сетевое подключение для первого сетевого Адаптера теста-40G-2.<p>В случае сбоя подключения проверьте параметр виртуальной локальной сети конфигурации или назначение участия в той же виртуальной сети.

   ```PowerShell    
   Test-NetConnection 192.168.2.5
   ```

   _**Результаты:** _    


   |        Параметр         |    Значение    |
   |--------------------------|-------------|
   |       имя_компьютера       | 192.168.2.5 |
   |      RemoteAddress       | 192.168.2.5 |
   |      InterfaceAlias      | Тест-40G-2  |
   |      SourceAddress       | 192.168.2.3 |
   |      PingSucceeded       |    True     |
   | PingReplyDetails \(время приема-Передачи\) |    0 мс     |

   ---

   >[!IMPORTANT]
   >Нередко для **Test-NetConnection** или проверить связь с ошибки возникает немедленно после выполнения **Restart-NetAdapter**.  Поэтому дождитесь сетевого адаптера, который полностью инициализировать и повторите попытку.
   >
   >Если подключения 101 виртуальной ЛС работают, но не подключений 102 виртуальной локальной сети, проблема может быть, что коммутатор должен разрешать трафик на портах на требуемой виртуальной локальной сети. Для этого можно проверить путем временно установки адаптеры сбой на 101 виртуальной локальной сети и повторяющиеся проверки подключения.


   На следующем рисунке показана узлами Hyper-V после успешной настройки виртуальных локальных сетей.

   ![Настройка качества обслуживания](../../media/Converged-NIC/3-datacenter-configure-qos.jpg)


## <a name="step-4-configure-quality-of-service-qos"></a>Шаг 4. Настройка качества обслуживания \(QoS\)

>[!NOTE]
>Все перечисленные ниже этапы конфигурации DCB и качества обслуживания следует выполнять на всех узлах, которые должны взаимодействовать друг с другом.

1. Установить мост для центра обработки данных \(DCB\) на каждом из узлов Hyper-V.

   - **Необязательный** для сетевых конфигураций, использующих iWarp.
   - **Требуется** для сетевых конфигураций, использующих RoCE \(любой версии\) для служб RDMA.

   ```PowerShell
   Install-WindowsFeature Data-Center-Bridging
   ```

   _**Результаты:** _


   | Success | Требуется перезагрузка | Код выхода |     Результат функции     |
   |---------|----------------|-----------|------------------------|
   |  True   |       Нет       |  Success  | {Мост для центра обработки данных} |

   ---

2. Настроить политики качества обслуживания для SMB Direct:

   - **Необязательный** для сетевых конфигураций, использующих iWarp.
   - **Требуется** для сетевых конфигураций, использующих RoCE \(любой версии\) для служб RDMA.

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

3. Настроить дополнительные политики качества обслуживания для другого трафика в интерфейсе.   

   ```PowerShell
   New-NetQosPolicy "DEFAULT" -Default -PriorityValue8021Action 0
   ```

   _**Результаты:** _   


   |   Параметр    |          Значение           |
   |----------------|--------------------------|
   |      Имя      |         DEFAULT          |
   |     Владелец      | Групповая политика \(машины\) |
   | NetworkProfile |           Все            |
   |   Precedence   |           127            |
   |    Шаблон    |         Значение по умолчанию          |
   |   JobObject    |          &nbsp;          |
   | PriorityValue  |            0             |

   ---

4. Включите **управление потоком приоритет** для трафика SMB, который не является обязательным для iWarp.

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

   >**ВАЖНЫЕ** результаты эти результаты не совпадают, так как элементы, отличные от 3 имеет значение "Enabled" значение True, необходимо отключить **управления потоком** для этих классов.
   >
   >```PowerShell
   >Disable-NetQosFlowControl -priority 0,1,2,4,5,6,7
   >Get-NetQosFlowControl
   >```
   >В более сложных конфигураций — другие классы трафика может потребоваться управление потоком, однако эти сценарии выходят за рамки данного руководства.


5. Настроить службу качества обслуживания для первого сетевого Адаптера, Test-40G-1.

   ```PowerShell
   Enable-NetAdapterQos -InterfaceAlias "Test-40G-1"
   Get-NetAdapterQos -Name "Test-40G-1"

   Name: TEST-40G-1 
   Enabled: True
   ```
   _**Возможности**:_   


   |      Параметр      |   Оборудование   |   Текущий    |
   |---------------------|--------------|--------------|
   |    MacSecBypass     | NotSupported | NotSupported |
   |     DcbxSupport     |     Нет     |     Нет     |
   | NumTCs(Max/ETS/PFC) |    8/8/8     |    8/8/8     |

   ---

   _**OperationalTrafficClasses**:_    


   | TC |  TSA   | Пропускная способность | Приоритеты |
   |----|--------|-----------|------------|
   | 0  | "Строгий" |  &nbsp;   |    0-7     |

   ---

   _**OperationalFlowControl**:_  

   Приоритет 3 включена  

   _**OperationalClassifications**:_  


   | Protocol  | / Тип порта | Priority |
   |-----------|-----------|----------|
   |  Значение по умолчанию  |  &nbsp;   |    0     |
   | NetDirect |    445    |    3     |

   ---

6. Настроить службу качества обслуживания для второй сетевой Адаптер, тест-40G-2.

   ```PowerShell
   Enable-NetAdapterQos -InterfaceAlias "Test-40G-2"
   Get-NetAdapterQos -Name "Test-40G-2"

   Name: TEST-40G-2 
   Enabled: True 
   ```

   _**Возможности**:_ 


   |      Параметр      |   Оборудование   |   Текущий    |
   |---------------------|--------------|--------------|
   |    MacSecBypass     | NotSupported | NotSupported |
   |     DcbxSupport     |     Нет     |     Нет     |
   | NumTCs(Max/ETS/PFC) |    8/8/8     |    8/8/8     |

   ---

   _**OperationalTrafficClasses**:_  


   | TC |  TSA   | Пропускная способность | Приоритеты |
   |----|--------|-----------|------------|
   | 0  | "Строгий" |  &nbsp;   |    0-7     |

   ---

    _**OperationalFlowControl**:_  

    Приоритет 3 включена  

   _**OperationalClassifications**:_  


   | Protocol  | / Тип порта | Priority |
   |-----------|-----------|----------|
   |  Значение по умолчанию  |  &nbsp;   |    0     |
   | NetDirect |    445    |    3     |

   ---


7. Зарезервировать половина пропускной способности для SMB Direct \(RDMA\)

   ```PowerShell
   New-NetQosTrafficClass "SMB" -priority 3 -bandwidthpercentage 50 -algorithm ETS
   ```

   _**Результаты:** _  


   | Имя | Алгоритм | Bandwidth(%) | Priority | PolicySet | ifIndex | IfAlias |
   |------|-----------|--------------|----------|-----------|---------|---------|
   | SMB  |    ETS    |      50      |    3     |  Глобальная   | &nbsp;  | &nbsp;  |

   ---

8. Просмотрите параметры резервирования пропускной способности:   

   ```PowerShell
   Get-NetQosTrafficClass | ft -AutoSize
   ```

   _**Результаты:** _  


   |   Имя    | Алгоритм | Bandwidth(%) | Priority | PolicySet | ifIndex | IfAlias |
   |-----------|-----------|--------------|----------|-----------|---------|---------|
   | [Default] |    ETS    |      50      | 0-2,4-7  |  Глобальная   | &nbsp;  | &nbsp;  |
   |    SMB    |    ETS    |      50      |    3     |  Глобальная   | &nbsp;  | &nbsp;  |

   ---

9. (Необязательно) Создайте два класса дополнительный трафик для трафика IP-адрес клиента. 

   >[!TIP]
   >Значения «IP1» и «IP2» можно опустить.

   ```PowerShell
   New-NetQosTrafficClass "IP1" -Priority 1 -bandwidthpercentage 10 -algorithm ETS
   ```

   _**Результаты:** _


   | Имя | Алгоритм | Bandwidth(%) | Priority | PolicySet | ifIndex | IfAlias |
   |------|-----------|--------------|----------|-----------|---------|---------|
   | IP1  |    ETS    |      10      |    1     |  Глобальная   | &nbsp;  | &nbsp;  |

   ---

   ```PowerShell
   New-NetQosTrafficClass "IP2" -Priority 2 -bandwidthpercentage 10 -algorithm ETS
   ```

   _**Результаты:** _


   | Имя | Алгоритм | Bandwidth(%) | Priority | PolicySet | ifIndex | IfAlias |
   |------|-----------|--------------|----------|-----------|---------|---------|
   | IP2  |    ETS    |      10      |    2     |  Глобальная   | &nbsp;  | &nbsp;  |

   ---

10. Просмотр классы трафика QoS.

    ```PowerShell
    Get-NetQosTrafficClass | ft -AutoSize
    ```

    _**Результаты:** _


    |   Имя    | Алгоритм | Bandwidth(%) | Priority | PolicySet | ifIndex | IfAlias |
    |-----------|-----------|--------------|----------|-----------|---------|---------|
    | [Default] |    ETS    |      30      |  0,4-7   |  Глобальная   | &nbsp;  | &nbsp;  |
    |    SMB    |    ETS    |      50      |    3     |  Глобальная   | &nbsp;  | &nbsp;  |
    |    IP1    |    ETS    |      10      |    1     |  Глобальная   | &nbsp;  | &nbsp;  |
    |    IP2    |    ETS    |      10      |    2     |  Глобальная   | &nbsp;  | &nbsp;  |

    ---

11. (Необязательно) Переопределите отладчика.<p>По умолчанию присоединенному отладчику блокирует NetQos. 

    ```PowerShell
    Set-ItemProperty HKLM:"\SYSTEM\CurrentControlSet\Services\NDIS\Parameters" AllowFlowControlUnderDebugger -type DWORD -Value 1 –Force
    Get-ItemProperty HKLM:"\SYSTEM\CurrentControlSet\Services\NDIS\Parameters" | ft AllowFlowControlUnderDebugger
    ```

    _**Результаты:** _  

    ```
    AllowFlowControlUnderDebugger
    -----------------------------
    1
    ```

## <a name="step-5-verify-the-rdma-configuration-mode-1"></a>Шаг 5. Проверьте конфигурацию RDMA \(режим 1\) 

Вы хотите убедиться, что структуре настроен правильно, прежде чем создать виртуальный коммутатор и переход к RDMA \(режим 2\).

Ниже показано текущее состояние указанных узлах Hyper-V.

![Тест RDMA](../../media/Converged-NIC/4-datacenter-test-rdma.jpg)


1. Проверьте конфигурацию RDMA.

   ```PowerShell
   Get-NetAdapterRdma | ft -AutoSize
   ```

   _**Результаты:** _


   |    Имя    |        InterfaceDescription        | Enabled |
   |------------|------------------------------------|---------|
   | TEST-40G-1 | Адаптер Mellanox ConnectX-4 VPI #2 |  True   |
   | ТЕСТ-40G-2 |  Адаптер Mellanox ConnectX-4 VPI   |  True   |

   ---

2. Определить **ifIndex** значение целевой адаптеров.<p>Это значение используется в последующих шагах, при запуске скрипта, который можно скачать.   

   ```PowerShell
   Get-NetIPConfiguration -InterfaceAlias "TEST*" | ft InterfaceAlias,InterfaceIndex,IPv4Address
   ```

   _**Результаты:** _


   | InterfaceAlias | InterfaceIndex |  IPv4-адрес  |
   |----------------|----------------|---------------|
   |   TEST-40G-1   |       14       | {192.168.1.3} |
   |   ТЕСТ-40G-2   |       13       | {192.168.2.3} |

   ---

3. Скачайте [DiskSpd.exe программа](https://aka.ms/diskspd) и извлеките его содержимое в C:\TEST\.

4. Скачайте [сценарий PowerShell RDMA теста](https://github.com/Microsoft/SDN/blob/master/Diagnostics/Test-Rdma.ps1) в тестовой папке на локальном диске, например, C:\TEST\.

5. Запустите **Rdma.ps1 теста** сценарий PowerShell для передачи значения ifIndex в сценарий, а также IP-адрес первого удаленного адаптера в той же виртуальной сети.<p>В этом примере передает сценарий **ifIndex** значения 14 удаленной сети адаптера IP-адресом 192.168.1.5.

   ```PowerShell
   C:\TEST\Test-RDMA.PS1 -IfIndex 14 -IsRoCE $true -RemoteIpAddress 192.168.1.5 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
   ```

   _**Результаты:** _ 

   ```   
   VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\diskspd.exe
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

6. Запустите **Rdma.ps1 теста** сценарий PowerShell для передачи значения ifIndex в сценарий, а также IP-адрес второй удаленный адаптер в той же виртуальной сети.<p>В этом примере передает сценарий **ifIndex** значение 13 на IP-адрес адаптера удаленной сети 192.168.2.5.

   ```PowerShell
   C:\TEST\Test-RDMA.PS1 -IfIndex 13 -IsRoCE $true -RemoteIpAddress 192.168.2.5 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
   ```

   _**Результаты:** _ 

   ```   
   VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\diskspd.exe
   VERBOSE: The adapter TEST-40G-2 is a physical adapter
   VERBOSE: Underlying adapter is RoCE. Checking if QoS/DCB/PFC is configured on each physical adapter(s)
   VERBOSE: QoS/DCB/PFC configuration is correct.
   VERBOSE: RDMA configuration is correct.
   VERBOSE: Checking if remote IP address, 192.168.2.5, is reachable.
   VERBOSE: Remote IP 192.168.2.5 is reachable.
   VERBOSE: Disabling RDMA on adapters that are not part of this test. RDMA will be enabled on them later.
   VERBOSE: Testing RDMA traffic now for. Traffic will be sent in a parallel job. Job details:
   VERBOSE: 0 RDMA bytes written per second
   VERBOSE: 0 RDMA bytes sent per second
   VERBOSE: 541185606 RDMA bytes written per second
   VERBOSE: 34821478 RDMA bytes sent per second
   VERBOSE: 954717307 RDMA bytes written per second
   VERBOSE: 35040816 RDMA bytes sent per second
   VERBOSE: Enabling RDMA on adapters that are not part of this test. RDMA was disabled on them prior to sending RDMA traffic.
   VERBOSE: RDMA traffic test SUCCESSFUL: RDMA traffic was sent to 192.168.2.5
   ``` 

## <a name="step-6-create-a-hyper-v-vswitch-on-your-hyper-v-hosts"></a>Шаг 6. Создание виртуального коммутатора Hyper-V на узлах Hyper-V


На следующем рисунке показан узел 1 Hyper-V виртуальный коммутатор.

![Создание виртуального коммутатора Hyper-V](../../media/Converged-NIC/5-datacenter-create-vswitch.jpg)

1. Создайте виртуальный коммутатор в УСТАНОВИТЬ режим на узле Hyper-V 1.

   ```PowerShell
   New-VMSwitch –Name "VMSTEST" –NetAdapterName "TEST-40G-1","TEST-40G-2" -EnableEmbeddedTeaming $true -AllowManagementOS $true
   ```

   _**Результат:** _


   |  Имя   | SwitchType | NetAdapterInterfaceDescription |
   |---------|------------|--------------------------------|
   | VMSTEST |  Внешняя  |        Объединенные в группу интерфейс        |

   ---

2. Просмотр группы физических адаптеров в НАБОРЕ данных.

   ```PowerShell
   Get-VMSwitchTeam -Name "VMSTEST" | fl
   ```

   _**Результаты:** _  

   ```
   Name: VMSTEST  
   Id: ad9bb542-dda2-4450-a00e-f96d44bdfbec  
   NetAdapterInterfaceDescription: {Mellanox ConnectX-3 Pro Ethernet Adapter, Mellanox ConnectX-3 Pro Ethernet Adapter #2}  
   TeamingMode: SwitchIndependent  
   LoadBalancingAlgorithm: Dynamic   
   ```

3. Отображение двух представлений виртуального сетевого адаптера узла

   ```PowerShell
    Get-NetAdapter
   ```

   _**Результаты:** _


   |        Имя         |        InterfaceDescription         | ifIndex | Состояние |    macAddress     | Скорость линии |
   |---------------------|-------------------------------------|---------|--------|-------------------|-----------|
   | vEthernet (VMSTEST) | Hyper-V виртуального сетевого адаптера #2 |   28    |   Вверх   | E4-1D-2D-07-40-71 |  80 Гбит/с  |

   ---

4. Просмотр дополнительных свойств виртуального сетевого адаптера узла. 

   ```PowerShell
   Get-VMNetworkAdapter -ManagementOS
   ```

   _**Результаты:** _


   |  Имя   | IsManagementOs | VMName  |  SwitchName  | macAddress | Состояние | IPAddresses |
   |---------|----------------|---------|--------------|------------|--------|-------------|
   | VMSTEST |      True      | VMSTEST | E41D2D074071 |    {ОК}    | &nbsp; |             |

   ---


5. Проверьте сетевое подключение к Удаленный адаптер 101 виртуальной локальной сети.

   ```PowerShell
   Test-NetConnection 192.168.1.5 
   ```

   _**Результаты:** _  

   ```
   WARNING: Ping to 192.168.1.5 failed -- Status: DestinationHostUnreachable

   ComputerName   : 192.168.1.5
   RemoteAddress  : 192.168.1.5
   InterfaceAlias : vEthernet (CORP-External-Switch)
   SourceAddress  : 10.199.48.170
   PingSucceeded  : False
   PingReplyDetails (RTT) : 0 ms
   ```

## <a name="step-7-remove-the-access-vlan-setting"></a>Шаг 7. Удалите параметр доступа VLAN

На этом шаге вы удалите параметр доступа VLAN из физическому сетевому Адаптеру, а также для установки VLANID, используя виртуальный коммутатор.

Необходимо удалить параметр доступа VLAN, чтобы предотвратить оба автоматического присвоения тегов исходящий трафик с неправильный идентификатор виртуальной локальной сети и из фильтрации входящего трафика, который не соответствует ИД виртуальной ЛС. доступ

1. Удалите параметр.

   ```PowerShell
   Set-NetAdapterAdvancedProperty -Name "Test-40G-1" -RegistryKeyword VlanID -RegistryValue "0"
   Set-NetAdapterAdvancedProperty -Name "Test-40G-2" -RegistryKeyword VlanID -RegistryValue "0"
   ```

2. Задать ИД виртуальной ЛС.

   ```PowerShell
   Set-VMNetworkAdapterVlan -VMNetworkAdapterName "VMSTEST" -VlanId "101" -Access -ManagementOS
   Get-VMNetworkAdapterVlan -ManagementOS -VMNetworkAdapterName "VMSTEST"
   ```

   _**Результаты:** _  

   ```
   VMName VMNetworkAdapterName Mode   VlanList
   ------ -------------------- ----   --------
          VMSTEST              Access 101     
   ```


3. Проверьте сетевое подключение.

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

   >**ВАЖНЫЕ** Если результаты не похожи на примере результатов, и эта команда завершится ошибкой с сообщением «предупреждение: Сбой проверки связи для 192.168.1.5 — состояние: DestinationHostUnreachable», убедитесь, что «vEthernet (VMSTEST)» имеет правильный IP-адрес.
   >
   >```PowerShell
   >Get-NetIPAddress -InterfaceAlias "vEthernet (VMSTEST)"
   >```
   >
   >Если не задать IP-адрес, устранить проблему.
   >
   >```PowerShell
   >New-NetIPAddress -InterfaceAlias "vEthernet (VMSTEST)" -IPAddress 192.168.1.3 -PrefixLength 24
   >
   >IPAddress : 192.168.1.3
   >InterfaceIndex: 37
   >InterfaceAlias: vEthernet (VMSTEST)
   >AddressFamily : IPv4
   >Type  : Unicast
   >PrefixLength  : 24
   >PrefixOrigin  : Manual
   >SuffixOrigin  : Manual
   >AddressState  : Tentative
   >ValidLifetime : Infinite ([TimeSpan]::MaxValue)
   >PreferredLifetime : Infinite ([TimeSpan]::MaxValue)
   >SkipAsSource  : False
   >PolicyStore   : ActiveStore
   >```  


4. Переименовать управления сетевой карты.

   ```PowerShell
   Rename-VMNetworkAdapter -ManagementOS -Name “VMSTEST” -NewName “MGT”
   Get-VMNetworkAdapter -ManagementOS
   ```

   _**Результаты:** _ 


   |         Имя         | IsManagementOs | VMName |      SwitchName      |  macAddress  | Состояние | IPAddresses |
   |----------------------|----------------|--------|----------------------|--------------|--------|-------------|
   | CORP-внешний коммутатор |      True      | &nbsp; | CORP-внешний коммутатор | 001B785768AA |  {ОК}  |   &nbsp;    |
   |         КОММУТАТОРУ          |      True      | &nbsp; |       VMSTEST        | E41D2D074071 |  {ОК}  |   &nbsp;    |

   ---

5. Просмотр свойств сетевого Адаптера.

   ```PowerShell
   Get-NetAdapter
   ```

   _**Результаты:** _


   |      Имя       |        InterfaceDescription         | ifIndex | Состояние |    macAddress     | Скорость линии |
   |-----------------|-------------------------------------|---------|--------|-------------------|-----------|
   | vEthernet (MGT) | Hyper-V виртуального сетевого адаптера #2 |   28    |   Вверх   | E4-1D-2D-07-40-71 |  80 Гбит/с  |

   ---

## <a name="step-8-test-hyper-v-vswitch-rdma"></a>Шаг 8. Тестирование виртуального коммутатора Hyper-V RDMA

Ниже показано текущее состояние узлов Hyper-V, включая виртуальный коммутатор на узле 1 Hyper-V.

![Тестирование виртуального коммутатора Hyper-V](../../media/Converged-NIC/6-datacenter-test-vswitch-rdma.jpg)

1. Задайте приоритет, добавление тегов на виртуальном сетевом адаптере узла, в дополнение к предыдущие параметры виртуальной локальной сети.

   ```PowerShell    
   Set-VMNetworkAdapter -ManagementOS -Name "MGT" -IeeePriorityTag on
   Get-VMNetworkAdapter -ManagementOS -Name "MGT" | fl Name,IeeePriorityTag
   ```

   _**Результаты:** _  

   Имя: КОММУТАТОРУ  
   IeeePriorityTag :  Включено  

2. Создайте две виртуальные сетевые карты узла для RDMA и подключите их к vSwitch VMSTEST.

   ```PowerShell    
   Add-VMNetworkAdapter –SwitchName "VMSTEST" –Name SMB1 –ManagementOS
   Add-VMNetworkAdapter –SwitchName "VMSTEST" –Name SMB2 –ManagementOS
   ```

3. Просмотр свойств сетевого Адаптера управления.

   ```PowerShell    
   Get-VMNetworkAdapter -ManagementOS
   ```

   _**Результаты:** _ 


   |         Имя         | IsManagementOs |        VMName        |  SwitchName  | macAddress | Состояние | IPAddresses |
   |----------------------|----------------|----------------------|--------------|------------|--------|-------------|
   | CORP-внешний коммутатор |      True      | CORP-внешний коммутатор | 001B785768AA |    {ОК}    | &nbsp; |             |
   |         Коммутатору          |      True      |       VMSTEST        | E41D2D074071 |    {ОК}    | &nbsp; |             |
   |         SMB1         |      True      |       VMSTEST        | 00155D30AA00 |    {ОК}    | &nbsp; |             |
   |         SMB2         |      True      |       VMSTEST        | 00155D30AA01 |    {ОК}    | &nbsp; |             |

   ---

## <a name="step-9-assign-an-ip-address-to-the-smb-host-vnics-vethernet-smb1-and-vethernet-smb2"></a>Шаг 9. Назначить IP-адресом vEthernet виртуальных сетевых адаптеров узла SMB \(SMB1\) и vEthernet \(SMB2\)

TEST-40G-1 и физическими адаптерами ТЕСТА-40G-2 по-прежнему иметь доступа VLAN, 101 и 102 настроен. По этой причине адаптеры пометить трафик — и она выполняется успешно. Ранее настроен идентификаторы виртуальной локальной сети обоих pNIC нулю, то значение VMSTEST vSwitch 101 виртуальной локальной сети. После этого по-прежнему можно было проверить связь с Удаленный адаптер 101 виртуальной локальной сети с помощью виртуального сетевого адаптера Коммутатору, но в настоящее время нет участников 102 виртуальной локальной сети.



1. Удалить параметр доступа VLAN из физический сетевой Адаптер для предотвращения обоих автоматического присвоения тегов исходящий трафик с неправильный идентификатор виртуальной локальной сети и чтобы предотвратить фильтрацию входящего трафика, который не соответствует ИД виртуальной ЛС. доступ

   ```PowerShell    
   New-NetIPAddress -InterfaceAlias "vEthernet (SMB1)" -IPAddress 192.168.2.111 -PrefixLength 24
   ```

   _**Результаты:** _  

   ```   
   IPAddress : 192.168.2.111
   InterfaceIndex: 40
   InterfaceAlias: vEthernet (SMB1)
   AddressFamily : IPv4
   Type  : Unicast
   PrefixLength  : 24
   PrefixOrigin  : Manual
   SuffixOrigin  : Manual
   AddressState  : Invalid
   ValidLifetime : Infinite ([TimeSpan]::MaxValue)
   PreferredLifetime : Infinite ([TimeSpan]::MaxValue)
   SkipAsSource  : False
   PolicyStore   : PersistentStore
   ```

2. Адаптер теста удаленного 102 виртуальной локальной сети.

   ```PowerShell
   Test-NetConnection 192.168.2.5 
   ```

   _**Результаты:** _  

   ```
   ComputerName   : 192.168.2.5
   RemoteAddress  : 192.168.2.5
   InterfaceAlias : vEthernet (SMB1)
   SourceAddress  : 192.168.2.111
   PingSucceeded  : True
   PingReplyDetails (RTT) : 0 ms
   ```

3. Добавить новый IP-адрес для интерфейса vEthernet \(SMB2\).

   ```PowerShell
   New-NetIPAddress -InterfaceAlias "vEthernet (SMB2)" -IPAddress 192.168.2.222 -PrefixLength 24 
   ```

   _**Результаты:** _ 

   ```
   IPAddress : 192.168.2.222
   InterfaceIndex: 44
   InterfaceAlias: vEthernet (SMB2)
   AddressFamily : IPv4
   Type  : Unicast
   PrefixLength  : 24
   PrefixOrigin  : Manual
   SuffixOrigin  : Manual
   AddressState  : Invalid
   ValidLifetime : Infinite ([TimeSpan]::MaxValue)
   PreferredLifetime : Infinite ([TimeSpan]::MaxValue)
   SkipAsSource  : False
   PolicyStore   : PersistentStore
   ```

4. Повторите проверку.    


5. Поместите виртуальных сетевых адаптеров RDMA узла на существующей виртуальной ЛС 102.

   ```PowerShell
   Set-VMNetworkAdapterVlan -VMNetworkAdapterName "SMB1" -VlanId "102" -Access -ManagementOS
   Set-VMNetworkAdapterVlan -VMNetworkAdapterName "SMB2" -VlanId "102" -Access -ManagementOS

   Get-VMNetworkAdapterVlan -ManagementOS
   ```

   _**Результаты:** _ 

   ```   
   VMName VMNetworkAdapterName Mode VlanList
   ------ -------------------- ---- --------
      SMB1 Access   102 
      Mgt  Access   101 
      SMB2 Access   102 
      CORP-External-Switch Untagged
   ```

6. Проверьте сопоставление SMB1 и SMB2 для базовых физических сетевых адаптеров в виртуальный коммутатор ЗАДАТЬ Team.<p>Связь виртуальный сетевой адаптер узла к физическим сетевым адаптерам случайных и подлежит перераспределения во время создания и удаления. В этом случае можно использовать косвенную механизм для проверки текущей связи. MAC-адреса SMB1 и SMB2 связаны с элементом группы сетевых КАРТ ТЕСТА-40G-2. Это не идеальное решение, так как не имеет связанного виртуального сетевого адаптера узла SMB Test-40G-1 и не позволит для использования трафика RDMA на ссылку, пока он сопоставляется с виртуальной сетевой картой узла SMB.

   ```PowerShell    
   Get-NetAdapterVPort (Preferred)

   Get-NetAdapterVmqQueue
   ```

   _**Результаты:** _ 

   ```
   Name   QueueID MacAddressVlanID Processor VmFriendlyName
   ----   ------- ---------------- --------- --------------
   TEST-40G-1 1   E4-1D-2D-07-40-71 1010:17
   TEST-40G-2 1   00-15-5D-30-AA-00 1020:17
   TEST-40G-2 2   00-15-5D-30-AA-01 1020:17
   ```

7. Просмотр свойств сетевого адаптера виртуальной Машины.

   ```PowerShell
   Get-VMNetworkAdapter -ManagementOS
   ```

   _**Результаты:** _ 

   ```
   Name IsManagementOs VMName SwitchName   MacAddress   Status IPAddresses
   ---- -------------- ------ ----------   ----------   ------ -----------
   CORP-External-Switch True  CORP-External-Switch 001B785768AA {Ok}  
   Mgt  True  VMSTEST  E41D2D074071 {Ok}  
   SMB1 True  VMSTEST  00155D30AA00 {Ok}  
   SMB2 True  VMSTEST  00155D30AA01 {Ok}  
   ```

8. Просмотр адаптера team сетевое сопоставление.<p>Результаты не должен возвращать сведения, поскольку не выполняется сопоставление.

   ```PowerShell
   Get-VMNetworkAdapterTeamMapping -ManagementOS -SwitchName VMSTEST -VMNetworkAdapterName SMB1
   Get-VMNetworkAdapterTeamMapping -ManagementOS -SwitchName VMSTEST -VMNetworkAdapterName SMB2
   ```


9. Сопоставьте SMB1 и SMB2 для разделения членов группы физический сетевой Адаптер, а также для просмотра результатов действий.

   >[!IMPORTANT]
   >Убедитесь, что после завершения этого шага, прежде чем продолжить, или происходит сбой вашей реализации.

   ```PowerShell
   Set-VMNetworkAdapterTeamMapping -ManagementOS -SwitchName VMSTEST -VMNetworkAdapterName "SMB1" -PhysicalNetAdapterName "Test-40G-1"
   Set-VMNetworkAdapterTeamMapping -ManagementOS -SwitchName VMSTEST -VMNetworkAdapterName "SMB2" -PhysicalNetAdapterName "Test-40G-2"

   Get-VMNetworkAdapterTeamMapping -ManagementOS -SwitchName VMSTEST
   ```

   _**Результаты:** _ 

   ```   
   NetAdapterName : Test-40G-1
   NetAdapterDeviceId : {BAA9A00F-A844-4740-AA93-6BD838F8CFBA}
   ParentAdapter  : VMInternalNetworkAdapter, Name = 'SMB1'
   IsTemplate : False
   CimSession : CimSession: .
   ComputerName   : 27-3145G0803
   IsDeleted  : False

   NetAdapterName : Test-40G-2
   NetAdapterDeviceId : {B7AB5BB3-8ACB-444B-8B7E-BC882935EBC8}
   ParentAdapter  : VMInternalNetworkAdapter, Name = 'SMB2'
   IsTemplate : False
   CimSession : CimSession: .
   ComputerName   : 27-3145G0803
   IsDeleted  : False
   ```

10. Подтверждение связи MAC, созданный ранее.

    ```PowerShell    
    Get-NetAdapterVmqQueue
    ```

    _**Результаты:** _ 

    ```   
    Name   QueueID MacAddressVlanID Processor VmFriendlyName
    ----   ------- ---------------- --------- --------------
    TEST-40G-1 1   E4-1D-2D-07-40-71 1010:17
    TEST-40G-1 2   00-15-5D-30-AA-00 1020:17
    TEST-40G-2 1   00-15-5D-30-AA-01 1020:17
    ```


11. Проверить соединение с удаленной системы, поскольку обе виртуальные сетевые карты узла находятся в той же подсети и имеют один и тот же идентификатор виртуальной локальной сети \(102\).

    ```PowerShell 
    Test-NetConnection 192.168.2.111
    ```

    _**Результаты:** _   

    ```
    ComputerName   : 192.168.2.111
    RemoteAddress  : 192.168.2.111
    InterfaceAlias : Test-40G-2
    SourceAddress  : 192.168.2.5
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms
    ```

    ```PowerShell   
    Test-NetConnection 192.168.2.222
    ```

    _**Результаты:** _   

    ```
    ComputerName   : 192.168.2.222
    RemoteAddress  : 192.168.2.222
    InterfaceAlias : Test-40G-2
    SourceAddress  : 192.168.2.5
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms 
    ```
12. Задайте имя, имя коммутатора и теги приоритета.   

    ```PowerShell
    Set-VMNetworkAdapter -ManagementOS -Name "SMB1" -IeeePriorityTag on
    Set-VMNetworkAdapter -ManagementOS -Name "SMB2" -IeeePriorityTag on
    Get-VMNetworkAdapter -ManagementOS -Name "SMB*" | fl Name,SwitchName,IeeePriorityTag,Status
    ```

    _**Результаты:** _   

    ```
    Name: SMB1
    SwitchName  : VMSTEST
    IeeePriorityTag : On 
    Status  : {Ok}

    Name: SMB2
    SwitchName  : VMSTEST
    IeeePriorityTag : On
    Status  : {Ok}
    ```

13. Просмотр свойств сетевого адаптера vEthernet.

    ```PowerShell
    Get-NetAdapterRdma -Name "vEthernet*" | sort Name | ft -AutoSize
    ```

    _**Результаты:** _   

    ```
    Name  InterfaceDescription Enabled
    ----  -------------------- -------
    vEthernet (SMB2)  Hyper-V Virtual Ethernet Adapter #4  False  
    vEthernet (SMB1)  Hyper-V Virtual Ethernet Adapter #3  False  
    vEthernet (MGT)   Hyper-V Virtual Ethernet Adapter #2  False   
    ```

14. Включение сетевых адаптеров vEthernet.  

    ```PowerShell
    Enable-NetAdapterRdma -Name "vEthernet (SMB1)"
    Enable-NetAdapterRdma -Name "vEthernet (SMB2)"
    Get-NetAdapterRdma -Name "vEthernet*" | sort Name | fl *
    ```

    _**Результаты:** _   

    ```
    Name  InterfaceDescription Enabled
    ----  -------------------- -------
    vEthernet (SMB2)  Hyper-V Virtual Ethernet Adapter #4  True   
    vEthernet (SMB1)  Hyper-V Virtual Ethernet Adapter #3  True  
    vEthernet (MGT)   Hyper-V Virtual Ethernet Adapter #2  False
    ```

## <a name="step-10-validate-the-rdma-functionality"></a>Шаг 10. Проверьте функциональные возможности.

Вы хотите проверить функциональные возможности из удаленной системы в локальной системе, имеющей виртуальный коммутатор, оба участникам команды SET виртуальный коммутатор.<p>Так как обе виртуальные сетевые карты узла \(SMB1 и SMB2\) назначаются для 102 виртуальной локальной сети, можно выбрать адаптер 102 виртуальной ЛС в удаленной системе. <p>В этом примере сетевой Адаптер теста-40G-2 не RDMA SMB1 (192.168.2.111) и SMB2 (192.168.2.222).

>[!TIP]
>Может потребоваться отключить брандмауэр в этой системе.  Дополнительные сведения см. политику fabric.
>
>```PowerShell
>Set-NetFirewallProfile -All -Enabled False
>    
>Get-NetAdapterAdvancedProperty -Name "Test-40G-2"
>```
>
>_**Результаты:** _ 
>   
>```
>Name  DisplayNameDisplayValue   RegistryKeyword RegistryValue  
>----  -----------------------   --------------- -------------  
> .
> .
>Test-40G-2VLAN ID102VlanID  {102} 
>```

1. Просмотр свойств сетевого адаптера.

   ```PowerShell
   Get-NetAdapter
   ```

   _**Результаты:** _ 

   ```
   Name  InterfaceDescriptionifIndex Status   MacAddress LinkSpeed
   ----  --------------------------- ------   ---------- ---------
   Test-40G-2Mellanox ConnectX-3 Pro Ethernet A...#3   3 Up   E4-1D-2D-07-43-D140 Gbps
   ```

2. Просмотрите сведения RDMA сетевого адаптера.

   ```PowerShell
   Get-NetAdapterRdma
   ```

   _**Результаты:** _  

   ```
   Name  InterfaceDescription Enabled
   ----  -------------------- -------
   Test-40G-2Mellanox ConnectX-3 Pro Ethernet Adap... True   
   ```

3. Выполните тест трафика RDMA первого физического адаптера.

   ```PowerShell 
   C:\TEST\Test-RDMA.PS1 -IfIndex 3 -IsRoCE $true -RemoteIpAddress 192.168.2.111 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
   ```

   _**Результаты:** _ 

   ```
   VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\diskspd.exe
   VERBOSE: The adapter Test-40G-2 is a physical adapter
   VERBOSE: Underlying adapter is RoCE. Checking if QoS/DCB/PFC is configured on each physical adapter(s)
   VERBOSE: QoS/DCB/PFC configuration is correct.
   VERBOSE: RDMA configuration is correct.
   VERBOSE: Checking if remote IP address, 192.168.2.111, is reachable.
   VERBOSE: Remote IP 192.168.2.111 is reachable.
   VERBOSE: Disabling RDMA on adapters that are not part of this test. RDMA will be enabled on them later.
   VERBOSE: Testing RDMA traffic now for. Traffic will be sent in a parallel job. Job details:
   VERBOSE: 34251744 RDMA bytes sent per second
   VERBOSE: 967346308 RDMA bytes written per second
   VERBOSE: 35698177 RDMA bytes sent per second
   VERBOSE: 976601842 RDMA bytes written per second
   VERBOSE: Enabling RDMA on adapters that are not part of this test. RDMA was disabled on them prior to sending RDMA traffic.
   VERBOSE: RDMA traffic test SUCCESSFUL: RDMA traffic was sent to 192.168.2.111
   ```

4. Выполните тест трафика RDMA для второго физического адаптера.

   ```PowerShell
   C:\TEST\Test-RDMA.PS1 -IfIndex 3 -IsRoCE $true -RemoteIpAddress 192.168.2.222 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
   ```

   _**Результаты:** _ 

   ```
   VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\diskspd.exe
   VERBOSE: The adapter Test-40G-2 is a physical adapter
   VERBOSE: Underlying adapter is RoCE. Checking if QoS/DCB/PFC is configured on each physical adapter(s)
   VERBOSE: QoS/DCB/PFC configuration is correct.
   VERBOSE: RDMA configuration is correct.
   VERBOSE: Checking if remote IP address, 192.168.2.222, is reachable.
   VERBOSE: Remote IP 192.168.2.222 is reachable.
   VERBOSE: Disabling RDMA on adapters that are not part of this test. RDMA will be enabled on them later.
   VERBOSE: Testing RDMA traffic now for. Traffic will be sent in a parallel job. Job details:
   VERBOSE: 0 RDMA bytes written per second
   VERBOSE: 0 RDMA bytes sent per second
   VERBOSE: 485137693 RDMA bytes written per second
   VERBOSE: 35200268 RDMA bytes sent per second
   VERBOSE: 939044611 RDMA bytes written per second
   VERBOSE: 34880901 RDMA bytes sent per second
   VERBOSE: Enabling RDMA on adapters that are not part of this test. RDMA was disabled on them prior to sending RDMA traffic.
   VERBOSE: RDMA traffic test SUCCESSFUL: RDMA traffic was sent to 192.168.2.222
   ```

5. Тест для трафика RDMA с локального компьютера на удаленный компьютер.

    ```PowerShell
    Get-NetAdapter | ft –AutoSize
    ```

    _**Результаты:** _ 

    ```
    Name  InterfaceDescriptionifIndex Status   MacAddress LinkSpeed
    ----  --------------------------- ------   ---------- ---------
    vEthernet (SMB2)  Hyper-V Virtual Ethernet Adapter #4  45 Up   00-15-5D-30-AA-0380 Gbps
    vEthernet (SMB1)  Hyper-V Virtual Ethernet Adapter #3  41 Up   00-15-5D-30-AA-0280 Gbps
    ```

6. Выполните тест трафика RDMA первого виртуального адаптера.    

   ```
   C:\TEST\Test-RDMA.PS1 -IfIndex 41 -IsRoCE $true -RemoteIpAddress 192.168.2.5 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
   ```

   _**Результаты:** _ 

   ```
   VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\diskspd.exe
   VERBOSE: The adapter vEthernet (SMB1) is a virtual adapter
   VERBOSE: Retrieving vSwitch bound to the virtual adapter
   VERBOSE: Found vSwitch: VMSTEST
   VERBOSE: Found the following physical adapter(s) bound to vSwitch: TEST-40G-1, TEST-40G-2
   VERBOSE: Underlying adapter is RoCE. Checking if QoS/DCB/PFC is configured on each physical adapter(s)
   VERBOSE: QoS/DCB/PFC configuration is correct.
   VERBOSE: RDMA configuration is correct.
   VERBOSE: Checking if remote IP address, 192.168.2.5, is reachable.
   VERBOSE: Remote IP 192.168.2.5 is reachable.
   VERBOSE: Disabling RDMA on adapters that are not part of this test. RDMA will be enabled on them later.
   VERBOSE: Testing RDMA traffic now for. Traffic will be sent in a parallel job. Job details:
   VERBOSE: 0 RDMA bytes written per second
   VERBOSE: 0 RDMA bytes sent per second
   VERBOSE: 0 RDMA bytes written per second
   VERBOSE: 15250197 RDMA bytes sent per second
   VERBOSE: 896320913 RDMA bytes written per second
   VERBOSE: 33947559 RDMA bytes sent per second
   VERBOSE: 912160540 RDMA bytes written per second
   VERBOSE: 34091930 RDMA bytes sent per second
   VERBOSE: Enabling RDMA on adapters that are not part of this test. RDMA was disabled on them prior to sending RDMA traffic.
   VERBOSE: RDMA traffic test SUCCESSFUL: RDMA traffic was sent to 192.168.2.5
   ```

7. Выполните тест трафика RDMA на второй виртуальный адаптер.

   ```PowerShell
   C:\TEST\Test-RDMA.PS1 -IfIndex 45 -IsRoCE $true -RemoteIpAddress 192.168.2.5 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
   ```

   _**Результаты:** _ 

   ```
   VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\diskspd.exe
   VERBOSE: The adapter vEthernet (SMB2) is a virtual adapter
   VERBOSE: Retrieving vSwitch bound to the virtual adapter
   VERBOSE: Found vSwitch: VMSTEST
   VERBOSE: Found the following physical adapter(s) bound to vSwitch: TEST-40G-1, TEST-40G-2
   VERBOSE: Underlying adapter is RoCE. Checking if QoS/DCB/PFC is configured on each physical adapter(s)
   VERBOSE: QoS/DCB/PFC configuration is correct.
   VERBOSE: RDMA configuration is correct.
   VERBOSE: Checking if remote IP address, 192.168.2.5, is reachable.
   VERBOSE: Remote IP 192.168.2.5 is reachable.
   VERBOSE: Disabling RDMA on adapters that are not part of this test. RDMA will be enabled on them later.
   VERBOSE: Testing RDMA traffic now for. Traffic will be sent in a parallel job. Job details:
   VERBOSE: 0 RDMA bytes written per second
   VERBOSE: 0 RDMA bytes sent per second
   VERBOSE: 385169487 RDMA bytes written per second
   VERBOSE: 33902277 RDMA bytes sent per second
   VERBOSE: 907354685 RDMA bytes written per second
   VERBOSE: 33923662 RDMA bytes sent per second
   VERBOSE: Enabling RDMA on adapters that are not part of this test. RDMA was disabled on them prior to sending RDMA traffic.
   VERBOSE: RDMA traffic test SUCCESSFUL: RDMA traffic was sent to 192.168.2.5
   ```

Последняя строка в эти выходные данные «тестирования трафика RDMA успешно: Трафика RDMA было отправлено 192.168.2.5,» показывает, что вы успешно настроили сетевой Адаптер, специализирующимся на адаптере.

## <a name="related-topics"></a>См. также 

- [Конфигурации сетевых Адаптеров со схождением с одним сетевым адаптером](cnic-single.md)
- [Конфигурация физического коммутатора для сетевых Адаптеров со схождением](cnic-app-switch-config.md)
- [Устранение неполадок со схождением конфигурации сетевых Адаптеров](cnic-app-troubleshoot.md)
