---
title: Ошибки служба работоспособности
ms.prod: windows-server
manager: eldenc
ms.author: cosdar
ms.technology: storage-health-service
ms.topic: article
ms.assetid: ''
author: cosmosdarwin
ms.date: 10/05/2017
ms.openlocfilehash: 11af69d1c6f32205b87ad4605edebacb59b0b710
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71369708"
---
# <a name="health-service-faults"></a>Ошибки служба работоспособности
> Относится к: Windows Server 2019, Windows Server 2016

## <a name="what-are-faults"></a>Что такое ошибки

Служба работоспособности постоянно отслеживает кластер Локальные дисковые пространства для обнаружения проблем и создания ошибок. Один новый командлет отображает текущие ошибки, что позволяет легко проверить работоспособность развертывания, не изучая каждую сущность или функцию в свою очередь. Все сообщения об ошибках дают точную информацию, которую легко понять и по которой можно выполнить конкретные действия.  

Каждая ошибка содержит пять важных полей:  

-   severity
-   Описание проблемы
-   Рекомендуемые действия для устранения проблемы
-   Сведения для идентификации сущности, вызвавшей сбой
-   Физическое расположение (если применимо)

Вот пример распространенной ошибки:  

```
Severity: MINOR                                         
Reason: Connectivity has been lost to the physical disk.                           
Recommendation: Check that the physical disk is working and properly connected.    
Part: Manufacturer Contoso, Model XYZ9000, Serial 123456789                        
Location: Seattle DC, Rack B07, Node 4, Slot 11
```

 >[!NOTE]
 > Физическое расположение основывается на конфигурации домена сбоя. Дополнительные сведения о доменах сбоя см. [в статье домены сбоя в Windows Server 2016](fault-domains.md). Если эти сведения отсутствуют, поле размещения менее полезно — например, в нем может быть указан только номер слота.  

## <a name="root-cause-analysis"></a>Анализ основных причин

Служба работоспособности может оценить потенциальную причину возникновения проблемных сущностей, чтобы определить и объединить ошибки, которые являются последствиями одной и той же базовой проблемы. Выявление таких цепочек влияния позволяет снизить объемы выводимой информации. Например, если сервер не работает, то ожидается, что он не будет подключен к серверу. Поэтому для основной причины будет выдана только одна ошибка — в данном случае это сервер.  

## <a name="usage-in-powershell"></a>Использование в PowerShell

Чтобы просмотреть текущие ошибки в PowerShell, выполните следующий командлет:

```PowerShell
Get-StorageSubSystem Cluster* | Debug-StorageSubSystem  
```

Это возвращает все ошибки, которые влияют на общий кластер Локальные дисковые пространства. Чаще всего эти ошибки связаны с оборудованием или конфигурацией. Если ошибок нет, этот командлет возвратит Nothing.  

>[!NOTE]
> В непроизводственной среде вы можете поэкспериментировать с этой функцией, выполнив самостоятельное срабатывание ошибок. Например, можно удалить один физический диск или завершить работу одного узла. После появления ошибки повторно вставьте физический диск или перезапустите узел, после чего ошибка исчезнет снова.

Кроме того, можно просматривать ошибки, влияющие только на определенные тома или общие файловые ресурсы, с помощью следующих командлетов:  

```PowerShell
Get-Volume -FileSystemLabel <Label> | Debug-Volume  

Get-FileShare -Name <Name> | Debug-FileShare  
```

Это возвращает все ошибки, затрагивающие только конкретный том или общую папку. Чаще всего эти ошибки связаны с планированием емкости, устойчивостью данных или такими функциями, как качество обслуживания хранилища или Реплика хранилища. 

## <a name="usage-in-net-and-c"></a>Использование в .NET иC#

### <a name="connect"></a>Подключение

Чтобы запросить служба работоспособности, необходимо будет установить **CimSession** с кластером. Для этого вам потребуются некоторые вещи, которые доступны только в полной среде .NET. Это означает, что вы не можете сделать это непосредственно из веб-приложения или с мобильных приложений. Эти примеры кода будут использовать C @ no__t-0, самый простой выбор для этого уровня доступа к данным.

``` 
...
using System.Security;
using Microsoft.Management.Infrastructure;

public CimSession Connect(string Domain = "...", string Computer = "...", string Username = "...", string Password = "...")
{
    SecureString PasswordSecureString = new SecureString();
    foreach (char c in Password)
    {
        PasswordSecureString.AppendChar(c);
    }

    CimCredential Credentials = new CimCredential(
        PasswordAuthenticationMechanism.Default, Domain, Username, PasswordSecureString);
    WSManSessionOptions SessionOptions = new WSManSessionOptions();
    SessionOptions.AddDestinationCredentials(Credentials);
    Session = CimSession.Create(Computer, SessionOptions);
    return Session;
}
```

Указанное имя пользователя должно быть локальным администратором конечного компьютера.

Рекомендуется создавать **SecureString** с паролем непосредственно из входных данных пользователя в режиме реального времени, поэтому пароль никогда не хранится в памяти в виде открытого текста. Это помогает устранить различные проблемы безопасности. Но на практике его создание, как и раньше, является общим для целей создания прототипов.

### <a name="discover-objects"></a>Обнаружение объектов

После установки **CimSession** можно запросить инструментарий управления Windows (WMI) (WMI) в кластере.

Прежде чем можно будет получить ошибки или метрики, необходимо получить экземпляры нескольких соответствующих объектов. Сначала **MSFT @ no__t-1StorageSubSystem** , который представляет локальные дисковые пространства в кластере. Используя это, вы можете получить все данные о **MSFT @ no__t-1StorageNode** в кластере, а также в каждом **MSFT @ no__t-3Volume**, томах данных. Наконец, вам потребуются **MSFT @ no__t-1StorageHealth**, а также сам служба работоспособности.

```
CimInstance Cluster;
List<CimInstance> Nodes;
List<CimInstance> Volumes;
CimInstance HealthService;

public void DiscoverObjects(CimSession Session)
{
    // Get MSFT_StorageSubSystem for Storage Spaces Direct
    Cluster = Session.QueryInstances(@"root\microsoft\windows\storage", "WQL", "SELECT * FROM MSFT_StorageSubSystem")
        .First(Instance => (Instance.CimInstanceProperties["FriendlyName"].Value.ToString()).Contains("Cluster"));

    // Get MSFT_StorageNode for each cluster node
    Nodes = Session.EnumerateAssociatedInstances(Cluster.CimSystemProperties.Namespace,
        Cluster, "MSFT_StorageSubSystemToStorageNode", null, "StorageSubSystem", "StorageNode").ToList();

    // Get MSFT_Volumes for each data volume
    Volumes = Session.EnumerateAssociatedInstances(Cluster.CimSystemProperties.Namespace,
        Cluster, "MSFT_StorageSubSystemToVolume", null, "StorageSubSystem", "Volume").ToList();

    // Get MSFT_StorageHealth itself
    HealthService = Session.EnumerateAssociatedInstances(Cluster.CimSystemProperties.Namespace,
        Cluster, "MSFT_StorageSubSystemToStorageHealth", null, "StorageSubSystem", "StorageHealth").First();
}
```

Это те же объекты, которые вы получаете в PowerShell с помощью таких командлетов, как **Get-сторажесубсистем**, **Get-стораженоде**и **Get-Volume**.

Вы можете получить доступ ко всем тем же свойствам, описанным в статье [классы API управления хранением](https://msdn.microsoft.com/library/windows/desktop/hh830612(v=vs.85).aspx).

```
...
using System.Diagnostics;

foreach (CimInstance Node in Nodes)
{
    // For illustration, write each node's Name to the console. You could also write State (up/down), or anything else!
    Debug.WriteLine("Discovered Node " + Node.CimInstanceProperties["Name"].Value.ToString());
}
```

### <a name="query-faults"></a>Ошибки запросов

Вызовите метод **диагностики** , чтобы получить все текущие ошибки, выделенные для целевого объекта **CimInstance**, который является кластером или любым томом.

Полный список ошибок, доступных в каждой области в Windows Server 2016, приведен ниже.

```       
public void GetFaults(CimSession Session, CimInstance Target)
{
    // Set Parameters (None)
    CimMethodParametersCollection FaultsParams = new CimMethodParametersCollection();
    // Invoke API
    CimMethodResult Result = Session.InvokeMethod(Target, "Diagnose", FaultsParams);
    IEnumerable<CimInstance> DiagnoseResults = (IEnumerable<CimInstance>)Result.OutParameters["DiagnoseResults"].Value;
    // Unpack
    if (DiagnoseResults != null)
    {
        foreach (CimInstance DiagnoseResult in DiagnoseResults)
        {
            // TODO: Whatever you want!
        }
    }
}
```

### <a name="optional-myfault-class"></a>Дополнительно Класс Мифаулт

Может иметь смысл создать и сохранить собственное представление ошибок. Например, этот класс **мифаулт** хранит несколько ключевых свойств ошибок, в том числе **фаултид**, которые можно использовать позже для связывания уведомлений об обновлениях или удаления, а также для дедупликации в случае, если одна и та же ошибка обнаруживается несколько раз. по какой бы то ни было причине.

```       
public class MyFault {
    public String FaultId { get; set; }
    public String Reason { get; set; }
    public String Severity { get; set; }
    public String Description { get; set; }
    public String Location { get; set; }

    // Constructor
    public MyFault(CimInstance DiagnoseResult)
    {
        CimKeyedCollection<CimProperty> Properties = DiagnoseResult.CimInstanceProperties;
        FaultId     = Properties["FaultId"                  ].Value.ToString();
        Reason      = Properties["Reason"                   ].Value.ToString();
        Severity    = Properties["PerceivedSeverity"        ].Value.ToString();
        Description = Properties["FaultingObjectDescription"].Value.ToString();
        Location    = Properties["FaultingObjectLocation"   ].Value.ToString();
    }
}
```

```
List<MyFault> Faults = new List<MyFault>;

foreach (CimInstance DiagnoseResult in DiagnoseResults)
{
    Faults.Add(new Fault(DiagnoseResult));
}
```

Полный список свойств в каждой ошибке (**диагносересулт**) приведен ниже.

### <a name="fault-events"></a>События сбоя

При создании, удалении или обновлении ошибок служба работоспособности создает события WMI. Это важно для обеспечения синхронизации состояния приложения без частого опроса и может помочь в определении времени отправки оповещений по электронной почте, например. Чтобы подписываться на эти события, этот пример кода снова использует шаблон разработки наблюдателя.

Сначала Подпишитесь на события **MSFT @ no__t-1StorageFaultEvent** .

```      
public void ListenForFaultEvents()
{
    IObservable<CimSubscriptionResult> Events = Session.SubscribeAsync(
        @"root\microsoft\windows\storage", "WQL", "SELECT * FROM MSFT_StorageFaultEvent");
    // Subscribe the Observer
    FaultsObserver<CimSubscriptionResult> Observer = new FaultsObserver<CimSubscriptionResult>(this);
    IDisposable Disposeable = Events.Subscribe(Observer);
}   
```

Затем реализуйте наблюдателя, метод **OnNext ()** которого будет вызываться при создании нового события.

Каждое событие содержит значение **ChangeType** , указывающее, создается ли ошибка, удаляется или обновляется, и соответствующий **фаултид**.

Кроме того, они содержат все свойства ошибки.

```
class FaultsObserver : IObserver
{
    public void OnNext(T Event)
    {
        // Cast
        CimSubscriptionResult SubscriptionResult = Event as CimSubscriptionResult;

        if (SubscriptionResult != null)
        {
            // Unpack            
            CimKeyedCollection<CimProperty> Properties = SubscriptionResult.Instance.CimInstanceProperties;
            String ChangeType = Properties["ChangeType"].Value.ToString();
            String FaultId = Properties["FaultId"].Value.ToString();

            // Create
            if (ChangeType == "0")
            {
                Fault MyNewFault = new MyFault(SubscriptionResult.Instance);
                // TODO: Whatever you want!
            }
            // Remove
            if (ChangeType == "1")
            {
                // TODO: Use FaultId to find and delete whatever representation you have...
            }
            // Update
            if (ChangeType == "2")
            {
                // TODO: Use FaultId to find and modify whatever representation you have...
            }
        }
    }
    public void OnError(Exception e)
    {
        // Handle Exceptions
    }
    public void OnCompleted()
    {
        // Nothing
    }
}
```

### <a name="understand-fault-lifecycle"></a>Общие сведения о жизненном цикле сбоев

Ошибки не должны помечаться как "видимые" или разрешенные пользователем. Они создаются, когда служба работоспособности обнаруживает проблему и удаляются автоматически и только в том случае, если служба работоспособности не может наблюдать за проблемой. Как правило, это отражает, что проблема исправлена.

Однако в некоторых случаях ошибки могут быть повторно обнаружены служба работоспособности (например, после отработки отказа или из-за периодического подключения и т. д.). По этой причине может иметь смысл сохранить собственное представление ошибок, чтобы можно было легко отменить дублирование. Это особенно важно, если вы отправляете оповещения по электронной почте или эквивалентные.

### <a name="properties-of-faults"></a>Свойства ошибок

В этой таблице представлено несколько ключевых свойств объекта fault. Чтобы получить полную схему, проверьте класс **MSFT @ no__t-1StorageDiagnoseResult** в *сторажевми. mof*.

| **Свойства**              | **Пример**                                                     |
|---------------------------|-----------------------------------------------------------------|
| фаултид                   | {12345-12345-12345-12345-12345}                                 |
| фаулттипе                 | Microsoft. Health. Фаулттипе. том. Capacity                      |
| `Reason`                    | "На томе заканчивается свободное место".                 |
| перцеиведсеверити         | 5                                                               |
| фаултингобжектдескриптион | Contoso XYZ9000 С.Н. 123456789                                  |
| фаултингобжектлокатион    | Стойка A06, RU 25, слот 11                                        |
| рекоммендедактионс        | {"Расширение тома", "Перенос рабочих нагрузок в другие тома".}   |

**Фаултид** Уникально в пределах области одного кластера.

**Перцеиведсеверити** Перцеиведсеверити = {4, 5, 6} = {"информационное", "предупреждение" и "ошибка"} или эквивалентные цвета, такие как синий, желтый и красный.

**Фаултингобжектдескриптион** Сведения о части оборудования, обычно пустые для программных объектов.

**Фаултингобжектлокатион** Сведения о расположении оборудования, обычно пустые для программных объектов.

**Рекоммендедактионс** Список рекомендуемых действий, которые являются независимыми и не имеют определенного порядка. Сегодня этот список часто имеет длину 1.

## <a name="properties-of-fault-events"></a>Свойства событий сбоя

В этой таблице представлено несколько ключевых свойств события сбоя. Чтобы получить полную схему, проверьте класс **MSFT @ no__t-1StorageFaultEvent** в *сторажевми. mof*.

Обратите внимание на **ChangeType**, который указывает, создается ли ошибка, удаляется или обновляется, и **фаултид**. Событие также содержит все свойства затронутой ошибки.

| **Свойства**              | **Пример**                                                     |
|---------------------------|-----------------------------------------------------------------|
| ChangeType                | 0                                                               |
| фаултид                   | {12345-12345-12345-12345-12345}                                 |
| фаулттипе                 | Microsoft. Health. Фаулттипе. том. Capacity                      |
| `Reason`                    | "На томе заканчивается свободное место".                 |
| перцеиведсеверити         | 5                                                               |
| фаултингобжектдескриптион | Contoso XYZ9000 С.Н. 123456789                                  |
| фаултингобжектлокатион    | Стойка A06, RU 25, слот 11                                        |
| рекоммендедактионс        | {"Расширение тома", "Перенос рабочих нагрузок в другие тома".}   |

**ChangeType** ChangeType = {0, 1, 2} = {"Create", "Remove", "Update"}.

## <a name="coverage"></a>Покрытие

В Windows Server 2016 служба работоспособности обеспечивает следующее покрытие ошибки:  

### <a name="physicaldisk-8"></a>**Физический диск (8)**

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskfailedmedia"></a>Фаулттипе: Microsoft. Health. Фаулттипе. физический. Фаиледмедиа
* Серьезность: Предупреждение
* Причина: *"Сбой физического диска".*
* Рекоммендедактион: *«Замените физический диск».*

#### <a name="faulttype-microsofthealthfaulttypephysicaldisklostcommunication"></a>Фаулттипе: Microsoft. Health. Фаулттипе. физический. Лосткоммуникатион
* Серьезность: Предупреждение
* Причина: *"Потеряна связь с физическим диском".*
* Рекоммендедактион: *«Убедитесь, что физический диск работает и правильно подключен».*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunresponsive"></a>Фаулттипе: Microsoft. Health. Фаулттипе. физический. не отвечает
* Серьезность: Предупреждение
* Причина: *"Физический диск ведет к небыстрой отклику".*
* Рекоммендедактион: *«Замените физический диск».*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskpredictivefailure"></a>Фаулттипе: Microsoft. Health. Фаулттипе. физический. Предиктивефаилуре
* Серьезность: Предупреждение
* Причина: *«В ближайшее время прогнозируется сбой физического диска».*
* Рекоммендедактион: *«Замените физический диск».*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunsupportedhardware"></a>Фаулттипе: Microsoft. Health. Фаулттипе. физический. Унсуппортедхардваре
* Серьезность: Предупреждение
* Причина: *"Физический диск помещается в карантин, так как он не поддерживается поставщиком решений".*
* Рекоммендедактион: *"Замените физический диск поддерживаемым оборудованием".*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunsupportedfirmware"></a>Фаулттипе: Microsoft. Health. Фаулттипе. физический. Унсуппортедфирмваре
* Серьезность: Предупреждение
* Причина: *"Физический диск находится в карантине, так как его версия встроенного по не поддерживается поставщиком решения".*
* Рекоммендедактион: *"Обновите встроенное по на физическом диске до целевой версии".*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunrecognizedmetadata"></a>Фаулттипе: Microsoft. Health. Фаулттипе. физический. Унрекогнизедметадата
* Серьезность: Предупреждение
* Причина: *"Физический диск содержит нераспознанные метаданные".*
* Рекоммендедактион: *"Этот диск может содержать данные из неизвестного пула носителей. Сначала убедитесь, что на этом диске нет полезных данных, а затем сбросьте диск ".*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskfailedfirmwareupdate"></a>Фаулттипе: Microsoft. Health. Фаулттипе. физический. Фаиледфирмвареупдате
* Серьезность: Предупреждение
* Причина: *«Сбой попытки обновления встроенного по на физическом диске».*
* Рекоммендедактион: *"Попробуйте использовать другой двоичный файл встроенного по".*

### <a name="virtual-disk-2"></a>**Виртуальный диск (2)**

#### <a name="faulttype-microsofthealthfaulttypevirtualdisksneedsrepair"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Виртуалдискс. Нидсрепаир
* Серьезность: Сведения
* Причина: *"некоторые данные на этом томе не являются полностью устойчивыми. Он остается доступным».*
* Рекоммендедактион: *"Восстановление устойчивости данных".*

#### <a name="faulttype-microsofthealthfaulttypevirtualdisksdetached"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Виртуалдискс. Detach
* Серьезность: Критическое
* Причина: *"том недоступен. Некоторые данные могут быть потеряны. "*
* Рекоммендедактион: *"Проверьте физическое и/или сетевое подключение всех запоминающих устройств. Возможно, потребуется выполнить восстановление из резервной копии ".*

### <a name="pool-capacity-1"></a>**Емкость пула (1)**

#### <a name="faulttype-microsofthealthfaulttypestoragepoolinsufficientreservecapacityfault"></a>Фаулттипе: Microsoft. Health. Фаулттипе. StoragePool. ИнсуффиЦиентресервекапаЦитифаулт
* Серьезность: Предупреждение
* Причина: *"пул носителей не имеет минимально рекомендуемой резервной емкости. Это может ограничить возможность восстановить устойчивость данных в случае сбоя диска. "*
* Рекоммендедактион: *"добавьте дополнительную емкость в пул носителей или освободите емкость. Минимальное рекомендуемое резервное значение зависит от развертывания, но имеет емкость примерно 2 диска.*

### <a name="volume-capacity-2sup1sup"></a>**Емкость тома (2)** <sup>1</sup>

#### <a name="faulttype-microsofthealthfaulttypevolumecapacity"></a>Фаулттипе: Microsoft. Health. Фаулттипе. том. Capacity
* Серьезность: Предупреждение
* Причина: *"На томе заканчивается свободное место".*
* Рекоммендедактион: *"Разверните том или перенесите рабочие нагрузки на другие тома".*

#### <a name="faulttype-microsofthealthfaulttypevolumecapacity"></a>Фаулттипе: Microsoft. Health. Фаулттипе. том. Capacity
* Серьезность: Критическое
* Причина: *"На томе заканчивается свободное место".*
* Рекоммендедактион: *"Разверните том или перенесите рабочие нагрузки на другие тома".*

### <a name="server-3"></a>**Сервер (3)**

#### <a name="faulttype-microsofthealthfaulttypeserverdown"></a>Фаулттипе: Microsoft. исправность. Фаулттипе. Server. Down
* Серьезность: Критическое
* Причина: *«Сервер недоступен».*
* Рекоммендедактион: *"Запустить или заменить сервер".*

#### <a name="faulttype-microsofthealthfaulttypeserverisolated"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Server. изоляция
* Серьезность: Критическое
* Причина: *"Сервер изолирован от кластера из-за проблем с подключением".*
* Рекоммендедактион: *"Если изоляция сохраняется, проверьте сети или перенесите рабочие нагрузки на другие узлы".*

#### <a name="faulttype-microsofthealthfaulttypeserverquarantined"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Server. карантин
* Серьезность: Критическое
* Причина: *"Сервер помещен в карантин кластера из-за повторяющихся сбоев".*
* Рекоммендедактион: *"Замените сервер или исправьте сеть".*

### <a name="cluster-1"></a>**Кластер (1)**

#### <a name="faulttype-microsofthealthfaulttypeclusterquorumwitnesserror"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Клустеркуорумвитнесс. Error
* Серьезность: Критическое
* Причина: *«В кластере не удается перейти на другой сервер».*
* Рекоммендедактион: *"Проверьте ресурс следящего сервера и при необходимости перезапустите его. Запуск или замена серверов с ошибками».*

### <a name="network-adapterinterface-4"></a>**Сетевой адаптер или интерфейс (4)**

#### <a name="faulttype-microsofthealthfaulttypenetworkadapterdisconnected"></a>Фаулттипе: Microsoft. исправность. Фаулттипе. сетевого адаптера. DISCONNECTED
* Серьезность: Предупреждение
* Причина: *"Сетевой интерфейс был отключен".*
* Рекоммендедактион: *"Повторное подключение сетевого кабеля".*

#### <a name="faulttype-microsofthealthfaulttypenetworkinterfacemissing"></a>Фаулттипе: Microsoft. Health. Фаулттипе. NetworkInterface. Missing
* Серьезность: Предупреждение
* Причина: *"На сервере {Server} отсутствуют сетевые адаптеры, подключенные к сети кластера {кластерная сеть}".*
* Рекоммендедактион: *"Подключение сервера к отсутствующей сети кластера".*

#### <a name="faulttype-microsofthealthfaulttypenetworkadapterhardware"></a>Фаулттипе: Microsoft. Health. Фаулттипе. сетевого адаптера. оборудование
* Серьезность: Предупреждение
* Причина: *«В сетевом интерфейсе произошла ошибка оборудования».*
* Рекоммендедактион: *"Замените адаптер сетевого интерфейса".*

#### <a name="faulttype-microsofthealthfaulttypenetworkadapterdisabled"></a>Фаулттипе: Microsoft. Health. Фаулттипе. сетевого адаптера. Disabled
* Серьезность: Предупреждение
* Причина: *"Сетевой интерфейс {сетевой интерфейс} не включен и не используется".*
* Рекоммендедактион: *"Включить сетевой интерфейс".*

### <a name="enclosure-6"></a>**Корпус (6)**

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurelostcommunication"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Сторажеенклосуре. Лосткоммуникатион
* Серьезность: Предупреждение
* Причина: *"Связь потеряна в корпусе хранилища".*
* Рекоммендедактион: *"Запуск или замена корпуса хранилища".*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurefanerror"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Сторажеенклосуре. Фанеррор
* Серьезность: Предупреждение
* Причина: *"Сбой вентилятора в позиции {положением} в корпусе хранилища".*
* Рекоммендедактион: *"Замените вентилятор в корпусе хранилища".*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurecurrentsensorerror"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Сторажеенклосуре. Куррентсенсореррор
* Серьезность: Предупреждение
* Причина: *"Сбой текущего датчика в позиции {положением} в корпусе хранилища".*
* Рекоммендедактион: *"Замените текущий датчик в корпусе хранилища".*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurevoltagesensorerror"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Сторажеенклосуре. Волтажесенсореррор
* Серьезность: Предупреждение
* Причина: *"Сбой датчика напряжения в позиции {положением} в корпусе хранилища".*
* Рекоммендедактион: *"Замените датчик напряжения в корпусе хранилища".*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosureiocontrollererror"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Сторажеенклосуре. Иоконтроллереррор
* Серьезность: Предупреждение
* Причина: *"Сбой контроллера ввода-вывода в позиции {положением} в корпусе хранилища".*
* Рекоммендедактион: *"Замените контроллер ввода-вывода в корпусе хранилища".*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosuretemperaturesensorerror"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Сторажеенклосуре. Температуресенсореррор
* Серьезность: Предупреждение
* Причина: *"Сбой датчика температуры в позиции {положением} в корпусе хранилища".*
* Рекоммендедактион: *"Замените датчик температуры в корпусе хранилища".*

### <a name="firmware-rollout-3"></a>**Развертывание встроенного по (3)**

#### <a name="faulttype-microsofthealthfaulttypefaultdomainfailedmaintenancemode"></a>Фаулттипе: Microsoft. Health. Фаулттипе. FaultDomain. Фаиледмаинтенанцемоде
* Серьезность: Предупреждение
* Причина: *"В настоящее время невозможно выполнить ход выполнения развертывания встроенного по".*
* Рекоммендедактион: *"Проверьте работоспособность всех дисковых пространств и убедитесь, что в режиме обслуживания нет домена сбоя".*

#### <a name="faulttype-microsofthealthfaulttypefaultdomainfirmwareverifyversionfaile"></a>Фаулттипе: Microsoft. Health. Фаулттипе. FaultDomain. Фирмвареверифиверсионфаиле
* Серьезность: Предупреждение
* Причина: *"Развертывание встроенного по было отменено из-за нечитаемости или непредвиденных сведений о версии встроенного по после применения обновления встроенного по".*
* Рекоммендедактион: *"Перезапустить развертывание встроенного по после устранения проблемы встроенного по".*

#### <a name="faulttype-microsofthealthfaulttypefaultdomaintoomanyfailedupdates"></a>Фаулттипе: Microsoft. Health. Фаулттипе. FaultDomain. Туманифаиледупдатес
* Серьезность: Предупреждение
* Причина: *"Развертывание встроенного по отменено, так как слишком много физических дисков не удалось выполнить попытку обновления встроенного по".*
* Рекоммендедактион: *"Перезапустить развертывание встроенного по после устранения проблемы встроенного по".*

### <a name="storage-qos-3sup2sup"></a>**Качество обслуживания хранилища (3)** <sup>2</sup>

#### <a name="faulttype-microsofthealthfaulttypestorqosinsufficientthroughput"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Сторкос. ИнсуффиЦиентсраугхпут
* Серьезность: Предупреждение
* Причина: *"Пропускная способность хранилища недостаточно для удовлетворения резервов".*
* Рекоммендедактион: *"Настройка политик качества обслуживания хранилища".*

#### <a name="faulttype-microsofthealthfaulttypestorqoslostcommunication"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Сторкос. Лосткоммуникатион
* Серьезность: Предупреждение
* Причина: *"Диспетчер политики качества обслуживания хранилища потерял связь с Томом".*
* Рекоммендедактион: *"Перезагрузите узлы {Nodes}".*

#### <a name="faulttype-microsofthealthfaulttypestorqosmisconfiguredflow"></a>Фаулттипе: Microsoft. Health. Фаулттипе. Сторкос. Мисконфигуредфлов
* Серьезность: Предупреждение
* Причина: *"Один или несколько потребителей хранилища (обычно виртуальные машины) используют несуществующую политику с идентификатором {ID}."*
* Рекоммендедактион: *"Повторное создание любых отсутствующих политик качества обслуживания для хранилища".*

<sup>1</sup> указывает, что том достиг уровня 80% Full (незначительный уровень серьезности) или 90% Full (основной уровень серьезности).  
<sup>2</sup> означает, что некоторые виртуальные жесткие диски на томе не соответствуют минимальным операциям ввода-вывода в секунду для более 10% (минор), 30% (основной) или 50% (критическое значение) скользящего 24-часового окна.  

>[!NOTE]
> Работоспособность компонентов дисковой полки (вентиляторы, источников питания, датчики и т. п.) определяется по данным SCSI Enclosure Services (SES). Если поставщик не предоставляет эту информацию, служба работоспособности ее не отображает.  

## <a name="see-also"></a>См. также

- [служба работоспособности в Windows Server 2016](health-service-overview.md)
