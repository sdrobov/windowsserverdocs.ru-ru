---
title: Управление мост центра обработки данных
description: В этом разделе содержатся инструкции о том, как использовать команды Windows PowerShell для управления, мост для центра обработки данных в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 1575cc7c-62a7-4add-8f78-e5d93effe93f
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: daed746fe798ae253956d0977827d0e205bb8b3e
ms.sourcegitcommit: 21165734a0f37c4cd702c275e85c9e7c42d6b3cb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2019
ms.locfileid: "65034574"
---
# <a name="manage-data-center-bridging-dcb"></a>Управление мост центра обработки данных

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе содержатся инструкции о том, как использовать команды Windows PowerShell для настройки моста для центра обработки данных \(DCB\) на DCB\-совместимый сетевой адаптер, который установлен на компьютере, который работает под управлением Windows Server 2016 или Windows 10.

## <a name="install-dcb-in-windows-server-2016-or-windows-10"></a>Установить мост центра обработки данных в Windows Server 2016 или Windows 10

Сведения о необходимых компонентах для использования и как установить мост центра обработки данных, см. в разделе [установить Data Center Bridging (DCB) в Windows Server 2016 или Windows 10](dcb-install.md).


## <a name="dcb-configurations"></a>Мост центра обработки данных конфигурации 

До выпуска Windows Server 2016, все DCB была применена Конфигурация глобально для всех сетевых адаптеров, которые поддерживаются DCB. 

В Windows Server 2016, можно применить конфигурации DCB Store политики Global или отдельные политики Store\(s\). При применении отдельных политик они переопределяют все параметры глобальной политики.

Пока вы не выполните следующие конфигурации трафика класса, PFC и приложения, назначение приоритета на уровне системы не применяется на сетевых адаптерах.

1. Включить бит готов DCBX значение false

2. Включите DCB в сетевых адаптерах. См. в разделе [включить и отобразить параметры DCB в сетевых адаптеров](#bkmk_enabledcb).

>[!NOTE]
>Если вы хотите настроить мост центра обработки данных от коммутатора через DCBX, см. в разделе [DCBX параметры](#dcb-configuration-on-network-adapters).

Бит готов DCBX описан в спецификации DCB. Если пойти бит на устройстве имеет значение true, устройство будет принимать конфигураций с удаленного устройства через DCBX. Если бит пойти на устройстве имеет значение false, устройство отклонит все попытки конфигурации из удаленных устройств и применить только локальной конфигурации.

Если DCB не установлен в Windows Server 2016 значение бита готов неважен, что касается операционной системы так как в операционной системе не локальные параметры, которые применяются к сетевым адаптерам. После установки DCB готов бита значение по умолчанию имеет значение true. Такой подход позволяет сетевых адаптеров, чтобы сохранить независимо от конфигурации может полученные с их удаленных одноранговых узлов.

Если сетевой адаптер не поддерживает DCBX, он никогда не будет получать конфигурации с удаленного устройства. Он получает конфигурации от операционной системы, но только после DCBX готов бит имеет значение false.

## <a name="set-the-willing-bit"></a>Установить бит готов

Принудительное применение конфигураций операционной системы, класс трафика, PFC и назначения приоритетов приложений на сетевых адаптерах, или просто переопределить конфигурации из удаленных устройств \ — Если существуют какие-либо \ — можно выполнить следующую команду.

>[!NOTE]
>Имена команд DCB Windows PowerShell включать «QoS» вместо «DCB» в строке имени. Это обусловлено тем, QoS и мост центра обработки данных интегрированы в Windows Server 2016 для эффективной работы управления QoS.

    
    Set-NetQosDcbxSetting -Willing $FALSE
    
    Confirm
    Are you sure you want to perform this action?
    Set-NetQosDcbxSetting -Willing $false
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
    

Чтобы отобразить состояние готов бит, можно использовать следующую команду:

    
    Get-NetQosDcbxSetting
    
    Willing PolicySetIfIndex IfAlias
    ------- ---------------- -------
    False   Global  
    

## <a name="dcb-configuration-on-network-adapters"></a>Конфигурация DCB в сетевых адаптеров

Включение DCB на сетевом адаптере позволяет см. в разделе конфигурации, который распространяется от коммутатора к сетевому адаптеру.

DCB конфигурации включают в себя следующие действия.

1.  Настройка параметров мост центра обработки данных на уровне системы, включая:

    1. Управление трафиком-класс
    
    2. Приоритет потока управления (PFC) параметры
    
    В. Назначение приоритетов приложений
    
    Г. Параметры DCBX

2. Настройте мост центра обработки данных на сетевом адаптере.



##  <a name="dcb-traffic-class-management"></a>Класс трафика DCB управления

Ниже приведены примеры команд Windows PowerShell для управления класса трафика.

### <a name="create-a-traffic-class"></a>Создайте класс трафика

Можно использовать **New-NetQosTrafficClass** команду, чтобы создать класс трафика.

    
    New-NetQosTrafficClass -Name SMB -Priority 4 -BandwidthPercentage 30 -Algorithm ETS
    
    Name Algorithm Bandwidth(%) Priority PolicySetIfIndex IfAlias
    ---- --------- ------------ -------- ---------------- -------
    SMB  ETS   30   4Global
      

По умолчанию все значения 802.1p сопоставляются класс трафика по умолчанию, который имеет 100% пропускной способности физической связи. **New-NetQosTrafficClass** команда создает новый класс трафика, для какой любой пакет, который является тег приоритета разметки 802.1 p значение 4 сопоставлен. Алгоритм выбора передачи \(TSA\) ETS и 30% пропускной способности.

Можно создать до 7 новые классы трафика. Включая класс трафика по умолчанию может существовать не более 8 классы трафика в системе. Тем не менее DCB сетевой адаптер с поддержкой могут не поддерживать что многие трафик классы в оборудовании. Если вы создаете дополнительные классы трафика, чем может быть размещено на сетевом адаптере и включите DCB в что сетевой адаптер, драйвер минипорта сообщает об ошибке в операционную систему. Ошибка регистрируется в журнале событий.

Сумма резервирование полосы пропускания для всех классов созданный трафика не может превышать 99% пропускной способности. Класс трафика по умолчанию всегда есть по крайней мере 1% пропускной способности, зарезервированные для себя.

### <a name="display-traffic-classes"></a>Отобразить классы трафика

Можно использовать **Get-NetQosTrafficClass** команду, чтобы просмотреть классы трафика.

    Get-NetQosTrafficClass
    
    NameAlgorithm Bandwidth(%) Priority PolicySetIfIndex IfAlias
    ------------- ------------ -------- ---------------- -------
    [Default]   ETS   70   0-3,5-7  Global
    SMB ETS   30   4Global  
    
### <a name="modify-a-traffic-class"></a>Измените класс трафика

Можно использовать **Set-NetQosTrafficClass** команду, чтобы создать класс трафика. 

    Set-NetQosTrafficClass -Name SMB -BandwidthPercentage 50

Затем можно использовать **Get-NetQosTrafficClass** команду, чтобы просмотреть параметры.

    Get-NetQosTrafficClass
    
    NameAlgorithm Bandwidth(%) Priority PolicySetIfIndex IfAlias
    ------------- ------------ -------- ---------------- -------
    [Default]   ETS   50   0-3,5-7  Global
    SMB ETS   50   4Global   
    

После создания класса трафика, можно изменить его параметры независимо друг от друга. Параметры, которые можно изменять:

1. Распределение пропускной способности \(- BandwidthPercentage\)

2. TSA (\-алгоритма\)

3. Приоритет сопоставления \(-приоритет\)

### <a name="remove-a-traffic-class"></a>Удалить класс трафика

Можно использовать **Remove-NetQosTrafficClass** команду, чтобы удалить класс трафика.

>[!IMPORTANT]
>Не удается удалить класс трафика по умолчанию.


    Remove-NetQosTrafficClass -Name SMB

Затем можно использовать **Get-NetQosTrafficClass** команду, чтобы просмотреть параметры.
    
    Get-NetQosTrafficClass
    
    NameAlgorithm Bandwidth(%) Priority PolicySetIfIndex IfAlias
    ------------- ------------ -------- ---------------- -------
    [Default]   ETS   100  0-7  Global
    

После удаления класс трафика, значение 802.1p сопоставляются меняется, класс трафика к классу трафика по умолчанию. При удалении класса трафика класс распределения трафика по умолчанию возвращаются полосе пропускания, зарезервированный для класса трафика.

## <a name="per-network-interface-policies"></a>— Сетевой интерфейс политики

Все приведенные выше примеры задать глобальные политики. Ниже приведены примеры того, как задать и получить политики каждым сетевым Интерфейсом. 

Поле «PolicySet» изменится с Global на AdapterSpecific. Когда AdapterSpecific политики отображаются, индекс интерфейса \(ifIndex\) и имя интерфейса \(ifAlias\) также отображаются.

```
PS C:\> Get-NetQosTrafficClass

Name        Algorithm Bandwidth(%) Priority         PolicySet        IfIndex IfAlias
----        --------- ------------ --------         ---------        ------- -------
[Default]   ETS       100          0-7              Global


PS C:\> Get-NetQosTrafficClass -InterfaceAlias M1

Name        Algorithm Bandwidth(%) Priority         PolicySet        IfIndex IfAlias
----        --------- ------------ --------         ---------        ------- -------
[Default]   ETS       100          0-7              AdapterSpecific  4       M1


PS C:\> New-NetQosTrafficClass -Name SMBGlobal -BandwidthPercentage 30 -Priority 4 -Algorithm ETS

Name        Algorithm Bandwidth(%) Priority         PolicySet        IfIndex IfAlias
----        --------- ------------ --------         ---------        ------- -------
SMBGlobal   ETS       30           4                Global


PS C:\> New-NetQosTrafficClass -Name SMBforM1 -BandwidthPercentage 30 -Priority 4 -Algorithm ETS -Interfac


Name        Algorithm Bandwidth(%) Priority         PolicySet        IfIndex IfAlias
----        --------- ------------ --------         ---------        ------- -------
SMBforM1    ETS       30           4                AdapterSpecific  4       M1


PS C:\> Get-NetQosTrafficClass

Name        Algorithm Bandwidth(%) Priority         PolicySet        IfIndex IfAlias
----        --------- ------------ --------         ---------        ------- -------
[Default]   ETS       70           0-3,5-7          Global
SMBGlobal   ETS       30           4                Global


PS C:\> Get-NetQosTrafficClass -InterfaceAlias M1

Name        Algorithm Bandwidth(%) Priority         PolicySet        IfIndex IfAlias
----        --------- ------------ --------         ---------        ------- -------
[Default]   ETS       70           0-3,5-7          AdapterSpecific  4       M1
SMBforM1    ETS       30           4                AdapterSpecific  4       M1


```

## <a name="priority-flow-control-settings"></a>Параметры приоритета потока управления:

Ниже приведены примеры команд для настройки приоритета потока управления. Эти параметры также могут быть указаны для отдельных адаптеров.

### <a name="enable-and-display-priority-flow-control-for-global-and-interface-specific-use-cases"></a>Включение и управление потоком отображения приоритета для Global и интерфейс конкретные варианты использования

```
PS C:\> Enable-NetQosFlowControl -Priority 4
PS C:\> Enable-NetQosFlowControl -Priority 3 -InterfaceAlias M1
PS C:\> Get-NetQosFlowControl

Priority   Enabled    PolicySet        IfIndex IfAlias
--------   -------    ---------        ------- -------
0          False      Global
1          False      Global
2          False      Global
3          False      Global
4          True       Global
5          False      Global
6          False      Global
7          False      Global

PS C:\> Get-NetQosFlowControl -InterfaceAlias M1

Priority   Enabled    PolicySet        IfIndex IfAlias
--------   -------    ---------        ------- -------
0          False      AdapterSpecific  4       M1
1          False      AdapterSpecific  4       M1
2          False      AdapterSpecific  4       M1
3          True       AdapterSpecific  4       M1
4          False      AdapterSpecific  4       M1
5          False      AdapterSpecific  4       M1
6          False      AdapterSpecific  4       M1
7          False      AdapterSpecific  4       M1  

```


### <a name="disable-priority-flow-control-global-and-interface-specific"></a>Отключите управление потоком приоритет (глобальные и интерфейса конкретных)

```
PS C:\> Disable-NetQosFlowControl -Priority 4
PS C:\> Disable-NetQosFlowControl -Priority 3 -InterfaceAlias m1
PS C:\> Get-NetQosFlowControl

Priority   Enabled    PolicySet        IfIndex IfAlias
--------   -------    ---------        ------- -------
0          False      Global
1          False      Global
2          False      Global
3          False      Global
4          False      Global
5          False      Global
6          False      Global
7          False      Global


PS C:\> Get-NetQosFlowControl -InterfaceAlias M1

Priority   Enabled    PolicySet        IfIndex IfAlias
--------   -------    ---------        ------- -------
0          False      AdapterSpecific  4       M1
1          False      AdapterSpecific  4       M1
2          False      AdapterSpecific  4       M1
3          False      AdapterSpecific  4       M1
4          False      AdapterSpecific  4       M1
5          False      AdapterSpecific  4       M1
6          False      AdapterSpecific  4       M1
7          False      AdapterSpecific  4       M1  

```

##  <a name="application-priority-assignment"></a>Назначение приоритетов приложений

Ниже приведены примеры назначения приоритетов.

### <a name="create-qos-policy"></a>Создание политики качества обслуживания

```
PS C:\> New-NetQosPolicy -Name "SMB Policy" -PriorityValue8021Action 4

Name           : SMB Policy
Owner          : Group Policy (Machine)
NetworkProfile : All
Precedence     : 127
JobObject      :
PriorityValue  : 4

```

Предыдущая команда создает новую политику для SMB. SMB — это папки "Входящие" Фильтр, извлекающий TCP-порт 445 (зарезервировано для SMB). Если пакет отправляется на TCP-порт 445, оно помечается операционной системой значением 802.1 p из 4 перед передачей пакета на драйвер минипорта сети.

В дополнение к – SMB другие фильтры по умолчанию включают — iSCSI (соответствующий порт TCP 3260), - NFS (сопоставления TCP-порт 2049), - LiveMigration (сопоставления TCP-порт 6600), - FCOE (сопоставление EtherType 0x8906) и NetworkDirect —.

NetworkDirect — это уровень абстракции, которые будут созданы поверх любой реализации RDMA в сетевом адаптере. NetworkDirect — следует указать порт Network Direct.

Помимо фильтров по умолчанию можно классифицировать трафика по имени исполняемого файла приложения (как показано в первом примере) или IP-адреса, порта или протокол (как показано во втором примере):

**С именем исполняемого файла**

```
PS C:\> New-NetQosPolicy -Name background -AppPathNameMatchCondition "C:\Program files (x86)\backup.exe" -PriorityValue8021Action 1

Name           : background
Owner          : Group Policy (Machine)
NetworkProfile : All
Precedence     : 127
AppPathName    : C:\Program files (x86)\backup.exe
JobObject      :
PriorityValue  : 1

```


**По IP-адрес порта или протокол**

```
PS C:\> New-NetQosPolicy -Name "Network Management" -IPDstPrefixMatchCondition 10.240.1.0/24 -IPProtocolMatchCondition both -NetworkProfile all -PriorityValue8021Action 7

Name           : Network Management
Owner          : Group Policy (Machine)
NetworkProfile : All
Precedence     : 127
JobObject      :
IPProtocol     : Both
IPDstPrefix    : 10.240.1.0/24
PriorityValue  : 7

```

### <a name="display-qos-policy"></a>Отображение политики качества обслуживания

```
PS C:\> Get-NetQosPolicy

Name           : background
Owner          : Group Policy (Machine)
NetworkProfile : All
Precedence     : 127
AppPathName    : C:\Program files (x86)\backup.exe
JobObject      :
PriorityValue  : 1

Name           : Network Management
Owner          : Group Policy (Machine)
NetworkProfile : All
Precedence     : 127
JobObject      :
IPProtocol     : Both
IPDstPrefix    : 10.240.1.0/24
PriorityValue  : 7

Name           : SMB Policy
Owner          : Group Policy (Machine)
NetworkProfile : All
Precedence     : 127
JobObject      :
PriorityValue  : 4

```

### <a name="modify-qos-policy"></a>Изменение политики QoS

Можно изменить политики качества обслуживания, как показано ниже.


```
PS C:\> Set-NetQosPolicy -Name "Network Management" -IPSrcPrefixMatchCondition 10.235.2.0/24 -IPProtocolMatchCondition both -PriorityValue8021Action 7
PS C:\> Get-NetQosPolicy

Name           : Network Management
Owner          : Group Policy (Machine)
NetworkProfile : All
Precedence     : 127
JobObject      :
IPProtocol     : Both
IPSrcPrefix    : 10.235.2.0/24
IPDstPrefix    : 10.240.1.0/24
PriorityValue  : 7


```

### <a name="remove-qos-policy"></a>Удалить политику качества обслуживания

```
PS C:\> Remove-NetQosPolicy -Name "Network Management"

Confirm
Are you sure you want to perform this action?
Remove-NetQosPolicy -Name "Network Management" -Store GPO:localhost
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y  

```

## <a name="dcb-configuration-on-network-adapters"></a>Конфигурация DCB в сетевых адаптеров

Конфигурация DCB в сетевых адаптеров не зависит от конфигурации мост центра обработки данных на уровне системы, описанные выше. 

Независимо от того, установлен ли мост центра обработки данных в Windows Server 2016 можно запускать следующие команды. 

Если вы настроите DCB от коммутатора и полагаться на DCBX распространение конфигурации к сетевым адаптерам, можно изучить принимаются и применяются на сетевых адаптерах со стороны операционной системы, после включения DCB в сетевых адаптерах, какие конфигурации.

###  <a name="bkmk_enabledcb"></a>Включить и отобразить параметры DCB в сетевых адаптеров

```
PS C:\> Enable-NetAdapterQos M1
PS C:\> Get-NetAdapterQos

Name                       : M1
Enabled                    : True
Capabilities               :                       Hardware     Current
                                                   --------     -------
                             MacSecBypass        : NotSupported NotSupported
                             DcbxSupport         : None         None
                             NumTCs(Max/ETS/PFC) : 8/8/8        8/8/8

OperationalTrafficClasses  : TC TSA    Bandwidth Priorities
                             -- ---    --------- ----------
                              0 ETS    70%       0-3,5-7
                              1 ETS    30%       4

OperationalFlowControl     : All Priorities Disabled
OperationalClassifications : Protocol  Port/Type Priority
                             --------  --------- --------
                             Default             1


```

### <a name="disable-dcb-on-network-adapters"></a>Отключить DCB в сетевых адаптеров

```
PS C:\> Disable-NetAdapterQos M1
PS C:\> Get-NetAdapterQos M1

Name         : M1
Enabled      : False
Capabilities :                       Hardware     Current
                                     --------     -------
               MacSecBypass        : NotSupported NotSupported
               DcbxSupport         : None         None
               NumTCs(Max/ETS/PFC) : 8/8/8        0/0/0  

```
## <a name="bkmk_wps"></a>Команды Windows PowerShell для DCB

Существуют команды DCB Windows PowerShell для Windows Server 2016 и Windows Server 2012 R2. Все команды можно использовать для Windows Server 2012 R2 в Windows Server 2016.

### <a name="windows-server-2016-windows-powershell-commands-for-dcb"></a>Команды Windows PowerShell Windows Server 2016 для блока управления Каталогами

Windows Server 2016 в следующем разделе приводится описание командлетов Windows PowerShell и синтаксис всех данных мост для центра обработки \(DCB\) качества обслуживания \(QoS\)\-определенные командлеты. Командлеты перечисляются в алфавитном порядке по команде в начале имени командлета.

- [Модуль DcbQoS](https://technet.microsoft.com/itpro/powershell/windows/dcbqos/dcbqos)

### <a name="windows-server-2012-r2-windows-powershell-commands-for-dcb"></a>Команды Windows Server 2012 R2 Windows PowerShell для DCB

Windows Server 2012 R2 в следующем разделе приводится описание командлетов Windows PowerShell и синтаксис всех данных мост для центра обработки \(DCB\) качества обслуживания \(QoS\)\-определенные командлеты. Командлеты перечисляются в алфавитном порядке по команде в начале имени командлета.

- [Центр обработки данных (DCB) обслуживания (QoS) командлеты моста в Windows PowerShell](https://technet.microsoft.com/library/hh967440.aspx)
