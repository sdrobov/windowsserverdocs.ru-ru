---
title: Ошибки службы работоспособности
ms.prod: windows-server-threshold
manager: eldenc
ms.author: cosdar
ms.technology: storage-health-service
ms.topic: article
ms.assetid: ''
author: cosmosdarwin
ms.date: 10/05/2017
ms.openlocfilehash: 31a38eacea3af3c0a288d61a77a24b4fa45a1932
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59843375"
---
# <a name="health-service-faults"></a>Ошибки службы работоспособности
> Область применения: Windows Server 2016

## <a name="what-are-faults"></a>Что такое ошибок

Служба работоспособности постоянно наблюдает за дисковыми пространствами кластера для выявления проблем и создания «ошибки». Новый командлет отображает все актуальные ошибки, что позволяет легко проверить работоспособность развертывания, не изучая отдельно каждую сущность и функцию. Все сообщения об ошибках дают точную информацию, которую легко понять и по которой можно выполнить конкретные действия.  

Каждое такое сообщение содержит пять важных полей:  

-   Severity
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
 > Физическое расположение основывается на конфигурации домена сбоя. Дополнительные сведения о доменах сбоя см. в разделе [доменов сбоя в Windows Server 2016](fault-domains.md). Если эти сведения отсутствуют, поле размещения менее полезно — например, в нем может быть указан только номер слота.  

## <a name="root-cause-analysis"></a>Анализ основных причин

Служба работоспособности способна оценивать потенциальных причинно-следственных связей между сущностями, чтобы объединить следственные из одной основной причиной с ошибками. Выявление таких цепочек влияния позволяет снизить объемы выводимой информации. Например если сервер не работает, ожидается, чем все диски на сервере также будет без подключения к. Таким образом только одна ошибка возникает для основной причины - в этом случае сервер.  

## <a name="usage-in-powershell"></a>Использование в PowerShell

Чтобы просмотреть все актуальные ошибки в PowerShell, выполните этот командлет:

```PowerShell
Get-StorageSubSystem Cluster* | Debug-StorageSubSystem  
```

Эта команда возвращает все сообщения об ошибках, которые влияют на весь кластер дисковых пространств. Чаще всего это ошибки, связанные с оборудованием или конфигурацией. Если актуальных ошибок нет, этот командлет возвращает nothing.  

>[!NOTE]
> В тестовой среде и на свой страх и риск вы можете поэкспериментировать с помощью этой функции условия для ошибок самостоятельно, — например, удалив один физический диск или завершить работу узла. После появления ошибки, повторно вставьте физического диска или перезагрузка узла и ошибка исчезнет еще раз.

Можно также просмотреть сбои, затрагивающие работу только определенных томов или общих папок с помощью следующих командлетов:  

```PowerShell
Get-Volume -FileSystemLabel <Label> | Debug-Volume  

Get-FileShare -Name <Name> | Debug-FileShare  
```

Эта команда возвращает все сообщения об ошибках, которые влияют на только конкретного тома или файловый ресурс. Чаще всего эти ошибки связаны с планирования загрузки, Устойчивость данных или функции, такие как хранилища качества обслуживания или репликой хранилища. 

## <a name="usage-in-net-and-c"></a>Использование в .NET иC#

### <a name="connect"></a>Подключение

Для запроса к службе работоспособности, необходимо установить **CimSession** с кластером. Для этого необходимо помнить, что доступны только в полной .NET, то есть вы легко это сделать непосредственно из веб-роли или мобильного приложения. В этих примерах кода будет использоваться C\#наиболее простым выбор для этого уровня доступа к данным.

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

Указанное имя пользователя должно быть локальным администратором целевого компьютера.

Рекомендуется создавать пароль **SecureString** непосредственно из введенных пользователем данных в в режиме реального времени, поэтому пароль никогда не хранится в памяти в виде открытого текста. Это помогает снизить разнообразные проблемы безопасности. Но на практике, создать его самостоятельно выше характерен для целей создания прототипов.

### <a name="discover-objects"></a>Обнаружение объектов

С помощью **CimSession** установлено, вы можете запросить инструментария управления Windows (WMI) в кластере.

Перед получением сбоев или метрики, необходимо будет получить экземпляры соответствующих объектов. Во-первых, **MSFT\_StorageSubSystem** представляет дисковыми пространствами, в кластере. Используя который, можно получить каждый **MSFT\_StorageNode** в кластере и каждый **MSFT\_тома**, объем данных. Наконец, вам потребуется **MSFT\_StorageHealth**, самого слишком службе работоспособности.

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

Это те же объекты, вы можете получить в PowerShell с помощью командлетов, например **Get-StorageSubSystem**, **Get-StorageNode**, и **Get-Volume**.

Доступны те же свойства, описанные по адресу [классы API управления хранилищами](https://msdn.microsoft.com/en-us/library/windows/desktop/hh830612(v=vs.85).aspx).

```
...
using System.Diagnostics;

foreach (CimInstance Node in Nodes)
{
    // For illustration, write each node's Name to the console. You could also write State (up/down), or anything else!
    Debug.WriteLine("Discovered Node " + Node.CimInstanceProperties["Name"].Value.ToString());
}
```

### <a name="query-faults"></a>Сбоев запросов

Вызвать **Диагностика** получить все актуальные ошибки, с заданной областью в целевой объект **CimInstance**, что быть кластера или любой другой том.

Полный список ошибок в каждой области видимости в Windows Server 2016 описана ниже.

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

### <a name="optional-myfault-class"></a>Дополнительно Класс MyFault

Целесообразно создать и сохранить собственные представление ошибок. К примеру, это **MyFault** класс хранит нескольким ключевым группам ошибок, включая **FaultId**, который можно использовать позже связать обновления или удаления уведомлений, или для нее в случае, если то же ошибка обнаруживается несколько раз, для какой-либо причине.

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

Полный список свойств в каждой ошибке (**DiagnoseResult**) описана ниже.

### <a name="fault-events"></a>События ошибок

При ошибок создается, удалены или обновлены, служба работоспособности создает события WMI. Они необходимы для синхронизации состояния вашего приложения без частых опроса и хорошо, как определить время отправки оповещений по электронной почте, например. Чтобы подписаться на эти события, этот пример кода использует шаблон разработки наблюдателя еще раз.

Во-первых, Подпишитесь на **MSFT\_StorageFaultEvent** события.

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

Затем реализация объекта Observer, **OnNext()** метод будет вызываться всякий раз, когда создается новое событие.

Каждое событие содержит **ChangeType** , указывающее ошибку, создается ли, удаленных или обновленных и соответствующие **FaultId**.

Кроме того они содержат все свойства самой ошибки.

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

### <a name="understand-fault-lifecycle"></a>Понимание жизненного цикла сбоя

Сбои не предназначены для помечен как «просмотр» или разрешенный этим пользователем. Они создаются, когда служба работоспособности наблюдает за проблемы, и они будут автоматически удалены, и только в том случае, если служба работоспособности больше не можете наблюдать за проблему. Как правило здесь указано, что проблема была устранена.

Однако в некоторых случаях сбои могут быть повторно обнаружены службой работоспособности (например, после отработки отказа, или из-за прерыванием связи и т. д.). По этой причине может смысл для сохранения представления ошибок, поэтому можно легко выполнить дедупликацию. Это особенно важно при отправке уведомлений по электронной почте или наличие эквивалентных прав.

### <a name="properties-of-faults"></a>Свойства ошибок

Эта таблица предоставляет несколько ключевых свойств объекта сбоя. Полную схему, проверять **MSFT\_StorageDiagnoseResult** в класс *storagewmi.mof*.

| **Свойство**              | **Пример**                                                     |
|---------------------------|-----------------------------------------------------------------|
| FaultId                   | {12345-12345-12345-12345-12345}                                 |
| FaultType                 | Microsoft.Health.FaultType.Volume.Capacity                      |
| Причина                    | «Томе заканчивается доступное пространство.»                 |
| PerceivedSeverity         | 5                                                               |
| FaultingObjectDescription | Contoso XYZ9000 S.N. 123456789                                  |
| FaultingObjectLocation    | Установка в стойку A06, RU 25, слоте 11                                        |
| RecommendedActions        | {«Расширение тома.», «Перенос рабочих нагрузок на другие тома.»}   |

**FaultId** уникальный в пределах одного кластера.

**PerceivedSeverity** PerceivedSeverity = {4, 5, 6} = {«Информационный», «Warning» и «Error»}, или эквивалентные цвета, например blue, желтым и красным цветом.

**FaultingObjectDescription** часть сведения для оборудования, обычно пустым для программных объектов.

**FaultingObjectLocation** сведения о расположении для оборудования, обычно пусто для программных объектов.

**RecommendedActions** список рекомендуемых действий, которые не зависят от и в произвольном порядке. В настоящее время этот список часто является длиной в 1 знак.

## <a name="properties-of-fault-events"></a>Свойства событий сбоя

Эта таблица предоставляет несколько ключевых свойств события сбоя. Полную схему, проверять **MSFT\_StorageFaultEvent** в класс *storagewmi.mof*.

Примечание **ChangeType**, который показывает ли ошибка создается, удаленных или обновленных и **FaultId**. Событие также содержит все свойства затронутых ошибки.

| **Свойство**              | **Пример**                                                     |
|---------------------------|-----------------------------------------------------------------|
| ChangeType                | 0                                                               |
| FaultId                   | {12345-12345-12345-12345-12345}                                 |
| FaultType                 | Microsoft.Health.FaultType.Volume.Capacity                      |
| Причина                    | «Томе заканчивается доступное пространство.»                 |
| PerceivedSeverity         | 5                                                               |
| FaultingObjectDescription | Contoso XYZ9000 S.N. 123456789                                  |
| FaultingObjectLocation    | Установка в стойку A06, RU 25, слоте 11                                        |
| RecommendedActions        | {«Расширение тома.», «Перенос рабочих нагрузок на другие тома.»}   |

**ChangeType** ChangeType = { 0, 1, 2 } = { "Create", "Remove", "Update" }.

## <a name="coverage"></a>Покрытие

В Windows Server 2016 служба работоспособности предоставляет информацию о следующих ошибках:  

### <a name="physicaldisk-8"></a>**Физический диск (8)**

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskfailedmedia"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.FailedMedia
* Серьезность: Предупреждение
* Причина: *«Сбой физического диска.»*
* RecommendedAction: *«Replace физический диск».*

#### <a name="faulttype-microsofthealthfaulttypephysicaldisklostcommunication"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.LostCommunication
* Серьезность: Предупреждение
* Причина: *«Подключение потеряно на физический диск.»*
* RecommendedAction: *«Проверьте, что физический диск не работает и правильности их подключения.»*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunresponsive"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.Unresponsive
* Серьезность: Предупреждение
* Причина: *«Физический диск из машин наблюдаются повторяющиеся зависания.»*
* RecommendedAction: *«Replace физический диск».*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskpredictivefailure"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.PredictiveFailure
* Серьезность: Предупреждение
* Причина: *«Сбой физического диска, согласно прогнозу произойти в ближайшее время.»*
* RecommendedAction: *«Replace физический диск».*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunsupportedhardware"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.UnsupportedHardware
* Серьезность: Предупреждение
* Причина: *«Физический диск в карантин, так как он не поддерживается поставщиком решений.»*
* RecommendedAction: *«Replace физического диска с помощью поддерживаемого оборудования».*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunsupportedfirmware"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.UnsupportedFirmware
* Серьезность: Предупреждение
* Причина: *«Физический диск — в карантин, так как его версия встроенного по не поддерживается поставщиком решений».*
* RecommendedAction: *«Обновление встроенного по на физическом диске, до целевой версии.»*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunrecognizedmetadata"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.UnrecognizedMetadata
* Серьезность: Предупреждение
* Причина: *«Физический диск содержит нераспознанный meta data».*
* RecommendedAction: *«Этот диск может содержать данные из неизвестного хранилища пула. Сначала убедитесь, что отсутствуют полезные данные на этом диске, а затем восстановить диск.»*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskfailedfirmwareupdate"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.FailedFirmwareUpdate
* Серьезность: Предупреждение
* Причина: *«Неудачная попытка обновления встроенного по на физическом диске.»*
* RecommendedAction: *«Попробуйте с помощью различных двоичных встроенного по».*

### <a name="virtual-disk-2"></a>**Виртуальный диск (2)**

#### <a name="faulttype-microsofthealthfaulttypevirtualdisksneedsrepair"></a>FaultType: Microsoft.Health.FaultType.VirtualDisks.NeedsRepair
* Серьезность: Сведения
* Причина: *«Некоторые данные на этом томе не полностью устойчивой. Она остается доступной.»*
* RecommendedAction: *«Восстановление устойчивости данных».*

#### <a name="faulttype-microsofthealthfaulttypevirtualdisksdetached"></a>FaultType: Microsoft.Health.FaultType.VirtualDisks.Detached
* Серьезность: Критическое
* Причина: *«Том недоступен. Некоторые данные могут быть потеряны.»*
* RecommendedAction: *«Проверьте физическое устройство и/или сетевое подключение всех устройств хранения. Может потребоваться восстановление из резервной копии.»*

### <a name="pool-capacity-1"></a>**Емкость пула (1)**

#### <a name="faulttype-microsofthealthfaulttypestoragepoolinsufficientreservecapacityfault"></a>FaultType: Microsoft.Health.FaultType.StoragePool.InsufficientReserveCapacityFault
* Серьезность: Предупреждение
* Причина: *«В пул носителей не поддерживает минимальный рекомендуемый объем резерва. Это может ограничить возможность восстановления данных устойчивости в случае сбоя диска.»*
* RecommendedAction: *«Добавление дополнительной емкости для пула носителей, либо освободить емкость. Минимальный рекомендуемый резерва зависит от развертывания, но имеет емкость, накопленные приблизительно 2 дисков.»*

### <a name="volume-capacity-2sup1sup"></a>**Емкость тома (2)**<sup>1</sup>

#### <a name="faulttype-microsofthealthfaulttypevolumecapacity"></a>FaultType: Microsoft.Health.FaultType.Volume.Capacity
* Серьезность: Предупреждение
* Причина: *«Томе заканчивается доступное пространство.»*
* RecommendedAction: *«Увеличить размер тома или перенос рабочих нагрузок на другие тома.»*

#### <a name="faulttype-microsofthealthfaulttypevolumecapacity"></a>FaultType: Microsoft.Health.FaultType.Volume.Capacity
* Серьезность: Критическое
* Причина: *«Томе заканчивается доступное пространство.»*
* RecommendedAction: *«Увеличить размер тома или перенос рабочих нагрузок на другие тома.»*

### <a name="server-3"></a>**Сервер (3)**

#### <a name="faulttype-microsofthealthfaulttypeserverdown"></a>FaultType: Microsoft.Health.FaultType.Server.Down
* Серьезность: Критическое
* Причина: *«Не удается подключиться к серверу.»*
* RecommendedAction: *«Запустите или заменить сервер».*

#### <a name="faulttype-microsofthealthfaulttypeserverisolated"></a>FaultType: Microsoft.Health.FaultType.Server.Isolated
* Серьезность: Критическое
* Причина: *«Сервер изолирована от кластера из-за проблем с подключением.»*
* RecommendedAction: *«Если изоляция не удается устранить, проверьте в сети или перенос рабочих нагрузок на другие узлы.»*

#### <a name="faulttype-microsofthealthfaulttypeserverquarantined"></a>FaultType: Microsoft.Health.FaultType.Server.Quarantined
* Серьезность: Критическое
* Причина: *«Сервер в карантин в кластере из-за повторяющихся ошибок.»*
* RecommendedAction: *«Вместо имени сервера или исправления сети».*

### <a name="cluster-1"></a>**Кластер (1)**

#### <a name="faulttype-microsofthealthfaulttypeclusterquorumwitnesserror"></a>FaultType: Microsoft.Health.FaultType.ClusterQuorumWitness.Error
* Серьезность: Критическое
* Причина: *«Кластер — один сбой сервера из строя».*
* RecommendedAction: *«Проверьте ресурса-свидетеля и перезапустите при необходимости. Запустите или замена неисправных сервера.»*

### <a name="network-adapterinterface-4"></a>**Сетевой адаптер и интерфейс (4)**

#### <a name="faulttype-microsofthealthfaulttypenetworkadapterdisconnected"></a>FaultType: Microsoft.Health.FaultType.NetworkAdapter.Disconnected
* Серьезность: Предупреждение
* Причина: *«Сетевой интерфейс был отключен.»*
* RecommendedAction: *«Подключите сетевой кабель.»*

#### <a name="faulttype-microsofthealthfaulttypenetworkinterfacemissing"></a>FaultType: Microsoft.Health.FaultType.NetworkInterface.Missing
* Серьезность: Предупреждение
* Причина: *«Сервер {server} отсутствуют сетевые адаптеры, подключенные к сети кластера {сети кластера}.»*
* RecommendedAction: *«Подключите сервер к отсутствует сети кластера».*

#### <a name="faulttype-microsofthealthfaulttypenetworkadapterhardware"></a>FaultType: Microsoft.Health.FaultType.NetworkAdapter.Hardware
* Серьезность: Предупреждение
* Причина: *«Сетевой интерфейс произошел сбой оборудования.»*
* RecommendedAction: *«Replace адаптера сетевого интерфейса».*

#### <a name="faulttype-microsofthealthfaulttypenetworkadapterdisabled"></a>FaultType: Microsoft.Health.FaultType.NetworkAdapter.Disabled
* Серьезность: Предупреждение
* Причина: *«Сетевой интерфейс {сетевой интерфейс} не включена и не используется.»*
* RecommendedAction: *«Включить сетевой интерфейс».*

### <a name="enclosure-6"></a>**Корпус (6)**

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurelostcommunication"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.LostCommunication
* Серьезность: Предупреждение
* Причина: *«Связь потеряна корпуса хранилища.»*
* RecommendedAction: *«Запустить или замена корпуса хранилища».*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurefanerror"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.FanError
* Серьезность: Предупреждение
* Причина: *«В позиции {позиции} отсека перестал работать вентилятор.»*
* RecommendedAction: *«Replace неисправности вентилятора в массиве хранилища».*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurecurrentsensorerror"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.CurrentSensorError
* Серьезность: Предупреждение
* Причина: *«Не удалось датчик тока, расположенного в позиции {позиции} корпуса хранилища».*
* RecommendedAction: *«Replace датчик в массиве хранилища».*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurevoltagesensorerror"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.VoltageSensorError
* Серьезность: Предупреждение
* Причина: *«Не удалось Датчик напряжения, расположенного в позиции {позиции} корпуса хранилища».*
* RecommendedAction: *«Replace Датчик напряжения в массиве хранилища».*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosureiocontrollererror"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.IoControllerError
* Серьезность: Предупреждение
* Причина: *«Не удалось контроллера ввода-ВЫВОДА, расположенного в позиции {позиции} корпуса хранилища».*
* RecommendedAction: *«Replace контроллеру ввода-ВЫВОДА в массиве хранилища».*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosuretemperaturesensorerror"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.TemperatureSensorError
* Серьезность: Предупреждение
* Причина: *«Не удалось датчик температуры, расположенного в позиции {позиции} корпуса хранилища».*
* RecommendedAction: *«Replace датчика температуры в массиве хранилища».*

### <a name="firmware-rollout-3"></a>**Развертывание встроенного по (3)**

#### <a name="faulttype-microsofthealthfaulttypefaultdomainfailedmaintenancemode"></a>FaultType: Microsoft.Health.FaultType.FaultDomain.FailedMaintenanceMode
* Серьезность: Предупреждение
* Причина: *«В настоящее время не могли добиться прогресса, выполняя развертывание встроенного по.»*
* RecommendedAction: *«Проверить все дисковые находятся в работоспособном состоянии, а что нет домен сбоя, в настоящее время находится в режиме обслуживания».*

#### <a name="faulttype-microsofthealthfaulttypefaultdomainfirmwareverifyversionfaile"></a>FaultType: Microsoft.Health.FaultType.FaultDomain.FirmwareVerifyVersionFaile
* Серьезность: Предупреждение
* Причина: *«Развертывание встроенного по была отменена из-за сведений о версии встроенного по может быть прочитан или непредвиденных после применения обновления встроенного по».*
* RecommendedAction: *«Restart встроенного по разворачивать после устранения проблемы встроенного по.»*

#### <a name="faulttype-microsofthealthfaulttypefaultdomaintoomanyfailedupdates"></a>FaultType: Microsoft.Health.FaultType.FaultDomain.TooManyFailedUpdates
* Серьезность: Предупреждение
* Причина: *«Развертывание встроенного по была отменена из-за слишком много физических дисков, Сбой попытки обновления встроенного по».*
* RecommendedAction: *«Restart встроенного по разворачивать после устранения проблемы встроенного по.»*

### <a name="storage-qos-3sup2sup"></a>**Качество обслуживания хранилища (3)**<sup>2</sup>

#### <a name="faulttype-microsofthealthfaulttypestorqosinsufficientthroughput"></a>FaultType: Microsoft.Health.FaultType.StorQos.InsufficientThroughput
* Серьезность: Предупреждение
* Причина: *«Пропускная способность хранилища недостаточен для удовлетворения резервы.»*
* RecommendedAction: *«Настроить политики качества обслуживания хранилища».*

#### <a name="faulttype-microsofthealthfaulttypestorqoslostcommunication"></a>FaultType: Microsoft.Health.FaultType.StorQos.LostCommunication
* Серьезность: Предупреждение
* Причина: *«Диспетчер политики качества обслуживания хранилища потерял связь с томом.»*
* RecommendedAction: *«Перезагрузите узлы {узла}»*

#### <a name="faulttype-microsofthealthfaulttypestorqosmisconfiguredflow"></a>FaultType: Microsoft.Health.FaultType.StorQos.MisconfiguredFlow
* Серьезность: Предупреждение
* Причина: *«Один или несколько потребителей хранилища (обычно виртуальные машины) использование несуществующую политику с идентификатором {id}».*
* RecommendedAction: *«Повторно создать все отсутствующие политики качества обслуживания хранилища».*

<sup>1</sup> указывает том был достигнут полный 80% (незначительный уровень серьезности) или полная 90% (значительный уровень серьезности).  
<sup>2</sup> указывает, что некоторые незначительный на томе не выполнил их минимальное значение IOPS для более чем 10% (минимальное), 30% (значительный) или 50% (критический уровень) времени за 24-часовой период.  

>[!NOTE]
> Работоспособность компонентов дисковой полки (вентиляторы, источников питания, датчики и т. п.) определяется по данным SCSI Enclosure Services (SES). Если поставщик не предоставляет эту информацию, служба работоспособности ее не отображает.  

## <a name="see-also"></a>См. также

- [Служба работоспособности в Windows Server 2016](health-service-overview.md)
