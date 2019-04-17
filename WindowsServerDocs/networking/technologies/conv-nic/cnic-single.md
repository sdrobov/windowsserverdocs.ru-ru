---
title: Настройка объединенных сетевых Адаптеров с одним сетевым адаптером
description: Этот раздел содержит инструкции по развертыванию схождение выполнено сетевого Адаптера с одним сетевым адаптером, в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: eed5c184-fa55-43a8-a879-b1610ebc70ca
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: d6663a966026afb301a4bad90a9573d16fc82875
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="converged-nic-configuration-with-a-single-network-adapter"></a>Настройка объединенных сетевых Адаптеров с одним сетевым адаптером

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Инструкции по настройке схождение выполнено сетевого Адаптера с одной сетевой КАРТОЙ на узле Hyper-V в следующих разделах.

Пример конфигурации в этом руководстве описывается два узла Hyper-V, **узла Hyper-V A**, и **B узла Hyper-V**.

## <a name="test-connectivity-between-source-and-destination"></a>Проверьте подключение между исходным и конечным

Этот раздел содержит шаги, необходимые для проверки подключения между исходного и конечного узлов Hyper-V.

На рисунке ниже показаны два узла Hyper-V, **узла Hyper-V A** и **B узла Hyper-V**. 

На обоих серверах установлен один физический сетевой Адаптер (pNIC) установлены и сетевые адаптеры подключены к верхней части стойки \(ToR\) физическому коммутатору. Кроме того серверы находятся в той же подсети, который является 192.168.1.x/24.

![Узлы Hyper-V](../../media/Converged-NIC/1-single-test-conn.jpg)


### <a name="test-nic-connectivity-to-the-hyper-v-virtual-switch"></a>Проверка подключения сетевого Адаптера к виртуальному коммутатору Hyper\-V

Используя этот шаг, можно гарантировать, что физический сетевой Адаптер, для которого позднее создать виртуальный коммутатор Hyper\-V, могут подключаться к конечного узла. 

Этот тест демонстрирует подключения с помощью \(L3\) уровня 3 - или на уровне IP -, а также \(L2\) уровня 2.

Для получения свойств сетевого адаптера, можно использовать следующую команду Windows PowerShell.

    Get-NetAdapter
     
Ниже приведены примеры результатов выполнения этой команды.

|Имя|InterfaceDescription|ifIndex|Состояние|MAC-адрес|Скорость линии|
|-----|--------------------|-------|-----|----------|---------|
|
|M1|Mellanox ConnectX 3 Pro...| 4| Вверх|7C-FE-90-93-8F-A1|40 Гбит/с|

Один из следующих команд можно использовать для получения свойств дополнительного адаптера, включая IP-адрес.

    Get-NetAdapter M1 | fl *

Ниже приведены результаты измененную пример этой команды.
    
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
    

### <a name="ensure-that-source-and-destination-can-communicate"></a>Убедитесь, что исходный и конечный могут обмениваться данными

Этот шаг можно использовать для проверки Двусторонняя связь \ (проверка связи из источника для назначения и обратно на обоих systems\).  В следующем примере **NetConnection теста** использовать команду Windows PowerShell, но если вы предпочитаете, можно использовать **ping** команды. 

>[!NOTE]
>Если вы уверены, что узлы могут обмениваться данными друг с другом, этот шаг можно пропустить.

    Test-NetConnection 192.168.1.5

Ниже приведены примеры результатов выполнения этой команды.

|Параметр|Значение|
|---------|-----|
|
|Имя компьютера|192.168.1.5|
|RemoteAddress|192.168.1.5|
|InterfaceAlias|M1|
|SourceAddress|192.168.1.3|
|PingSucceeded|Значение true|
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

## <a name="configure-vlans-optional"></a>Настройка \(Optional\) виртуальных локальных сетей

Многие конфигурации сети пользоваться виртуальных локальных сетей. Если вы планируете использовать виртуальные локальные сети в вашей сети, необходимо повторить предыдущем тесте настроить виртуальные ЛС. \ (Если вы планируете использовать RoCE для служб RDMA необходимо включить виртуальных локальных сетей. \)

Для этого шага, сетевые адаптеры в **доступа** режим. Однако при создании виртуального коммутатора Hyper-V \(vSwitch\) Далее в этом руководстве свойства виртуальной локальной сети применяются на уровне порта виртуальный коммутатор. 

Поскольку коммутатор может размещаться несколько виртуальных ЛС, она необходима для элемента верхнего \(ToR\) физического коммутатора порт, на подключенном узле настроен магистральный режим.

>[!NOTE]
>Обратитесь к документации коммутатора ToR инструкции о том, как настроить режим магистрали на коммутаторе.

На рисунке ниже показаны два узла Hyper-V, каждый с одним физическим сетевым адаптером, и каждый из которых настроен для связи на 101 виртуальной локальной сети.

![Настройка виртуальных локальных сетей](../../media/Converged-NIC/2-single-configure-vlans.jpg)

### <a name="configure-the-vlan-id"></a>Настройка идентификатор виртуальной ЛС

Этот шаг можно использовать для настройки идентификаторов виртуальной локальной сети для сетевых адаптеров, установить в узлов Hyper-V.

#### <a name="configure-nic-m1"></a>Настройка M1 сетевого Адаптера

С помощью следующих команд настройте идентификатор виртуальной ЛС для первого сетевого Адаптера M1, а затем просмотрев полученную конфигурацию.

>[!IMPORTANT]
>Не запускайте эта команда при подключении к узлу удаленно через этот интерфейс, так как это поэтому приведет к потере доступа к узлу.
    
    Set-NetAdapterAdvancedProperty -Name M1 -RegistryKeyword VlanID -RegistryValue "101"
    Get-NetAdapterAdvancedProperty -Name M1 | Where-Object {$_.RegistryKeyword -eq "VlanID"} 
    
Ниже приведены примеры результатов выполнения этой команды.

|Имя |Отображаемое имя| DisplayValue| RegistryKeyword |RegistryValue|
|----|-----------|------------|---------------|-------------|
|
|M1|ИДЕНТИФИКАТОР ВИРТУАЛЬНОЙ ЛС|101|VlanID|{101}|


Убедитесь, что идентификатор виртуальной ЛС действует зависит от реализации адаптера сети, используя следующую команду для перезапуска сетевого адаптера.

    Restart-NetAdapter -Name "M1"

Можно использовать следующую команду, чтобы убедиться, что состояния сетевого адаптера **вверх** перед продолжением.

    Get-NetAdapter -Name "M1"

Ниже приведены примеры результатов выполнения этой команды.

|Имя|InterfaceDescription|ifIndex| Состояние|MAC-адрес|Скорость линии|
|----|--------------------|-------|------|----------| ---------|
|
|M1|Mellanox ConnectX 3 Pro Ethernet Ada...|4|Вверх|7C-FE-90-93-8F-A1|40 Гбит/с|

Убедитесь, выполните это действие на как локального, так и конечного серверов. Если конечный сервер не настроен с тем же ИД виртуальной ЛС, как локальный сервер, не могут взаимодействовать двух.

### <a name="verify-connectivity"></a>Проверьте сетевое подключение

В этом разделе можно использовать для проверки подключения, после перезагрузки сетевых адаптеров. Вы можете подтвердить подключения после применения тега виртуальной локальной сети к обоим устройствам. В случае сбоя подключения можно проверить коммутатор виртуальной ЛС конфигурации или назначения участие в той же виртуальной сети. 

>[!IMPORTANT]
>После выполнения шагов в предыдущем разделе он может занять несколько секунд для устройства для перезагрузки и становятся доступны в сети.

#### <a name="verify-connectivity-for-nic-test-40g-1"></a>Проверьте сетевое подключение для сетевого Адаптера Test-40G-1

Для проверки подключения для первого сетевого Адаптера, можно выполнить следующую команду.

    Test-NetConnection 192.168.1.5
    
## <a name="configure-data-center-bridging-dcb"></a>Настройка \(DCB\) мост для центра обработки данных

Следующий шаг — Настройка \(QoS\) DCB и качества обслуживания, который необходимо сначала установить Windows Server 2016 функция DCB.

>[!NOTE]
>Все следующие этапы настройки DCB и качество обслуживания следует выполнять на всех серверах, которые предназначены для связи друг с другом.

### <a name="install-data-center-bridging-dcb"></a>Установить мост \(DCB\) центра обработки данных

Этот шаг можно использовать, чтобы установить и включить DCB. 

>[!IMPORTANT]
>- Установка и настройка DCB **необязательно** для сетевых конфигураций, использующих iWarp RDMA служб.
>- Установка и настройка DCB **необходимые** для сетевых конфигураций, использующих RoCE \(any version\) RDMA служб.


Можно использовать следующую команду для установки мост центра обработки данных на каждом из узлов Hyper-V. 

    Install-WindowsFeature Data-Center-Bridging

### <a name="set-the-qos-policies-for-smb-direct"></a>Настроить политики QoS для SMB Direct 

Можно использовать следующую команду для настройки политик QoS для SMB Direct.

>[!IMPORTANT]
>- Этот шаг является необязательным для сетевых конфигураций, использующих iWarp.
>- Этот шаг является обязательным для сетевых конфигураций, использующих RoCE.
>- В примере ниже команды значение «3» является произвольным. Можно использовать любое значение от 1 до 7, пока согласованно использовать то же значение в конфигурации политик QoS.

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

### <a name="for-roce-deployments-turn-on-priority-flow-control-for-smb-traffic"></a>Для RoCE развертываний включите управление потоком приоритета для трафика SMB 

Если вы используете RoCE RDMA служб, можно использовать следующие команды для включения управления потоком для SMB и просмотреть результаты. Приоритет потока управления необходим для RoCE, но не является необходимой при использовании iWarp.

    Enable-NetQosFlowControl -priority 3
    Get-NetQosFlowControl

Ниже приведены примеры результатов из **Get-NetQosFlowControl** команды.

|Приоритет|Включен|PolicySet|IfIndex|IfAlias|
|---------|-----|--------- |-------| -------|
|
|0 |False |Глобальные|&nbsp;|&nbsp;|
|1 |False |Глобальные|&nbsp;|&nbsp;|
|2 |False |Глобальные|&nbsp;|&nbsp;|
|3 |Значение true  |Глобальные|&nbsp;|&nbsp;|
|4 |False |Глобальные|&nbsp;|&nbsp;|
|5 |False |Глобальные|&nbsp;|&nbsp;|
|6 |False |Глобальные|&nbsp;|&nbsp;|
|7 |False |Глобальные|&nbsp;|&nbsp;|

### <a name="enable-qos-for-the-local-and-destination-network-adapters"></a>Включение качества обслуживания для локальной и конечных сетевых адаптеров
На этом этапе вы включите DCB в конкретных сетевых адаптеров.

>[!IMPORTANT]
>-  Этот шаг не требуется для сетевых конфигураций, использующих iWarp.
>-  Этот шаг является обязательным для сетевых конфигураций, использующих RoCE.




#### <a name="enable-qos-for-nic-m1"></a>Включение качества обслуживания для сетевого Адаптера M1

Включение качества обслуживания и просмотрите результаты применения конфигурации можно использовать следующие команды.

    Enable-NetAdapterQos -InterfaceAlias "M1"
    Get-NetAdapterQos -Name "M1"

Ниже приведены примеры результатов выполнения этой команды.

**Имя**: M1 **включен**: True **возможности**:   

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
|0| ETS|70%|0-2,4-7|
|1|ETS|30%|3

**OperationalFlowControl**: приоритет 3 включена **OperationalClassifications**:

|Протокол|Тип порта и|Приоритет|
|--------|---------|--------|
|
|По умолчанию|&nbsp;|0|
|NetDirect| 445|3|

### <a name="reserve-a-percentage-of-the-bandwidth-for-smb-direct-rdma"></a>Зарезервировать процент пропускной способности для SMB Direct \(RDMA\)

Чтобы зарезервировать процент пропускной способности для SMB Direct можно использовать следующую команду.  

В этом примере используется резервирование пропускной способности на 30%. Следует выбирать значение, представляющее, что ожидать, что будет требовать вашего трафика хранилища. Значение **- bandwidthpercentage** параметр должен быть кратным 10%.

    New-NetQosTrafficClass "SMB" -Priority 3 -BandwidthPercentage 30 -Algorithm ETS

Ниже приведены примеры результатов выполнения этой команды.

|Имя|Алгоритм |Bandwidth(%)| Приоритет |PolicySet |IfIndex |IfAlias |
|----|---------| ------------ |--------| ---------|------- |------- |
|
|SMB | ETS     | 30 |3 |Глобальные |&nbsp;|&nbsp;|                                      
 
Можно использовать следующую команду, чтобы просмотреть сведения о резервировании пропускной способности.

    Get-NetQosTrafficClass

Ниже приведены примеры результатов выполнения этой команды.
 
|Имя|Алгоритм |Bandwidth(%)| Приоритет |PolicySet |IfIndex |IfAlias |
|----|---------| ------------ |--------| ---------|------- |------- |
|
|[По умолчанию]|ETS|70 |0-2,4-7| Глобальные|&nbsp;|&nbsp;| 
|SMB      |ETS|30 |3 |Глобальные|&nbsp;|&nbsp;| 

## <a name="remove-debugger-conflict-mellanox-adapter-only"></a>Удалить отладчик конфликт \(Mellanox adapter only\)

При использовании адаптера из Mellanox, необходимо выполнить этот шаг, чтобы настроить отладчик. При использовании адаптера Mellanox присоединенного отладчика по умолчанию блокирует NetQos. Чтобы переопределить отладчик можно использовать следующую команду.

    
    Set-ItemProperty HKLM:"\SYSTEM\CurrentControlSet\Services\NDIS\Parameters" AllowFlowControlUnderDebugger -type DWORD -Value 1 –Force
    

## <a name="test-rdma-native-host"></a>Тест RDMA (основной сервер)

Этот шаг можно использовать, чтобы убедиться, что прежде чем создавать виртуальный коммутатор и переходу на RDMA \(Converged NIC\) структуры настроен правильно.

На рисунке ниже показаны текущее состояние узлов Hyper-V.

![Тест RDMA](../../media/Converged-NIC/4-single-test-rdma.jpg)

Чтобы проверить конфигурацию RDMA, можно выполнить следующую команду.

    Get-NetAdapterRdma

Ниже приведены примеры результатов выполнения этой команды.

|Имя |InterfaceDescription |Включен|
|----|--------------------|-------|
|
|M1| Адаптер Mellanox ConnectX 3 Pro Ethernet |Значение true|

### <a name="download-diskspdexe-and-a-powershell-script"></a>Загрузите DiskSpd.exe и сценарий PowerShell

Чтобы продолжить, необходимо сначала загрузить следующие элементы.

- Загрузите и извлеките программу в C:\TEST\ программу DiskSpd.exe [служебная программа Diskspd: надежного хранилища тестирования инструмента (заменяющих SQLIO)](https://gallery.technet.microsoft.com/DiskSpd-a-robust-storage-6cd2f223)

- Скачайте скрипт powershell Test-RDMA C:\TEST\[https://github.com/Microsoft/SDN/blob/master/Diagnostics/Test-Rdma.ps1](https://github.com/Microsoft/SDN/blob/master/Diagnostics/Test-Rdma.ps1)

### <a name="determine-the-ifindex-value-of-your-target-adapter"></a>Определить значение ifIndex адаптера цели

Для обнаружения значение ifIndex адаптера цели можно использовать следующую команду. Это значение можно использовать в последующих шагах, при выполнении сценария, который вы скачали.

    Get-NetIPConfiguration -InterfaceAlias "M*" | ft InterfaceAlias,InterfaceIndex,IPv4Address

Ниже приведены примеры результатов выполнения этой команды.

|InterfaceAlias |InterfaceIndex |IPv4-адрес|
|-------------- |-------------- |-----------|
|
|M2 |14 |{192.168.1.5}|

### <a name="run-the-powershell-script"></a>Запустите сценарий PowerShell

При запуске .ps1 Test-Rdma сценарий Windows PowerShell, можно передать значение ifIndex сценария, а также IP-адрес удаленного адаптера в той же виртуальной сети.

Следующий пример команды можно использовать для запуска сценария с ifIndex 14 на сетевом адаптере 192.168.1.5.
    
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
    

>[!NOTE]
>Если трафик RDMA не удается, в случае RoCE, в частности, см. конфигурацию коммутатора ToR правильных параметров PFC или ETS, должен соответствовать параметров узла. Обратитесь к разделу QoS в этом документе, для значений ссылок.

## <a name="remove-the-access-vlan-setting"></a>Удалите параметр доступа виртуальной ЛС

В процессе подготовки к созданию коммутатора Hyper-V необходимо удалить параметры виртуальной локальной сети, которые установлены выше.  Можно использовать следующую команду для удаления параметра доступа виртуальной ЛС из физического сетевого адаптера. Это действие запрещает автоматическое добавление тегов исходящего трафика неверный идентификатор виртуальной ЛС сетевого Адаптера и также препятствует фильтрации входящего трафика, который не соответствует ИД виртуальной ЛС доступа

    
    Set-NetAdapterAdvancedProperty -Name M1 -RegistryKeyword VlanID -RegistryValue "0"
    

Следующий пример команды можно использовать, чтобы подтвердить параметр VlanID и просмотреть результаты, которые показывают, что идентификатор виртуальной ЛС значение равно нулю.

    
    Get-NetAdapterAdvancedProperty -name m1 | Where-Object {$_.RegistryKeyword -eq 'VlanID'} 
    


## <a name="create-a-hyper-v-virtual-switch"></a>Создание виртуального коммутатора Hyper-V

В этом разделе можно использовать для создания \(vSwitch\) виртуального коммутатора Hyper-V на узлах Hyper-V.

На рисунке ниже показаны узел 1 Hyper-V с виртуальный коммутатор.

![Создание виртуального коммутатора Hyper-V](../../media/Converged-NIC/5-single-create-vswitch.jpg)


### <a name="create-an-external-hyper-v-virtual-switch"></a>Создание внешнего виртуального коммутатора Hyper-V

В этом разделе можно использовать, чтобы создать внешний виртуальный коммутатор в Hyper-V на узле Hyper-V A.

Следующий пример команды можно использовать для создания коммутатор с именем VMSTEST.

>[!NOTE]
>Параметр **AllowManagementOS** в следующая команда создает виртуальную сетевую карту узла, который наследует MAC-адрес и IP-адрес физический сетевой адаптер.

    New-VMSwitch -Name VMSTEST -NetAdapterName "M1" -AllowManagementOS $true

Ниже приведены примеры результатов выполнения этой команды.

|Имя |SwitchType |NetAdapterInterfaceDescription|
|---- |---------- |------------------------------|
|VMSTEST |Внешние |Адаптер Mellanox ConnectX 3 Pro Ethernet|

Можно использовать следующую команду для просмотра свойств сетевого адаптера.

    Get-NetAdapter | ft -AutoSize

Ниже приведены примеры результатов выполнения этой команды.

|Имя |InterfaceDescription | ifIndex |Состояние |MAC-адрес |Скорость линии|
|---- |-------------------- |-------| ------|----------|---------|
|
|vEthernet \(VMSTEST\) |Hyper-V виртуального сетевого адаптера #2|27 |Вверх |E4-1D-2D-07-40-71 |40 Гбит/с|


Вы можете управлять виртуальную сетевую карту узла двумя способами. Один из методов — **NetAdapter** представление, в котором работает основе «vEthernet \(VMSTEST\)» имя.

Это также **VMNetworkAdapter** представление, которое удаляет префикс «vEthernet» и просто использует имя vmswitch.

**VMNetworkAdapter** отображаются некоторых свойств сетевого адаптера, которые не отображаются с **NetAdapter** команды.

Можно использовать следующую команду для просмотра результатов **VMNetworkAdapter** метод.

    Get-VMNetworkAdapter –ManagementOS | ft -AutoSize

Ниже приведены примеры результатов выполнения этой команды.

|Имя |IsManagementOs |VMName |SwitchName |MAC-адрес |Состояние |IPAddresses|
|----|-------------- |------ |----------|----------|------ |-----------|
|
|CORP внешний коммутатор |Значение true |CORP внешний коммутатор| 001B785768AA |{ОК} |&nbsp;|
|VMSTEST |Значение true |VMSTEST | E41D2D074071| {ОК} | &nbsp;| 

### <a name="test-the-connection"></a>Тестирование подключения

Следующий пример команды можно использовать для проверки подключения и просмотреть результаты.
    
    Test-NetConnection 192.168.1.5

    ComputerName   : 192.168.1.5
    RemoteAddress  : 192.168.1.5
    InterfaceAlias : vEthernet (CORP-External-Switch)
    SourceAddress  : 192.168.1.3
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms
    
В следующем примере показан можно использовать для назначения и просмотр параметров виртуальной ЛС сетевого адаптера.
    
    Set-VMNetworkAdapterVlan -VMNetworkAdapterName "VMSTEST" -VlanId "101" -Access -ManagementOS
    Get-VMNetworkAdapterVlan -ManagementOS -VMNetworkAdapterName "VMSTEST"
    

|VMName |VMNetworkAdapterName |Режим |VlanList|
|------ |-------------------- |---- |--------|
|
|&nbsp;|VMSTEST |Доступ |101     
 
### <a name="test-the-connection"></a>Тестирование подключения

Вспомним, что изменения может занять несколько секунд до завершения вы можете успешно проверить связь с другой адаптер.

Следующий пример команды можно использовать для проверки подключения и просмотреть результаты.
    
    Test-NetConnection 192.168.1.5
     
    ComputerName   : 192.168.1.5
    RemoteAddress  : 192.168.1.5
    InterfaceAlias : vEthernet (VMSTEST)
    SourceAddress  : 192.168.1.3
    PingSucceeded  : True
    PingReplyDetails (RTT) : 0 ms
    

## <a name="test-hyper-v-virtual-switch-rdma-mode-2"></a>Тестирование виртуального коммутатора Hyper-V RDMA (режим 2)

На рисунке ниже показаны текущее состояние узлов Hyper-V, включая виртуальный коммутатор на узле 1 Hyper-V.

![Тестирование виртуального коммутатора Hyper-V](../../media/Converged-NIC/6-single-test-vswitch-rdma.jpg)


### <a name="set-priority-tagging-on-the-host-vnic"></a>Установка приоритета, добавление тегов на сетевой адаптер узла

В следующем примере показан можно использовать для настройки приоритета, добавление тегов на сетевой адаптер узла и просмотреть результаты действий.
    
    Set-VMNetworkAdapter -ManagementOS -Name "VMSTEST" -IeeePriorityTag on
    Get-VMNetworkAdapter -ManagementOS -Name "VMSTEST" | fl Name,IeeePriorityTag
    
    Name: VMSTEST
    IeeePriorityTag : On
    
Следующий пример команды можно использовать для просмотра сетевого адаптера RDMA сведения. В списке результатов при параметр **включено** имеет значение **False**, это означает, что RDMA не включена.
    
    Get-NetAdapterRdma
    
|Имя |InterfaceDescription |Включен |
|---- |-------------------- |-------|
|
|vEthernet \(VMSTEST\)| Hyper-V виртуального сетевого адаптера #2|False|

### <a name="enable-rdma-on-the-host-vnic"></a>Включите RDMA виртуальную сетевую карту узла

Чтобы просмотреть свойства сетевого адаптера, включить RDMA для адаптера и затем сетевого адаптера RDMA сведения можно использовать команды в следующем примере.
    
    Get-NetAdapter
    
|Имя |InterfaceDescription |ifIndex |Состояние |MAC-адрес |Скорость линии|
|----|--------------------|-------|------|----------|---------|
|
|vEthernet (VMSTEST)|Hyper-V виртуального сетевого адаптера #2|27|Вверх|E4-1D-2D-07-40-71|40 Гбит/с|

    Enable-NetAdapterRdma -Name "vEthernet (VMSTEST)"
    Get-NetAdapterRdma -Name "vEthernet (VMSTEST)"

В следующие результаты при параметр **включено** имеет значение **True**, это означает, что включен RDMA.

|Имя |InterfaceDescription |Включен |
|---- |-------------------- |-------|
|
|vEthernet \(VMSTEST\)| Hyper-V виртуального сетевого адаптера #2|Значение true|


    
    Get-NetAdapter 
    

|Имя |InterfaceDescription |ifIndex |Состояние |MAC-адрес |Скорость линии|
|----|--------------------|-------|------|----------|---------|
|
|vEthernet (VMSTEST)|Hyper-V виртуального сетевого адаптера #2|27|Вверх|E4-1D-2D-07-40-71|40 Гбит/с|

### <a name="perform-rdma-traffic-test-by-using-the-script"></a>Протестируйте трафика RDMA, с помощью сценария

Чтобы запустить сценарий, который вы скачали и просмотреть результаты можно использовать следующую команду.
    
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
    
Последняя строка в эти выходные данные» RDMA трафика теста Успех: RDMA трафик, отправленный 192.168.1.5,» показано, успешно настроена схождение выполнено Сетевых адаптера.

## <a name="all-topics-in-this-guide"></a>Все разделы в этом руководстве

Это руководство содержит следующие разделы.

- [Настройка объединенных сетевых Адаптеров с одним сетевым адаптером](cnic-single.md)
- [Настройка сетевой КАРТЫ группы схождением сетевых Адаптеров](cnic-datacenter.md)
- [Физический переключатель конфигурации для сетевого Адаптера схождением](cnic-app-switch-config.md)
- [Устранение неполадок схождение выполнено конфигурации сетевого Адаптера](cnic-app-troubleshoot.md)
