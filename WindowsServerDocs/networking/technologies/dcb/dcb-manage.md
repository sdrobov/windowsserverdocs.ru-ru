---
title: Управление центром обработки данных (DCB) мост
description: В этом разделе содержатся инструкции о том, как использовать команды Windows PowerShell для управления мост для центра обработки данных в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 1575cc7c-62a7-4add-8f78-e5d93effe93f
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: dbe9e5e4af2ddd834b5b8f38e9ffd1b403e92793
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="manage-data-center-bridging-dcb"></a>Управление центром обработки данных (DCB) мост

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе содержатся инструкции о том, как использовать команды Windows PowerShell для настройки \(DCB\) мост для центра обработки данных на совместимых DCB\ сетевым адаптером, который устанавливается на компьютере под управлением Windows Server 2016 или Windows 10.

## <a name="install-dcb-in-windows-server-2016-or-windows-10"></a>Установить мост центра обработки данных в Windows Server 2016 или Windows 10

Сведения на необходимые условия для использования и способ установки мост центра обработки данных см. в разделе [установить центр мост данных (DCB) в Windows Server 2016 или Windows 10](dcb-install.md).


## <a name="dcb-configurations"></a>Мост центра обработки данных конфигурации 

До выхода Windows Server 2016 для всех сетевых адаптеров, которые поддерживаются DCB все конфигурации DCB был применяются ко всем компонентам. 

В Windows Server 2016 можно применить DCB конфигурации в хранилище политики Global или Store\(s\) отдельные политики. При применении отдельные политики переопределяют все параметры глобальной политики.

Конфигурации трафика класса, PFC и приложения, назначения приоритетов на уровне системы не будет применяться на сетевых адаптерах, пока необходимо следующее.

1. Включить бит намерение DCBX значение false

2. Включите DCB в сетевых адаптеров. В разделе [включить и отобразить параметры DCB в сетевых адаптеров](#bkmk_enabledcb).

>[!NOTE]
>Если вы хотите настроить DCB от коммутатора через DCBX, см. раздел [DCBX параметры](#BKMK_DCBX_Settings)

Бит намерение DCBX описано в спецификации DCB. Если намерение бит на устройстве имеет значение true, устройство готов принимать конфигураций с удаленного устройства через DCBX. Если намерение бит на устройстве устанавливается значение false, это устройство отклонять все попытки конфигурации из удаленных устройств и применять только локальной конфигурации.

Если DCB не установлен в Windows Server 2016 значение намерение бита не имеет значения, как операционная система имеет дело, так как операционная система имеет локальные параметры не применяются к сетевым адаптерам. После установки мост центра обработки данных, значение по умолчанию намерение бита — true. Такой подход позволяет сетевых адаптеров, чтобы сохранить все конфигурации может получено из их удаленных одноранговых узлов.

Если сетевой адаптер не поддерживает DCBX, он не получит конфигурации с удаленным устройством. Он получает конфигурации из операционной системы, но только после DCBX намерение бит имеет значение false.

## <a name="set-the-willing-bit"></a>Установить намерение бит

Для применения конфигурации операционных систем класса трафика traffic class, PFC и назначения приоритетов приложения на сетевых адаптерах, или просто переопределить конфигурации из удаленных устройств \ — Если какой-либо \ — можно выполнить следующую команду.

>[!NOTE]
>Имена команд DCB Windows PowerShell включать «QoS» вместо «DCB» в строку имени. Это вызвано QoS и мост центра обработки данных интегрированы в Windows Server 2016 для обеспечения удобного управления QoS.

    
    Set-NetQosDcbxSetting -Willing $FALSE
    
    Confirm
    Are you sure you want to perform this action?
    Set-NetQosDcbxSetting -Willing $false
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
    

Чтобы отобразить состояние намерение бит, можно использовать следующую команду:

    
    Get-NetQosDcbxSetting
    
    Willing PolicySetIfIndex IfAlias
    ------- ---------------- -------
    False   Global  
    

## <a name="dcb-configuration-on-network-adapters"></a>DCB конфигурации сетевых адаптеров

Включение DCB на сетевом адаптере позволяет просмотреть конфигурацию распространяются от коммутатора к сетевому адаптеру.

DCB конфигурации включают следующие действия.

1.  Настройка параметров мост центра обработки данных на уровне системы, в том числе:

    . Управление трафиком класса
    
    б. Приоритет потока управления (PFC) параметры
    
    c. Назначение приоритетов приложений
    
    d. Параметры DCBX

2. Настройте DCB на сетевом адаптере.



##  <a name="dcb-traffic-class-management"></a>DCB класса трафика управления

Ниже приведены примеры команд Windows PowerShell для управления класса трафика Traffic Class.

### <a name="create-a-traffic-class"></a>Создайте класс трафика

Можно использовать **New-NetQosTrafficClass** команду, чтобы создать класс трафика.

    
    New-NetQosTrafficClass -Name SMB -Priority 4 -BandwidthPercentage 30 -Algorithm ETS
    
    Name Algorithm Bandwidth(%) Priority PolicySetIfIndex IfAlias
    ---- --------- ------------ -------- ---------------- -------
    SMB  ETS   30   4Global
      

По умолчанию для всех значений 802.1p сопоставляются с класс трафика по умолчанию, который имеет 100% от пропускной способности физической связи. **New-NetQosTrafficClass** команда создает новый класс трафика, к какой все пакеты, которые связаны с приоритета 802.1p значение 4 сопоставляется. Алгоритм выбора передачи \(TSA\) имеет ETS и 30% полосы пропускания.

Можно создать до 7 новые классы трафика. Включая класс трафика по умолчанию может существовать не более 8 классы трафика в системе. Тем не менее адаптер с поддержкой DCB может не поддерживать что многие трафика классы в оборудовании. Если создать дополнительные классы трафика, чем может быть размещено на сетевом адаптере, включите DCB в что сетевой адаптер драйвер мини-порта сообщает об ошибке в операционную систему. Данная ошибка регистрируется в журнале событий.

Сумма резервирования пропускной способности для всех классов созданный трафик не может превышать 99% от пропускной способности. Класс трафика по умолчанию всегда имеет по крайней мере 1% от пропускной способности, зарезервированные для себя.

### <a name="display-traffic-classes"></a>Отобразить классы трафика

Можно использовать **Get-NetQosTrafficClass** команду для просмотра классами трафика.

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
    

После создания класса трафика, можно изменять ее параметры независимо друг от друга. Ниже перечислены параметры, которые можно изменить.

1. \(-BandwidthPercentage\) распределение пропускной способности

2. TSA (\-Algorithm\)

3. Сопоставление \(-Priority\) приоритет

### <a name="remove-a-traffic-class"></a>Удаление класса трафика

Можно использовать **Remove-NetQosTrafficClass** команды для удаления класса трафика.

>[!IMPORTANT]
>Класс трафика по умолчанию удалить невозможно.


    Remove-NetQosTrafficClass -Name SMB

Затем можно использовать **Get-NetQosTrafficClass** команду, чтобы просмотреть параметры.
    
    Get-NetQosTrafficClass
    
    NameAlgorithm Bandwidth(%) Priority PolicySetIfIndex IfAlias
    ------------- ------------ -------- ---------------- -------
    [Default]   ETS   100  0-7  Global
    

После удаления класс трафика значением 802.1p сопоставить класса трафика traffic class, повторно сопоставляется для класса трафика по умолчанию. При удалении класса трафика класса распределения трафика по умолчанию возвращаются любой пропускной способности, который зарезервирован для класса трафика.

## <a name="per-network-interface-policies"></a>Интерфейс политик на сети

Все из приведенных выше примерах присвоить глобальных политик. Ниже приведены примеры того, как установить и get-NIC политик. 

В поле «PolicySet» переходит с Global AdapterSpecific. При AdapterSpecific политик, отображаются \(ifIndex\) индекс интерфейса и имя интерфейса \(ifAlias\) также отображается.

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

Ниже приведены примеры команды для настройки приоритета потока управления. Эти параметры также можно указать для отдельных адаптеров.

### <a name="enable-and-display-priority-flow-control-for-global-and-interface-specific-use-cases"></a>Включение и управление потоком отображения приоритет для глобальные и определенного интерфейса варианты использования

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

### <a name="create-qos-policy"></a>Создание политики QoS

```
PS C:\> New-NetQosPolicy -Name "SMB Policy" -PriorityValue8021Action 4

Name           : SMB Policy
Owner          : Group Policy (Machine)
NetworkProfile : All
Precedence     : 127
JobObject      :
PriorityValue  : 4

```

Предыдущая команда создается новая политика для SMB. SMB — это фильтр папки "Входящие", которое соответствует TCP-порт 445 (зарезервировано для SMB). Если пакет отправляется TCP-порт 445, он будет помечено операционной системой с значением 802.1 p 4 перед передачей пакета на сетевого драйвера мини-порта.

Помимо — SMB другие фильтры по умолчанию содержит — iSCSI (соответствующие TCP-порта 3260), - NFS (соответствующий порт TCP 2049), - LiveMigration (соответствующий порт 6600 TCP), - FCOE (сопоставление EtherType 0x8906) и NetworkDirect —.

NetworkDirect является уровень абстракции, который мы создадим поверх любой реализации RDMA в сетевом адаптере. NetworkDirect — должен быть указан знак Network Direct порт.

Помимо фильтры по умолчанию можно классифицировать трафика с именем исполняемого файла приложения (как в первом примере ниже) или IP-адреса, порта или протокола (как показано во втором примере):

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

### <a name="display-qos-policy"></a>Отображение политики QoS

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

Можно изменить политики QoS, как показано ниже.


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

### <a name="remove-qos-policy"></a>Удаление политики QoS

```
PS C:\> Remove-NetQosPolicy -Name "Network Management"

Confirm
Are you sure you want to perform this action?
Remove-NetQosPolicy -Name "Network Management" -Store GPO:localhost
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y  

```

## <a name="dcb-configuration-on-network-adapters"></a>DCB конфигурации сетевых адаптеров

DCB конфигурации сетевых адаптеров не зависит от конфигурации мост центра обработки данных на уровне системы, описанные выше. 

Независимо от того, установлен ли DCB в Windows Server 2016 можно всегда выполните следующие команды. 

Если вы настроите DCB от коммутатора и полагаться на DCBX для распространения конфигурации для сетевых адаптеров, можно проверить, какие конфигурации поступают и применяется на сетевые адаптеры со стороны операционной системы после включите DCB в сетевых адаптеров.

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

Существует команды DCB Windows PowerShell для Windows Server 2016 и Windows Server 2012 R2. Все команды можно использовать для Windows Server 2012 R2 в Windows Server 2016.

### <a name="windows-server-2016-windows-powershell-commands-for-dcb"></a>Команды Windows PowerShell Windows Server 2016 для DCB

Windows Server 2016 в следующем разделе приводится описание командлетов Windows PowerShell и синтаксис всех \(DCB\) мост для центра обработки данных качества обслуживания \ командлеты \-specific (QoS\). Он командлеты перечисляются в алфавитном порядке по команде в начале имени командлета.

- [Модуль DcbQoS](https://technet.microsoft.com/itpro/powershell/windows/dcbqos/dcbqos)

### <a name="windows-server-2012-r2-windows-powershell-commands-for-dcb"></a>Команды Windows Server 2012 R2 Windows PowerShell для DCB

Windows Server 2012 R2 в следующем разделе приводится описание командлетов Windows PowerShell и синтаксис всех \(DCB\) мост для центра обработки данных качества обслуживания \ командлеты \-specific (QoS\). Он командлеты перечисляются в алфавитном порядке по команде в начале имени командлета.

- [Качество обслуживания (QoS) командлетов в Windows PowerShell (DCB) мост центра обработки данных](https://technet.microsoft.com/library/hh967440.aspx)
