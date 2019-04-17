---
title: Настройка сетевой КАРТЫ группы схождением сетевых Адаптеров
description: Этот раздел содержит инструкции по настройке схождение выполнено сетевых КАРТ в конфигурацию центра обработки данных в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: f01546f8-c495-4055-8492-8806eee99862
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 1ac6c2915301b1cf64486f24c197ebbf22bb5e2e
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="converged-nic-teamed-nic-configuration"></a>Настройка сетевой КАРТЫ группы схождением сетевых Адаптеров

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Инструкции по развертыванию в конфигурации объединенных сетевых Адаптеров с объединение внедренных коммутатора \(SET\) схождение выполнено сетевых КАРТ в следующих разделах. Пример конфигурации в этом руководстве представлено два узла Hyper-V, узел 1 Hyper-V и узлу 2 Hyper-V.

## <a name="test-connectivity-between-source-and-destination"></a>Проверьте подключение между исходным и конечным

Этот раздел содержит шаги, необходимые для проверки подключения между исходного и конечного узлов Hyper-V.

На рисунке ниже показаны два узла Hyper-V, **узел 1 Hyper-V** и **узле 2 Hyper-V**. 

Обоих узлах Hyper-V имеют два сетевых адаптера. На каждом узле один адаптер подключается к подсети 192.168.1.x/24 и один адаптер подключается к 192.168.2.x/24 подсети.

![Узлы Hyper-V](../../media/Converged-NIC/1-datacenter-test-conn.jpg)

### <a name="test-nic-connectivity-to-the-hyper-v-virtual-switch"></a>Проверка подключения сетевого Адаптера для виртуального коммутатора Hyper-V

Используя этот шаг, можно гарантировать, что физический сетевой Адаптер, для которого будет позже создать виртуальный коммутатор Hyper-V, могут подключаться к конечного узла. 

Этот тест демонстрирует подключения с помощью \(L3\) уровня 3 - или на уровне IP -, а также \(L2\) уровня 2 виртуальные локальные сети \(VLAN\).

Для получения свойств сетевого адаптера, можно использовать следующую команду Windows PowerShell.

    Get-NetAdapter -Name "Test-40G-1" | ft -AutoSize
     
Ниже приведены примеры результатов выполнения этой команды.

|Имя|InterfaceDescription|ifIndex|Состояние|MAC-адрес|Скорость линии|
|-----|--------------------|-------|-----|----------|---------|
|
|Тест-40G-1|Адаптер Mellanox ConnectX 3 Pro Ethernet|11|Вверх|E4-1D-2D-07-43-D0|40 Гбит/с|

Один из следующих команд можно использовать для получения свойств дополнительного адаптера, включая IP-адрес.

    Get-NetIPAddress -InterfaceAlias "Test-40G-1"

    Get-NetIPAddress -InterfaceAlias "TEST-40G-1" | Where-Object {$_.AddressFamily -eq "IPv4"} | fl InterfaceAlias,IPAddress
    
Ниже приведены примеры результатов из этих команд.

|Параметр|Значение|
|---------|-----|
|
|IP-адрес| 192.168.1.3|
|InterfaceIndex|11|
|InterfaceAlias|Тест-40G-1|
|Адресов|IPv4|
|Тип| Одноадресная рассылка|
|PrefixLength|24|

### <a name="verify-that-nic-team-member-has-a-valid-ip-address"></a>Убедитесь, что член группы сетевых КАРТ имеет допустимый IP-адрес

Используйте этот шаг и убедитесь, что другие группы сетевых КАРТ или \(SET\) коммутатора встроенные группы члена физических сетевых адаптеров \(pNICs\) также иметь допустимый IP-адрес.

Для этого шага можно использовать отдельной подсети, \ (xxx.xxx.** 2**.xxx vs xxx.xxx. **1**. xxx\), чтобы облегчить отправки от этого адаптера на конечный. 

В противном случае если оба pNICs обнаружить в той же подсети, балансировку нагрузки стек Windows TCP/IP между интерфейсы и усложняется простой проверки.

Для получения свойства второго сетевого адаптера, можно использовать следующую команду Windows PowerShell.

    Get-NetAdapter -Name "Test-40G-2" | ft -AutoSize

Ниже приведены примеры результатов выполнения этой команды.

|Имя |InterfaceDescription |ifIndex |Состояние |MAC-адрес |Скорость линии|
|----|--------------------|-------|------|----------|---------|
|
|ТЕСТ-40G-2 |Mellanox ConnectX 3 Pro Ethernet A.... \ #2 |13 |Вверх |E4-1D-2D-07-40-70 |40 Гбит/с|

Один из следующих команд можно использовать для получения свойств дополнительного адаптера, включая IP-адрес.

    Get-NetIPAddress -InterfaceAlias "Test-40G-2"

    Get-NetIPAddress -InterfaceAlias "Test-40G-2" | Where-Object {$\_.AddressFamily -eq "IPv4"} | fl InterfaceAlias,IPAddress

Ниже приведены примеры результатов из этих команд.

|Параметр|Значение|
|---------|-----|
|
|IP-адрес|192.168.2.3|
|InterfaceIndex|13|
|InterfaceAlias|ТЕСТ-40G-2|
|Адресов|IPv4|
|Тип|Одноадресная рассылка|
|PrefixLength|24|

### <a name="verify-that-additional-nics-have-valid-ip-addresses"></a>Убедитесь, что дополнительные адаптеры действительных IP-адресов

Этот шаг можно использовать для убедитесь, что второй Адаптер имеет допустимый IP-адрес.

Для этого шага можно использовать отдельной подсети, \ (xxx.xxx.** 2**.xxx vs xxx.xxx. **1**. xxx\), чтобы облегчить отправки от этого адаптера на конечный. 

В противном случае если оба pNICs обнаружить в той же подсети, балансировку нагрузки стек Windows TCP/IP между интерфейсы и усложняется простой проверки.

Для получения свойства второго сетевого адаптера, можно использовать следующую команду Windows PowerShell.

    Get-NetAdapter -Name "Test-40G-2" | ft -AutoSize

Ниже приведены примеры результатов выполнения этой команды.

|Имя |InterfaceDescription |ifIndex |Состояние |MAC-адрес |Скорость линии|
|----|--------------------|-------|------|----------|---------|
|
|ТЕСТ-40G-2 |Mellanox ConnectX 3 Pro Ethernet A.... \ #2 |13 |Вверх |E4-1D-2D-07-40-70 |40 Гбит/с|

Один из следующих команд можно использовать для получения свойств дополнительного адаптера, включая IP-адрес.
    
    Get-NetIPAddress -InterfaceAlias "Test-40G-2"

    Get-NetIPAddress -InterfaceAlias "Test-40G-2" | Where-Object {$_.AddressFamily -eq "IPv4"} | fl InterfaceAlias,IPAddress

Ниже приведены примеры результатов из этих команд.

|Параметр|Значение|
|---------|-----|
|
|IP-адрес|192.168.2.3|
|InterfaceIndex|13|
|InterfaceAlias|ТЕСТ-40G-2|
|Адресов|IPv4|
|Тип|Одноадресная рассылка|
|PrefixLength|24|

### <a name="ensure-that-source-and-destination-can-communicate"></a>Убедитесь, что исходный и конечный могут обмениваться данными

Этот шаг можно использовать для проверки Двусторонняя связь \ (проверка связи из источника для назначения и обратно на обоих systems\).  В следующем примере **NetConnection теста** использовать команду Windows PowerShell, но если вы предпочитаете, можно использовать **ping** команды. 

    Test-NetConnection 192.168.1.5

Ниже приведены примеры результатов выполнения этой команды.

|Параметр|Значение|
|---------|-----|
|
|Имя компьютера|192.168.1.5|
|RemoteAddress|192.168.1.5|
|InterfaceAlias|Тест-40G-1|
|SourceAddress|192.168.1.3|
|PingSucceeded|False|
|PingReplyDetails \(RTT\)|0 ms|

В некоторых случаях может потребоваться отключить брандмауэр Windows в режиме повышенной безопасности, для успешного выполнения этого теста. Если вы отключите брандмауэр, помнить безопасности и убедитесь, что конфигурацию соответствует требованиям к безопасности вашей организации.

Следующая команда позволяет отключить все профили брандмауэра.

    Set-NetFirewallProfile -All -Enabled False
    
После отключения брандмауэра, можно использовать следующую команду для проверки подключения.

    Test-NetConnection 192.168.1.5

Ниже приведены примеры результатов выполнения этой команды.

|Параметр|Значение|
|---------|-----|
|
|Имя компьютера|192.168.1.5|
|RemoteAddress|192.168.1.5|
|InterfaceAlias|Тест-40G-1|
|SourceAddress|192.168.1.3|
|PingSucceeded|False|
|PingReplyDetails \(RTT\)|0 ms|

### <a name="verify-connectivity-for-additional-nics"></a>Проверьте сетевое подключение для дополнительных сетевых адаптеров

На этом этапе можно повторить предыдущие действия для всех последующих pNICs, включенных в объединении сетевых КАРТ или НАБОРА.

Можно использовать следующую команду, чтобы протестировать подключение.
    
    Test-NetConnection 192.168.2.5

Ниже приведены примеры результатов выполнения этой команды.

|Параметр|Значение|
|---------|-----|
|
|Имя компьютера|192.168.2.5|
|RemoteAddress|192.168.2.5|
|InterfaceAlias|Тест-40G-2|
|SourceAddress|192.168.2.3|
|PingSucceeded|False|
|PingReplyDetails \(RTT\)|0 ms|


## <a name="configure-vlans"></a>Настройка виртуальных локальных сетей

Для этого шага, сетевые адаптеры в **доступа** режим. Однако при создании виртуального коммутатора Hyper-V \(vSwitch\) Далее в этом руководстве свойства виртуальной локальной сети применяются на уровне порта виртуальный коммутатор. 

Поскольку коммутатор может размещаться несколько виртуальных ЛС, она необходима для элемента верхнего \(ToR\) физического коммутатора его порт настроен магистральный режим.

Обратитесь к документации коммутатора ToR инструкции о том, как настроить режим магистрали на коммутаторе.

На рисунке ниже показаны два узла Hyper-V с двумя сетевыми адаптерами, каждый с 101 виртуальной локальной сети и 102 виртуальной локальной сети настроены в свойствах сетевого адаптера.

![Настройка виртуальных локальных сетей](../../media/Converged-NIC/2-datacenter-configure-vlans.jpg)

### <a name="configure-the-vlan-ids-for-both-nics"></a>Настройка идентификаторов виртуальной локальной сети для оба сетевых адаптера

Этот шаг можно использовать для настройки идентификаторов виртуальной локальной сети для сетевых адаптеров, установить в узлов Hyper-V.

В соответствии с институтом инженеров по электротехнике и электронике \(IEEE\) сети стандартов, свойства \(QoS\) качества обслуживания в физическом NIC действовать от 802.1 p заголовок, который будет внедрен в 802.1Q \(VLAN\) заголовка, когда вы настраиваете идентификатор виртуальной ЛС

#### <a name="configure-nic-test-40g-1"></a>Настройка сетевого Адаптера Test-40G-1

С помощью следующих команд настройте идентификатор виртуальной ЛС для первого сетевого Адаптера, тест-40G-1, просмотрев полученную конфигурацию.

    
    Set-NetAdapterAdvancedProperty -Name "Test-40G-1" -RegistryKeyword VlanID -RegistryValue "101"
    Get-NetAdapterAdvancedProperty -Name "Test-40G-1" | Where-Object {$_.RegistryKeyword -eq "VlanID"} | ft -AutoSize
    
Ниже приведены примеры результатов выполнения этой команды.

|Имя |Отображаемое имя| DisplayValue| RegistryKeyword |RegistryValue|
|----|-----------|------------|---------------|-------------|
|
|ТЕСТ-40G-1|ИДЕНТИФИКАТОР ВИРТУАЛЬНОЙ ЛС|101|VlanID|{101}|


Убедитесь, что идентификатор виртуальной ЛС действует зависит от реализации адаптера сети, используя следующую команду для перезапуска сетевого адаптера.

    Restart-NetAdapter -Name "Test-40G-1"

Можно использовать следующую команду, чтобы убедиться, что состояния сетевого адаптера **вверх** перед продолжением.

    Get-NetAdapter -Name "Test-40G-1" | ft -AutoSize

Ниже приведены примеры результатов выполнения этой команды.

|Имя|InterfaceDescription|ifIndex| Состояние|MAC-адрес|Скорость линии|
|----|--------------------|-------|------|----------| ---------|
|
|Тест-40G-1|Mellanox ConnectX 3 Pro Ethernet Ada...|11|Вверх|E4-1D-2D-07-43-D0|40 Гбит/с|

#### <a name="configure-nic-test-40g-2"></a>Настройка сетевого Адаптера Test-40G-2

С помощью следующих команд настройте идентификатор виртуальной ЛС для второй сетевой Адаптер, тест-40G-2, просмотрев полученную конфигурацию.

    
    Set-NetAdapterAdvancedProperty -Name "Test-40G-2" -RegistryKeyword VlanID -RegistryValue "102"
    Get-NetAdapterAdvancedProperty -Name "Test-40G-2" | Where-Object {$_.RegistryKeyword -eq "VlanID"} | ft -AutoSize
    

Ниже приведены примеры результатов выполнения этой команды.

|Имя |Отображаемое имя| DisplayValue| RegistryKeyword |RegistryValue|
|----|-----------|------------|---------------|-------------|
|
|ТЕСТ-40G-2|ИДЕНТИФИКАТОР ВИРТУАЛЬНОЙ ЛС|102|VlanID|{102}|

Убедитесь, что идентификатор виртуальной ЛС действует зависит от реализации адаптера сети, используя следующую команду для перезапуска сетевого адаптера.

`Restart-NetAdapter -Name "Test-40G-2"  `              

Можно использовать следующую команду, чтобы убедиться, что состояния сетевого адаптера **вверх** перед продолжением.

    Get-NetAdapter -Name "Test-40G-1" | ft -AutoSize

Ниже приведены примеры результатов выполнения этой команды.

|Имя|InterfaceDescription|ifIndex| Состояние|MAC-адрес|Скорость линии|
|----|--------------------|-------|------|----------| ---------|
|
|Тест-40G-2 |Mellanox ConnectX 3 Pro Ethernet Ada... |11 |Вверх |E4-1D-2D-07-43-D1 |40 Гбит/с|


### <a name="verify-connectivity"></a>Проверьте сетевое подключение

В этом разделе можно использовать для проверки подключения, после перезагрузки сетевых адаптеров. Вы можете подтвердить подключения после применения тега виртуальной локальной сети к обоим устройствам. В случае сбоя подключения можно проверить коммутатор виртуальной ЛС конфигурации или назначения участие в той же виртуальной сети. 

>[!IMPORTANT]
>После выполнения шагов в предыдущем разделе он может занять несколько секунд для устройства для перезагрузки и становятся доступны в сети.

#### <a name="verify-connectivity-for-nic-test-40g-1"></a>Проверьте сетевое подключение для сетевого Адаптера Test-40G-1

Для проверки подключения для первого сетевого Адаптера, можно выполнить следующую команду.

    Test-NetConnection 192.168.1.5
    
Ниже приведены примеры результатов выполнения этой команды.

|Параметр|Значение|
|---------|-----|
|
|Имя компьютера|192.168.1.5|
|RemoteAddress|192.168.1.5|
|InterfaceAlias|Тест-40G-1|
|SourceAddress|192.168.1.5|
|PingSucceeded|Значение true|
|PingReplyDetails \(RTT\)|0 ms|

#### <a name="verify-connectivity-for-nic-test-40g-2"></a>Проверьте сетевое подключение для сетевого Адаптера Test-40G-2

В этом разделе можно использовать для проверки подключения для сетевых КАРТ Test-40G-2.

Можно использовать следующую команду для проверки подключения для второй сетевой адаптер.
    
    Test-NetConnection 192.168.2.5
    
Ниже приведены примеры результатов выполнения этой команды.

|Параметр|Значение|
|---------|-----|
|
|Имя компьютера|192.168.2.5|
|RemoteAddress|192.168.2.5|
|InterfaceAlias|Тест-40G-2|
|SourceAddress|192.168.2.3|
|PingSucceeded|Значение true|
|PingReplyDetails \(RTT\)|0 ms|

A **NetConnection теста** или сбой ping, которая возникает сразу после выполнения **перезагрузки NetAdapter** является обычной ситуацией, поэтому дождитесь полной инициализации сетевого адаптера, а затем повторите попытку.

Если работы подключений 101 виртуальной локальной сети, но подключения 102 виртуальной локальной сети не работают, проблема может быть коммутатора необходимо разрешить трафик на порту на нужный виртуальной локальной сети. Для этого можно проверить, временно значение адаптеров отказавший 101 виртуальной локальной сети, а повторяющихся проверку подключения к.

## <a name="configure-quality-of-service-qos"></a>Настройка качества \(QoS\) службы

Следующий шаг — Настройка \(QoS\) качества обслуживания, который необходимо сначала установить Windows Server 2016 функция \(DCB\) мост для центра обработки данных.

На рисунке ниже показаны узлов Hyper-V после успешной настройки виртуальных локальных сетей на предыдущем шаге.

![Настройка качества обслуживания](../../media/Converged-NIC/3-datacenter-configure-qos.jpg)

### <a name="install-data-center-bridging-dcb"></a>Установить мост \(DCB\) центра обработки данных

Этот шаг можно использовать, чтобы установить и включить DCB. В большинстве случаев этот шаг является необязательным для реализации iWarp, но это необходимо в масштабах структуры, например, для сценариев стойку между.

Можно использовать следующую команду для установки мост центра обработки данных на каждом из узлов Hyper-V. 

    Install-WindowsFeature Data-Center-Bridging

Ниже приведены примеры результатов выполнения этой команды.

|Успех |Требуется перезагрузка |Код выхода|Результат функции|
|------- |-------------- |--------- |-------------- |
|
|Значение true |Нет |Успех| {Мост для центра обработки данных}|

### <a name="set-the-qos-policies-for-smb-direct"></a>Настроить политики QoS для SMB Direct 

Можно использовать следующую команду для настройки политик QoS для SMB Direct.

    New-NetQosPolicy "SMB" -NetDirectPortMatchCondition 445 -PriorityValue8021Action 3

Ниже приведены примеры результатов выполнения этой команды.

|Параметр|Значение|
|---------|-----|
|
|Имя |SMB|
|Владелец|\(Machine\) групповой политики|
|NetworkProfile|Все|
|Приоритет|127|
|JobObject|&nbsp;| 
|NetDirectPort|445
|PriorityValue|3

### <a name="set-policies-for-other-traffic-on-the-interface"></a>Настройка политик для другой трафик от интерфейса 

Задавать дополнительные политики качества обслуживания можно использовать следующую команду.

    New-NetQosPolicy "DEFAULT" -Default -PriorityValue8021Action 0
 
Ниже приведены примеры результатов выполнения этой команды.

|Параметр|Значение|
|---------|-----|
|
|Имя | ПО УМОЛЧАНИЮ|
|Владелец|\(Machine\) групповой политики|
|NetworkProfile|Все|
|Приоритет|127|
|Шаблон| По умолчанию|
|JobObject| &nbsp;|
|PriorityValue|0|

### <a name="turn-on-flow-control-for-smb"></a>Включите управление потоком для протокола SMB 

Можно использовать следующие команды для включения управления потоком для SMB и просмотреть результаты.

    Enable-NetQosFlowControl -priority 3
    Get-NetQosFlowControl

Ниже приведены примеры результатов выполнения этой команды.

|Приоритет|Включен|PolicySet|IfIndex|IfAlias|
|---------|-----|--------- |-------| -------|
|
|0 |False |Глобальные|&nbsp;|&nbsp;|
|1 |False |Глобальные|&nbsp;|&nbsp;|
|2 |False |Глобальные|&nbsp;|&nbsp;|
|3 |Значение true |Глобальные|&nbsp;|&nbsp;|
|4 |False |Глобальные|&nbsp;|&nbsp;|
|5 |False |Глобальные|&nbsp;|&nbsp;|
|6 |False |Глобальные|&nbsp;|&nbsp;|
|7 |False |Глобальные|&nbsp;|&nbsp;|

Если результаты эти результаты не совпадают, так как элементы, отличных от 3 имеют включено значение true, необходимо выполнить следующий шаг. Если результаты соответствуют эти результаты пример только элемент 3 имеет значение "включено" значение True, не требуется выполнение следующего шага и можно перейти вниз до **Включение качества обслуживания для цели и конечных сетевых адаптеров**.

### <a name="ensure-flow-control-is-disabled-for-other-traffic-classes-optional"></a>Убедитесь, что управление потоком отключена для \(Optional\) другие классы трафика

Необходимо выполнить этот шаг, если **управления потоком** не включена для классы трафика 0,1,2,4,5,6 и 7.

Если **управления потоком** уже включен, любой трафик, классов, отличные от 3 \ (0,1,2,4,5,6 и 7\), необходимо отключить **управления потоком** для этих классов. 

>[!NOTE]
>В более сложных конфигураций другие классы трафика может потребоваться управление потоком, однако эти сценарии выходят за рамки данного руководства.

Отключите управление потоком SMB для классы трафика 0,1,2,4,5,6 и 7 и просмотреть результаты, можно использовать следующие команды.

    Disable-NetQosFlowControl -priority 0,1,2,4,5,6,7
    Get-NetQosFlowControl

Ниже приведены примеры результатов выполнения этой команды.

|Приоритет|Включен|PolicySet|IfIndex|IfAlias|
|---------|-----|--------- |-------| -------|
|
|0 |False |Глобальные|&nbsp;|&nbsp;|
|1 |False |Глобальные|&nbsp;|&nbsp;|
|2 |False |Глобальные|&nbsp;|&nbsp;|
|3 |Значение true |Глобальные|&nbsp;|&nbsp;|
|4 |False |Глобальные|&nbsp;|&nbsp;|
|5 |False |Глобальные|&nbsp;|&nbsp;|
|6 |False |Глобальные|&nbsp;|&nbsp;|
|7 |False |Глобальные|&nbsp;|&nbsp;|

### <a name="enable-qos-for-the-local-and-destination-network-adapters"></a>Включение качества обслуживания для локальной и конечных сетевых адаптеров 

На этом этапе можно включить QoS для как локального, так и конечных сетевых адаптеров. Убедитесь, что эти команды на обоих узлах Hyper-V.

#### <a name="enable-qos-for-nic-test-40g-1"></a>Включение качества обслуживания для сетевого Адаптера Test-40G-1

Включение качества обслуживания и просмотрите результаты применения конфигурации можно использовать следующие команды.

    Enable-NetAdapterQos -InterfaceAlias "Test-40G-1"
    Get-NetAdapterQos -Name "Test-40G-1"

Ниже приведены примеры результатов выполнения этой команды.

**Имя**: TEST-40G-1 **включен**: True **возможности**:   

|Параметр|Оборудование|Текущий|
|---------|--------|-------|
|
|MacSecBypass|NotSupported|NotSupported|
|DcbxSupport|Нет|Нет|
|NumTCs(Max/ETS/PFC)|8/8/8|8/8/8|
 
**OperationalTrafficClasses**: 

|УПРАВЛЕНИЕ ТРАФИКОМ|TSA|Пропускная способность|Приоритеты|
|----|-----|--------|-------|
|
|0| Строгий|&nbsp;|0-7|

**OperationalFlowControl**: приоритет 3 включена **OperationalClassifications**:

|Протокол|Тип порта и|Приоритет|
|--------|---------|--------|
|
|По умолчанию|&nbsp;|0|
|NetDirect| 445|3|

#### <a name="enable-qos-for-nic-test-40g-2"></a>Включение качества обслуживания для сетевого Адаптера Test-40G-2

Включение качества обслуживания и просмотрите результаты применения конфигурации можно использовать следующие команды.

    Enable-NetAdapterQos -InterfaceAlias "Test-40G-2"
    Get-NetAdapterQos -Name "Test-40G-2"

 
Ниже приведены примеры результатов выполнения этой команды.

**Имя**: ТЕСТИРОВАНИЕ 40G 2 **включен**: True **возможности**:   

|Параметр|Оборудование|Текущий|
|---------|--------|-------|
|
|MacSecBypass|NotSupported|NotSupported|
|DcbxSupport|Нет|Нет|
|NumTCs(Max/ETS/PFC)|8/8/8|8/8/8|
 
**OperationalTrafficClasses**: 

|УПРАВЛЕНИЕ ТРАФИКОМ|TSA|Пропускная способность|Приоритеты|
|----|-----|--------|-------|
|
|0| Строгий|&nbsp;|0-7|

**OperationalFlowControl**: приоритет 3 включена **OperationalClassifications**:

|Протокол|Тип порта и|Приоритет|
|--------|---------|--------|
|
|По умолчанию|&nbsp;|0|
|NetDirect| 445|3|


### <a name="allocate-50-of-the-bandwidth-reservation-to-smb-direct-rdma"></a>Распределить 50% резервирование полосы пропускания для SMB Direct \(RDMA\)

Чтобы присвоить половины резервирование пропускной способности SMB Direct, можно использовать следующие команды.

    New-NetQosTrafficClass "SMB" -priority 3 -bandwidthpercentage 50 -algorithm ETS

Ниже приведены примеры результатов выполнения этой команды.

|Имя|Алгоритм |Bandwidth(%)| Приоритет |PolicySet |IfIndex |IfAlias |
|----|---------| ------------ |--------| ---------|------- |------- |
|
|SMB | ETS     | 50 |3 |Глобальные |&nbsp;|&nbsp;|                                      
 
Можно использовать следующую команду, чтобы просмотреть сведения о резервировании пропускной способности.

    Get-NetQosTrafficClass | ft -AutoSize

Ниже приведены примеры результатов выполнения этой команды.
 
|Имя|Алгоритм |Bandwidth(%)| Приоритет |PolicySet |IfIndex |IfAlias |
|----|---------| ------------ |--------| ---------|------- |------- |
|
|[По умолчанию]| ETS|50 |0-2,4-7|  Глобальные|&nbsp;|&nbsp;| 
SMB |ETS|50 |3 |Глобальные|&nbsp;|&nbsp;| 

### <a name="create-traffic-classes-for-tenant-ip-traffic-optional"></a>Создать классы трафика для IP-трафика клиента \(optional\)

Этот шаг можно использовать для создания двух классов дополнительного трафика для IP-трафика клиента. 

При выполнении команды в следующем примере значения «IP1» и «IP2» можно опустить, если вы предпочитаете.

    New-NetQosTrafficClass "IP1" -Priority 1 -bandwidthpercentage 10 -algorithm ETS

Ниже приведены примеры результатов выполнения этой команды.

|Имя|Алгоритм |Bandwidth(%)| Приоритет |PolicySet |IfIndex |IfAlias |
|----|---------| ------------ |--------| ---------|------- |------- |
|
|IP1 |ETS |10 |1 |Глобальные|&nbsp;|&nbsp;|


    New-NetQosTrafficClass "IP2" -Priority 2 -bandwidthpercentage 10 -algorithm ETS

Ниже приведены примеры результатов выполнения этой команды.

|Имя|Алгоритм |Bandwidth(%)| Приоритет |PolicySet |IfIndex |IfAlias |
|----|---------| ------------ |--------| ---------|------- |------- |
|
|IP2 |ETS |10 |2 |Глобальные|&nbsp;|&nbsp;|

Можно использовать следующую команду для просмотра классы трафика QoS.

    Get-NetQosTrafficClass | ft -AutoSize

Ниже приведены примеры результатов выполнения этой команды.

|Имя|Алгоритм |Bandwidth(%)| Приоритет |PolicySet |IfIndex |IfAlias |
|----|---------| ------------ |--------| ---------|------- |------- |
|
|[По умолчанию] |ETS |30 |0,4-7 |Глобальные|&nbsp;|&nbsp;|
|SMB |ETS |50 |3 |Глобальные|&nbsp;|&nbsp;|
|IP1 |ETS |10 |1 |Глобальные|&nbsp;|&nbsp;|
|IP2 |ETS |10 |2 |Глобальные|&nbsp;|&nbsp;|

## <a name="configure-debugger-optional"></a>Настройка \(Optional\) отладчика

Этот шаг можно использовать для настройки отладчика.

По умолчанию присоединенным блокирует NetQos. Чтобы переопределить отладчик и просмотреть результаты можно использовать следующие команды.

    Set-ItemProperty HKLM:"\SYSTEM\CurrentControlSet\Services\NDIS\Parameters" AllowFlowControlUnderDebugger -type DWORD -Value 1 –Force
    
    Get-ItemProperty HKLM:"\SYSTEM\CurrentControlSet\Services\NDIS\Parameters" | ft AllowFlowControlUnderDebugger

Ниже приведены примеры результатов выполнения этой команды.

    AllowFlowControlUnderDebugger
    -----------------------------
    1

## <a name="test-rdma-mode-1"></a>Тестирование RDMA \(Mode 1\)

Этот шаг можно использовать, чтобы убедиться, что прежде чем создавать виртуальный коммутатор и переходу на RDMA \(Mode 2\) структуры настроен правильно.

На рисунке ниже показаны текущее состояние узлов Hyper-V.

![Тест RDMA](../../media/Converged-NIC/4-datacenter-test-rdma.jpg)

Чтобы проверить конфигурацию RDMA, можно выполнить следующую команду.

    Get-NetAdapterRdma | ft -AutoSize

Ниже приведены примеры результатов выполнения этой команды.

|Имя |InterfaceDescription |Включен|
|----|--------------------|-------|
|
|ТЕСТ-40G-1| Адаптер Mellanox ConnectX 4 VPI #2 |Значение true|
|ТЕСТ-40G-2| Адаптер Mellanox ConnectX 4 VPI |Значение true|


### <a name="determine-the-ifindex-value-of-your-target-adapter"></a>Определить значение ifIndex адаптера цели

Для обнаружения значение ifIndex адаптера цели можно использовать следующую команду.

    Get-NetIPConfiguration -InterfaceAlias "TEST*" | ft InterfaceAlias,InterfaceIndex,IPv4Address

Ниже приведены примеры результатов выполнения этой команды.

|InterfaceAlias |InterfaceIndex |IPv4-адрес|
|-------------- |-------------- |-----------|
|ТЕСТ-40G-1 |14 |{192.168.1.3}|
|ТЕСТ-40G-2 | 13 |{192.168.2.3}|

### <a name="download-diskspdexe-and-a-powershell-script"></a>Загрузите DiskSpd.exe и сценарий PowerShell

Чтобы продолжить, необходимо сначала загрузить следующие элементы.

- Загрузите и извлеките программу в C:\TEST\ программу DiskSpd.exe[http://tinyurl.com/z68h3rc](http://tinyurl.com/z68h3rc)

- Скачайте скрипт powershell Test-RDMA C:\TEST\[https://github.com/Microsoft/SDN/blob/master/Diagnostics/Test-Rdma.ps1](https://github.com/Microsoft/SDN/blob/master/Diagnostics/Test-Rdma.ps1)

### <a name="run-the-powershell-script"></a>Запустите сценарий PowerShell

При запуске .ps1 Test-Rdma сценарий Windows PowerShell, можно передать значение ifIndex сценария, а также IP-адрес удаленного адаптера в той же виртуальной сети.

Следующий пример команды можно использовать для запуска сценария с ifIndex 14 на сетевом адаптере 192.168.1.5.
    
    C:\TEST\Test-RDMA.PS1 -IfIndex 14 -IsRoCE $true -RemoteIpAddress 192.168.1.5 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
    
    VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\\diskspd.exe
    VERBOSE: The adapter TEST-40G-1 is a physical adapter
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
    

>[!NOTE]
>Если трафик RDMA не удается, в случае RoCE, в частности, см. конфигурацию коммутатора ToR правильных параметров PFC или ETS, должен соответствовать параметров узла. Обратитесь к разделу QoS в этом документе, для значений ссылок.

### <a name="determine-the-ifindex-value-of-your-target-adapter"></a>Определить значение ifIndex адаптера цели

Для обнаружения значение ifIndex адаптера цели можно использовать следующую команду.

    Get-NetIPConfiguration -InterfaceAlias "TEST*" | ft InterfaceAlias,InterfaceIndex,IPv4Address

Ниже приведены примеры результатов выполнения этой команды.

|InterfaceAlias |InterfaceIndex |IPv4-адрес|
|-------------- |-------------- |-----------|
|ТЕСТ-40G-1 |14 |{192.168.1.3}|
|ТЕСТ-40G-2 | 13 |{192.168.2.3}|

Следующий пример команды можно использовать для запуска сценария с ifIndex 13 на сетевом адаптере 192.168.2.5.

    
    C:\TEST\Test-RDMA.PS1 -IfIndex 13 -IsRoCE $true -RemoteIpAddress 192.168.2.5 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
    VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\\diskspd.exe
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
    

## <a name="create-a-hyper-v-virtual-switch"></a>Создание виртуального коммутатора Hyper-V

В этом разделе можно использовать для создания \(vSwitch\) виртуального коммутатора Hyper-V на узлах Hyper-V.

На рисунке ниже показаны узел 1 Hyper-V с виртуальный коммутатор.

![Создание виртуального коммутатора Hyper-V](../../media/Converged-NIC/5-datacenter-create-vswitch.jpg)

### <a name="create-a-vswitch-in-switch-embedded-teaming-set-mode"></a>Создать виртуальный коммутатор в режиме \(SET\) объединение внедренных коммутатора

Следующий пример команды можно использовать для создания НАБОРА коммутатора независимых группу с именем **VMSTEST** на узле 1 Hyper-V. Оба сетевых адаптеров на данном компьютере, тест-40G-1 и TEST-40G-2, добавляются в группы НАБОР с помощью следующей команды.
    
    New-VMSwitch –Name "VMSTEST" –NetAdapterName "TEST-40G-1","TEST-40G-2" -EnableEmbeddedTeaming $true -AllowManagementOS $true
    
Ниже приведены примеры результатов выполнения этой команды.

|Имя |SwitchType |NetAdapterInterfaceDescription|
|---- |---------- |------------------------------|
|VMSTEST |Внешние |Объединенных интерфейса|

Эта команда используется для просмотра физических адаптеров в НАБОРЕ.

    Get-VMSwitchTeam -Name "VMSTEST" | fl

Ниже приведены примеры результатов выполнения этой команды.

**Имя**: VMSTEST **идентификатор**: ad9bb542-dda2-4450-a00e-f96d44bdfbec **NetAdapterInterfaceDescription**: {адаптера Mellanox ConnectX 3 Pro Ethernet, адаптера Mellanox ConnectX 3 Pro Ethernet #2} **TeamingMode**: SwitchIndependent **LoadBalancingAlgorithm**: динамические

#### <a name="display-two-views-of-the-host-vnic"></a>Отображение два представления виртуальную сетевую карту узла

Можно использовать следующие две команды для двух различных представлений сетевой адаптер узла.

Эта команда используется для отображения свойств сетевой адаптер узла.

    Get-NetAdapter

Ниже приведены примеры результатов выполнения этой команды.

| Имя | InterfaceDescription | ifIndex | Состояние | MAC-адрес | Скорость линии | |------|---|---|---|---| | | vEthernet (VMSTEST) | Hyper-V Виртуального сетевого адаптера #2 | 28 | Копирование | E4-1D-2D-07-40-71|80 Гбит/с |

Эта команда используется для отображения дополнительных свойств сетевой адаптер узла.

    Get-VMNetworkAdapter -ManagementOS

Ниже приведены примеры результатов выполнения этой команды.

|Имя |IsManagementOs |VMName |SwitchName |MAC-адрес |Состояние |IPAddresses|
|----|--------------|------|----------|----------|------|-----------|
|
|VMSTEST|Значение true |VMSTEST |E41D2D074071| {ОК}|&nbsp;|

#### <a name="test-the-network-connection-to-the-remote-vlan-101-adapter"></a>Проверьте сетевое подключение удаленного адаптеру 101 виртуальной ЛС

Эта команда используется для проверки подключения к удаленным адаптером 101 виртуальной локальной сети.

`Test-NetConnection 192.168.1.5` 

Ниже приведены примеры результатов выполнения этой команды.

    WARNING: Ping to 192.168.1.5 failed -- Status: DestinationHostUnreachable
    
    ComputerName   : 192.168.1.5
    RemoteAddress  : 192.168.1.5
    InterfaceAlias : vEthernet (CORP-External-Switch)
    SourceAddress  : 10.199.48.170
    PingSucceeded  : False
    PingReplyDetails (RTT) : 0 ms
    
### <a name="reconfigure-vlans"></a>Перенастройте виртуальных локальных сетей

Этот шаг можно использовать для удаления параметра доступа виртуальной ЛС из физический сетевой Адаптер и задать параметр VLANID, с помощью виртуальный коммутатор.

Необходимо удалить параметр доступа виртуальной ЛС, чтобы предотвратить оба auto маркировка исходящего трафика неверный идентификатор виртуальной локальной сети и из фильтрации входящего трафика, которой не соответствует ИД виртуальной ЛС доступа

Чтобы удалить параметр доступа виртуальной локальной сети, можно использовать следующие команды.
    
    Set-NetAdapterAdvancedProperty -Name "Test-40G-1" -RegistryKeyword VlanID -RegistryValue "0"
    Set-NetAdapterAdvancedProperty -Name "Test-40G-2" -RegistryKeyword VlanID -RegistryValue "0"
    

Можно использовать следующие команды для установки VLANID, с помощью Windows PowerShell команды виртуальный коммутатор и просмотреть результаты этого действия.

    
    Set-VMNetworkAdapterVlan -VMNetworkAdapterName "VMSTEST" -VlanId "101" -Access -ManagementOS
    Get-VMNetworkAdapterVlan -ManagementOS -VMNetworkAdapterName "VMSTEST"
    

Ниже приведены примеры результатов выполнения этой команды.

Режим VlanList VMName VMNetworkAdapterName
------ -------------------- ----   --------
       VMSTEST              Access 101     

Чтобы проверить сетевое подключение и просмотреть результаты можно использовать следующую команду.

    Test-NetConnection 192.168.1.5
    
    ComputerName   : 192.168.1.5
    RemoteAddress  : 192.168.1.5
    InterfaceAlias : vEthernet (VMSTEST)
    SourceAddress  : 192.168.1.3
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms
    

Если результаты не аналогично пример результатов и ping завершается сбоем с сообщением «предупреждение: не удалось проверить связь с 192.168.1.5 — состояние: DestinationHostUnreachable,» убедитесь, что «vEthernet (VMSTEST)» имеет правильный IP-адрес, выполнив следующую команду.

    
    Get-NetIPAddress -InterfaceAlias "vEthernet (VMSTEST)"
    

Если IP-адрес не задано, можно использовать следующую команду, чтобы устранить эту проблему и просмотрите результаты действий.

    
    New-NetIPAddress -InterfaceAlias "vEthernet (VMSTEST)" -IPAddress 192.168.1.3 -PrefixLength 24
    
    IPAddress : 192.168.1.3
    InterfaceIndex: 37
    InterfaceAlias: vEthernet (VMSTEST)
    AddressFamily : IPv4
    Type  : Unicast
    PrefixLength  : 24
    PrefixOrigin  : Manual
    SuffixOrigin  : Manual
    AddressState  : Tentative
    ValidLifetime : Infinite ([TimeSpan]::MaxValue)
    PreferredLifetime : Infinite ([TimeSpan]::MaxValue)
    SkipAsSource  : False
    PolicyStore   : ActiveStore
    
#### <a name="rename-the-management-nic"></a>Переименуйте сетевой Адаптер управления

Этот раздел используется для переименования сетевого Адаптера управления и затем использовать отдельные экземпляры виртуальную сетевую карту узла для RDMA.

Позволяет выполнить следующие команды, чтобы переименовать сетевого Адаптера управления и просматривать некоторые свойства сетевого Адаптера.

    Rename-VMNetworkAdapter -ManagementOS -Name “VMSTEST” -NewName “MGT”
    Get-VMNetworkAdapter -ManagementOS

Ниже приведены примеры результатов выполнения этой команды.

|Имя |IsManagementOs |VMName |SwitchName |MAC-адрес |Состояние |IPAddresses
|----|--------------|------|----------|----------|------|-----------|
|
|CORP внешний коммутатор |Значение true |&nbsp;|CORP внешний коммутатор |001B785768AA |{ОК}|&nbsp;|
|КОММУТАТОРУ |Значение true |&nbsp;|VMSTEST |E41D2D074071 |{ОК}|&nbsp;|

Можно выполнить следующую команду, чтобы просмотреть дополнительные свойства сетевого Адаптера.

    Get-NetAdapter

Ниже приведены примеры результатов выполнения этой команды.

|Имя |InterfaceDescription |ifIndex |Состояние |MAC-адрес |Скорость линии|
|----|--------------------|------|----------|---------|------|
|
|vEthernet (Коммутатору) |Hyper-V виртуального сетевого адаптера #2 |28 |Вверх | E4-1D-2D-07-40-71 |80 Гбит/с|

## <a name="test-hyper-v-virtual-switch-rdma"></a>Тестирование виртуального коммутатора Hyper-V RDMA

На рисунке ниже показаны текущее состояние узлов Hyper-V, включая виртуальный коммутатор на узле 1 Hyper-V.

![Тестирование виртуального коммутатора Hyper-V](../../media/Converged-NIC/6-datacenter-test-vswitch-rdma.jpg)

### <a name="set-priority-tagging-on-the-host-vnic-to-complement-the-previous-vlan-settings"></a>Задайте Задание приоритета на сетевой адаптер узла в качестве дополнения предыдущие параметры виртуальной локальной сети

В следующем примере показан можно использовать для настройки приоритета, добавление тегов на сетевой адаптер узла и просмотреть результаты действий.
    
    Set-VMNetworkAdapter -ManagementOS -Name "MGT" -IeeePriorityTag on
    Get-VMNetworkAdapter -ManagementOS -Name "MGT" | fl Name,IeeePriorityTag
    

    Name: MGT
    IeeePriorityTag : On
    
### <a name="create-two-host-vnics-for-rdma"></a>Создайте две виртуальные сетевые карты узла для RDMA

В следующем примере показан можно использовать для создания двух виртуальные сетевые карты узла RDMA и подключите их к VMSTEST виртуальный коммутатор.
    
    Add-VMNetworkAdapter –SwitchName "VMSTEST" –Name SMB1 –ManagementOS
    Add-VMNetworkAdapter –SwitchName "VMSTEST" –Name SMB2 –ManagementOS
    
Следующий пример команды можно использовать для просмотра свойств сетевого Адаптера управления.
    
    Get-VMNetworkAdapter -ManagementOS
    
Ниже приведены примеры результатов выполнения этой команды.

|Имя |IsManagementOs |VMName |SwitchName |MAC-адрес |Состояние |IPAddresses|
|----|--------------|------|----------|----------|------|-----------|
|
|CORP внешний коммутатор |Значение true |CORP внешний коммутатор |001B785768AA|{ОК} |&nbsp;| 
|Коммутатору |Значение true |VMSTEST |E41D2D074071 |{ОК} |&nbsp;|
|SMB1 |Значение true |VMSTEST |00155D30AA00 |{ОК} |&nbsp;|
|SMB2 |Значение true |VMSTEST |00155D30AA01 |{ОК} |&nbsp;|

### <a name="assign-an-ip-address-to-the-smb-host-vnics"></a>Назначьте IP-адрес виртуальные сетевые карты узла SMB

В этом разделе можно использовать для назначения IP addressrd vEthernet виртуальную сетевую карту узла SMB \(SMB1\) и vEthernet \(SMB2\).

Первый тест-40G и физическими адаптерами ТЕСТИРОВАНИЕ 40G 2 все еще виртуальной локальной сети ACCESS 101 или 102 настроен. По этой причине адаптеры пометить трафик - и ping завершается успешно.

Ранее можно настроить оба идентификатора виртуальной ЛС pNIC нулевое значение, а затем значение 101 виртуальной ЛС виртуальный коммутатор VMSTEST. После этого вам по-прежнему смогут связь Удаленный адаптер 101 виртуальной локальной сети с помощью виртуального сетевого адаптера Коммутатору, но в данный момент нет ни одного члена 102 виртуальной локальной сети.

Теперь вы можете использовать следующий пример команды для удаления параметра доступа виртуальной ЛС из физический сетевой Адаптер для предотвращения обоих auto маркировка исходящего трафика неверный идентификатор виртуальной локальной сети и для предотвращения фильтрации входящего трафика, не соответствует ИД виртуальной ЛС доступа

Можно использовать следующий пример команды для достижения этих целей с того новый IP-адрес для интерфейса vEthernet (SMB1) и просмотреть результаты.

    
    New-NetIPAddress -InterfaceAlias "vEthernet (SMB1)" -IPAddress 192.168.2.111 -PrefixLength 24
    
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
    

Следующий пример команды можно использовать для тестирования Удаленный адаптер 102 виртуальной локальной сети и просмотреть результаты.
    
    Test-NetConnection 192.168.2.5 
    
    ComputerName   : 192.168.2.5
    RemoteAddress  : 192.168.2.5
    InterfaceAlias : vEthernet (SMB1)
    SourceAddress  : 192.168.2.111
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms
    
Следующий пример команды можно использовать для добавления нового IP-адрес для интерфейса vEthernet \(SMB2\) и просмотрите результаты.
    
    New-NetIPAddress -InterfaceAlias "vEthernet (SMB2)" -IPAddress 192.168.2.222 -PrefixLength 24 
    
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
    
Необходимо снова проверьте подключение из-за устанавливается соединение.

### <a name="place-the-rdma-host-vnics-on-vlan-102"></a>Поместите виртуальные сетевые карты узла RDMA на 102 виртуальной ЛС

В этом разделе можно использовать для назначения виртуальные сетевые карты узла RDMA 102 виртуальной локальной сети.

Так как сетевой адаптер узла «Коммутатору» находится на 101 виртуальной локальной сети, можно использовать команды в следующем примере для помещения виртуальные сетевые карты узла RDMA имеющийся 102 виртуальной локальной сети и просмотреть результаты действий.

    
    Set-VMNetworkAdapterVlan -VMNetworkAdapterName "SMB1" -VlanId "102" -Access -ManagementOS
    Set-VMNetworkAdapterVlan -VMNetworkAdapterName "SMB2" -VlanId "102" -Access -ManagementOS
    
    Get-VMNetworkAdapterVlan -ManagementOS
    
    VMName VMNetworkAdapterName Mode VlanList
    ------ -------------------- ---- --------
       SMB1 Access   102 
       Mgt  Access   101 
       SMB2 Access   102 
       CORP-External-Switch Untagged
    
### <a name="inspect-the-mapping-of-smb1-and-smb2-to-the-underlying-physical-nics"></a>Проверьте сопоставление SMB1 и SMB2 для базовых физических сетевых адаптеров

Для проверки сопоставление SMB1 и SMB2 для базовых физических сетевых адаптеров в виртуальный коммутатор ЗАДАТЬ команды, можно использовать в этом разделе.  Связь виртуальную сетевую карту узла для физических сетевых адаптеров случайных и подлежат перераспределения во время создания и удаления.

В этом случае можно использовать косвенный механизм для проверки текущего связь.

MAC-адреса SMB1 и SMB2 связаны с члена группы сетевых КАРТ TEST-40G-2. Это не подходит, поскольку первый тест-40G нет связанного виртуального сетевого адаптера узла SMB и не позволит для использования RDMA трафика по этой связи пока сопоставляется виртуальную сетевую карту узла SMB.

Чтобы просмотреть эти сведения можно использовать команды в следующем примере.

    
    Get-NetAdapterVPort (Preferred)
    
    Get-NetAdapterVmqQueue
    
    Name   QueueID MacAddressVlanID Processor VmFriendlyName
    ----   ------- ---------------- --------- --------------
    TEST-40G-1 1   E4-1D-2D-07-40-71 1010:17
    TEST-40G-2 1   00-15-5D-30-AA-00 1020:17
    TEST-40G-2 2   00-15-5D-30-AA-01 1020:17
    
    Get-VMNetworkAdapter -ManagementOS
    
    Name IsManagementOs VMName SwitchName   MacAddress   Status IPAddresses
    ---- -------------- ------ ----------   ----------   ------ -----------
    CORP-External-Switch True  CORP-External-Switch 001B785768AA {Ok}  
    Mgt  True  VMSTEST  E41D2D074071 {Ok}  
    SMB1 True  VMSTEST  00155D30AA00 {Ok}  
    SMB2 True  VMSTEST  00155D30AA01 {Ok}  
    

Обе команды ниже должна возвращать никаких сведений, так как не выполнить сопоставление.
    
    Get-VMNetworkAdapterTeamMapping -ManagementOS -SwitchName VMSTEST -VMNetworkAdapterName SMB1
    Get-VMNetworkAdapterTeamMapping -ManagementOS -SwitchName VMSTEST -VMNetworkAdapterName SMB2
    
Чтобы сопоставить SMB1 и SMB2 для разделения физических членов группы сетевых КАРТ, а также для просмотра результатов действий можно использовать команды в следующем примере.

>[!IMPORTANT]
>Убедитесь, что после завершения этого шага, прежде чем продолжить, или вашей реализации не удастся.
    
    Set-VMNetworkAdapterTeamMapping -ManagementOS -SwitchName VMSTEST -VMNetworkAdapterName "SMB1" -PhysicalNetAdapterName "Test-40G-1"
    Set-VMNetworkAdapterTeamMapping -ManagementOS -SwitchName VMSTEST -VMNetworkAdapterName "SMB2" -PhysicalNetAdapterName "Test-40G-2"
    
    Get-VMNetworkAdapterTeamMapping -ManagementOS -SwitchName VMSTEST
    
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
    
### <a name="confirm-the-mac-associations"></a>Подтверждение MAC сопоставления

В следующем примере показан можно использовать для подтверждения сопоставления MAC, которую вы создали ранее.
    
    Get-NetAdapterVmqQueue
    
    Name   QueueID MacAddressVlanID Processor VmFriendlyName
    ----   ------- ---------------- --------- --------------
    TEST-40G-1 1   E4-1D-2D-07-40-71 1010:17
    TEST-40G-1 2   00-15-5D-30-AA-00 1020:17
    TEST-40G-2 1   00-15-5D-30-AA-01 1020:17
    

Так как обе виртуальные сетевые карты узла находятся в одной подсети с же \(102\) идентификатор виртуальной локальной сети, можно проверить связь с удаленной системы и просмотрите результаты действий.

>[!IMPORTANT]
>Выполните следующие команды на удаленном компьютере.

    
    Test-NetConnection 192.168.2.111
    
    
    ComputerName   : 192.168.2.111
    RemoteAddress  : 192.168.2.111
    InterfaceAlias : Test-40G-2
    SourceAddress  : 192.168.2.5
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms
    
    Test-NetConnection 192.168.2.222
    
    ComputerName   : 192.168.2.222
    RemoteAddress  : 192.168.2.222
    InterfaceAlias : Test-40G-2
    SourceAddress  : 192.168.2.5
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms 
    
        
    Set-VMNetworkAdapter -ManagementOS -Name "SMB1" -IeeePriorityTag on
    Set-VMNetworkAdapter -ManagementOS -Name "SMB2" -IeeePriorityTag on
    Get-VMNetworkAdapter -ManagementOS -Name "SMB*" | fl Name,SwitchName,IeeePriorityTag,Status
    
    Name: SMB1
    SwitchName  : VMSTEST
    IeeePriorityTag : On
    Status  : {Ok}
    
    Name: SMB2
    SwitchName  : VMSTEST
    IeeePriorityTag : On
    Status  : {Ok}
    

    Get-NetAdapterRdma -Name "vEthernet*" | sort Name | ft -AutoSize
    
    Name  InterfaceDescription Enabled
    ----  -------------------- -------
    vEthernet (SMB2)  Hyper-V Virtual Ethernet Adapter #4  False  
    vEthernet (SMB1)  Hyper-V Virtual Ethernet Adapter #3  False  
    vEthernet (MGT)   Hyper-V Virtual Ethernet Adapter #2  False   
    
    
    Enable-NetAdapterRdma -Name "vEthernet (SMB1)"
    Enable-NetAdapterRdma -Name "vEthernet (SMB2)"
    Get-NetAdapterRdma -Name "vEthernet*" | sort Name | fl *
    
    
    Name  InterfaceDescription Enabled
    ----  -------------------- -------
    vEthernet (SMB2)  Hyper-V Virtual Ethernet Adapter #4  True   
    vEthernet (SMB1)  Hyper-V Virtual Ethernet Adapter #3  True  
    vEthernet (MGT)   Hyper-V Virtual Ethernet Adapter #2  False
      

### <a name="validate-rdma-functionality-from-the-remote-system"></a>Проверить функциональные возможности из удаленной системы

В этом разделе можно использовать для проверки функциональные возможности из удаленной системы к локальной системе, который содержит виртуальный коммутатор, тем самым тестирования обоих адаптеров, являющихся членами группы НАБОР виртуальный коммутатор.

Так как обе виртуальные сетевые карты узла \ (SMB1 и SMB2\) назначаются 102 виртуальной локальной сети, можно выбрать адаптер 102 виртуальной локальной сети на удаленном компьютере.  

В данном процессе сетевых КАРТ, тест-40G-2 не RDMA SMB1 (192.168.2.111) и SMB2 (192.168.2.222).

Необязательно: Возможно, нужно для отключения брандмауэра в данной системе.  Подробные сведения политику структуры.

    
    Set-NetFirewallProfile -All -Enabled False
    
    Get-NetAdapterAdvancedProperty -Name "Test-40G-2"
    
    Name  DisplayNameDisplayValue   RegistryKeyword RegistryValue  
    ----  -----------------------   --------------- -------------  
    .
    .
    Test-40G-2VLAN ID102VlanID  {102} 
    
    Get-NetAdapter
    
    Name  InterfaceDescriptionifIndex Status   MacAddress LinkSpeed
    ----  --------------------------- ------   ---------- ---------
    Test-40G-2Mellanox ConnectX-3 Pro Ethernet A...#3   3 Up   E4-1D-2D-07-43-D140 Gbps
    
    
    Get-NetAdapterRdma
    
    Name  InterfaceDescription Enabled
    ----  -------------------- -------
    Test-40G-2Mellanox ConnectX-3 Pro Ethernet Adap... True   
    
    
    C:\TEST\Test-RDMA.PS1 -IfIndex 3 -IsRoCE $true -RemoteIpAddress 192.168.2.111 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
    VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\\diskspd.exe
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
    
    
    C:\TEST\Test-RDMA.PS1 -IfIndex 3 -IsRoCE $true -RemoteIpAddress 192.168.2.222 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
    VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\\diskspd.exe
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
    
### <a name="test-for-rdma-traffic-from-the-local-to-the-remote-computer"></a>Тест RDMA трафика из локальной на удаленный компьютер

В этом разделе вы можете убедиться, что RDMA трафик пересылается с локального компьютера на удаленный компьютер.

В следующем примере показан можно использовать для проверки и просмотра поток трафика.

    
    Get-NetAdapter | ft –AutoSize
    
    Name  InterfaceDescriptionifIndex Status   MacAddress LinkSpeed
    ----  --------------------------- ------   ---------- ---------
    vEthernet (SMB2)  Hyper-V Virtual Ethernet Adapter #4  45 Up   00-15-5D-30-AA-0380 Gbps
    vEthernet (SMB1)  Hyper-V Virtual Ethernet Adapter #3  41 Up   00-15-5D-30-AA-0280 Gbps
    
    
    C:\TEST\Test-RDMA.PS1 -IfIndex 41 -IsRoCE $true -RemoteIpAddress 192.168.2.5 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
    VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\\diskspd.exe
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
    
    
    C:\TEST\Test-RDMA.PS1 -IfIndex 45 -IsRoCE $true -RemoteIpAddress 192.168.2.5 -PathToDiskspd C:\TEST\Diskspd-v2.0.17\amd64fre\
    VERBOSE: Diskspd.exe found at C:\TEST\Diskspd-v2.0.17\amd64fre\\diskspd.exe
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
    
Последняя строка в эти выходные данные» RDMA трафика теста Успех: RDMA трафик, отправленный 192.168.2.5,» показано, успешно настроена схождение выполнено Сетевых адаптера.

## <a name="all-topics-in-this-guide"></a>Все разделы в этом руководстве

Это руководство содержит следующие разделы.

- [Настройка объединенных сетевых Адаптеров с одним сетевым адаптером](cnic-single.md)
- [Настройка сетевой КАРТЫ группы схождением сетевых Адаптеров](cnic-datacenter.md)
- [Физический переключатель конфигурации для сетевого Адаптера схождением](cnic-app-switch-config.md)
- [Устранение неполадок схождение выполнено конфигурации сетевого Адаптера](cnic-app-troubleshoot.md)
