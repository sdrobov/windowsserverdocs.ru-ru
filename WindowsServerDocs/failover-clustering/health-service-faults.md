---
title: "Ошибок службы работоспособности"
ms.prod: windows-server-threshold
manager: eldenc
ms.author: cosdar
ms.technology: storage-health-service
ms.topic: article
ms.assetid: 
author: cosmosdarwin
ms.date: 10/05/2017
ms.openlocfilehash: c9e1fb4568ee93739c49ccc1a13106b09161c5f3
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="health-service-faults"></a>Ошибок службы работоспособности
> Применяется к Windows Server 2016

## <a name="what-are-faults"></a>Что такое сообщения об ошибках

Служба работоспособности постоянно наблюдает за кластером локальных дисковых пространств для выявления проблем и создания «сообщения об ошибках». Новый командлет отображает все актуальные ошибки, что позволяет легко проверить работоспособность развертывания, не изучая отдельно каждую сущность и функцию. Сообщения об ошибках предназначены для точную информацию, просты для понимания и какие-либо действия.  

Каждое такое сообщение содержит пять важных полей.  

-   Уровень серьезности
-   Описание проблемы
-   Рекомендуемые действия для устранения проблемы
-   Сведения для идентификации сущности, вызвавшей сбой
-   Физическое расположение (если применимо)

Например вот распространенной ошибки:  

```
Severity: MINOR                                         
Reason: Connectivity has been lost to the physical disk.                           
Recommendation: Check that the physical disk is working and properly connected.    
Part: Manufacturer Contoso, Model XYZ9000, Serial 123456789                        
Location: Seattle DC, Rack B07, Node 4, Slot 11
```

 >[!NOTE]
 > Физическое расположение основывается на конфигурации домена сбоя. Дополнительные сведения о доменах сбоя см. в разделе [доменах сбоя в Windows Server 2016](fault-domains.md). Если эти сведения отсутствуют, поле расположение будет менее полезно — например, он может показывать только номер слота.  

## <a name="root-cause-analysis"></a>Анализ основных причин

Службы работоспособности способна оценивать причинно-следственные между сущностями, чтобы группировать ошибки, объединенные одной основной причиной сбойного. Выявление таких цепочек влияния, это позволяет снизить объемы выводимой информации. Например если сервер не работает, ожидается, чем все диски на сервере также будет использоваться без подключения к. Таким образом только сообщение об ошибке будет вызываться для основной причины — в этом случае сервер.  

## <a name="usage-in-powershell"></a>Использование в PowerShell

Чтобы просмотреть все актуальные ошибки в PowerShell, запустите этот командлет:

```PowerShell
Get-StorageSubSystem Cluster* | Debug-StorageSubSystem  
```

Эта команда возвращает все сообщения об ошибках, которые имеют отношение к кластеру локальных дисковых пространств. Чаще всего эти ошибки связаны с оборудованием или конфигурацией. Если актуальных ошибок нет, этот командлет ничего не возвращает.  

>[!NOTE]
> В рабочей среде, а также на свой страх и риск экспериментировать вы можете эта возможность создавать условия для ошибок, — например, удалив один физический диск или завершить работу узла. Когда появится сообщение об ошибке, верните физический диск или перезапустите узел — сообщение должно исчезнуть.

Вы также можете просмотреть ошибки, относящиеся только к конкретному тому или файловые ресурсы с помощью следующих командлетов:  

```PowerShell
Get-Volume -FileSystemLabel <Label> | Debug-Volume  

Get-FileShare -Name <Name> | Debug-FileShare  
```

Эта команда возвращает все сообщения об ошибках, которые влияют только конкретного тома или общего ресурса. Чаще всего эти ошибки связаны с планирования емкости, устойчивостью данных или функции, такие как хранилища качества обслуживания или репликой хранилища. 

## <a name="usage-in-net-and-c"></a>Использование в .NET и C#

### <a name="connect"></a>Подключение

Для запроса службы работоспособности, необходимо установить **CimSession** с кластером. Для этого необходимо будет некоторые вещи, которые доступны только в полной .NET, то есть невозможно легко непосредственно из Интернета или мобильного приложения. Эти примеры кода будет использовать c#, самый простой вариант для этого уровня доступа к данным.

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

Данного пользователя должны быть локальным администратором целевого компьютера.

Рекомендуется создавать пароль **SecureString** непосредственно из пользовательского ввода в в реальном времени, так что пароль никогда не сохраняется в памяти открытым текстом. Это помогает устранить ряд соображений безопасности. Но на практике, создав его выше чаще всего для создания прототипов различных целей.

### <a name="discover-objects"></a>Обнаружение объектов

С помощью **CimSession** установлено, вы можете запросить инструментария управления Windows (WMI) в кластере.

Прежде чем начать пользоваться сообщения об ошибках или метрики, необходимо будет получить экземпляры соответствующих объектов. Во-первых, **MSFT\_StorageSubSystem** представляет дисковых пространств, в кластере. Используя это, вы можете получить все **MSFT\_StorageNode** в кластере и каждый **MSFT\_Volume**, тома данных. Наконец, вам потребуется **MSFT\_StorageHealth**, сам по себе слишком службе работоспособности.

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

Это те же объекты в PowerShell вы получаете с помощью командлетов, например **Get-StorageSubSystem**, **Get-StorageNode**, и **Get-Volume**.

Вы может получить доступ к те же свойства, описанные по адресу [классы API управления хранилищами](https://msdn.microsoft.com/en-us/library/windows/desktop/hh830612(v=vs.85).aspx).

```
...
using System.Diagnostics;

foreach (CimInstance Node in Nodes)
{
    // For illustration, write each node's Name to the console. You could also write State (up/down), or anything else!
    Debug.WriteLine("Discovered Node " + Node.CimInstanceProperties["Name"].Value.ToString());
}
```

### <a name="query-faults"></a>Ошибок запросов

Вызвать **Диагностика** для получения все актуальные ошибки, подходящей для целевой **CimInstance**, которая быть кластера или любой другой том.

Полный список ошибок в каждой области, в Windows Server 2016, описано ниже.

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

### <a name="optional-myfault-class"></a>Необязательно: MyFault класса

Может иметь смысл для создания и сохранения представление сообщения об ошибках. Например, это **MyFault** класс хранит несколько ключевых свойств сообщения об ошибках, в том числе **FaultId**, который можно использовать позднее для связать обновления или удалять уведомления, или для нее в том случае, если же сбой, Обнаружено несколько раз, для какой-либо причине.

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

Полный список свойств в каждое такое сообщение (**DiagnoseResult**) описано ниже.

### <a name="fault-events"></a>События сбоев

Если сообщения об ошибках создания, удаления или обновления, служба работоспособности создает события WMI. Они необходимы для синхронизации состояния приложения без часто опроса и может помочь в таких действий, как определить, когда для отправки оповещений по электронной почте, например. Чтобы оформить подписку на эти события, этот пример кода использует шаблон разработки наблюдателя еще раз.

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

Затем реализовать наблюдатель которого **OnNext()** метод будет вызываться всякий раз, когда создается новое событие.

Каждое событие содержит **ChangeType**, указывающее на ошибку, создается ли, удаленные или обновленные и соответствующие **FaultId**.

Кроме того они содержат все свойства сбоя сам.

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

Сообщения об ошибках не предназначены пометку «Просмотр» или разрешенных пользователем. Они создаются, когда служба работоспособности обнаруживает проблему и автоматически удаляются, и только в том случае, если служба работоспособности больше не может просмотреть проблемы. Как правило это отражает проблема устранена.

Однако в некоторых случаях ошибки может быть обнаружить повторно службой работоспособности (например, после перехода на другой ресурс, или из-за периодических разрывах подключения, и т. д.). По этой причине может смысл для сохранения представление сообщения об ошибках, чтобы легко дедуплицировать некоторые папки. Это особенно важно, если для отправки оповещений по электронной почте или наличие эквивалентных прав.

### <a name="properties-of-faults"></a>Свойства сообщения об ошибках

В этой таблице представлены несколько ключевых свойств объекта сбоя. Схему полной проверки **MSFT\_StorageDiagnoseResult** класса *storagewmi.mof*.

| **Свойство**              | **Пример**                                                     |
|---------------------------|-----------------------------------------------------------------|
| FaultId                   | {12345-12345-12345-12345-12345}                                 |
| FaultType                 | Microsoft.Health.FaultType.Volume.Capacity                      |
| Причина                    | «Томе недостаточно свободного места.»                 |
| PerceivedSeverity         | 5                                                               |
| FaultingObjectDescription | Contoso XYZ9000 S.N. 123456789                                  |
| FaultingObjectLocation    | Стойка A06, RU 25, слот 11                                        |
| RecommendedActions        | {«Разверните тома.», «Перенос рабочих нагрузок других томов.»}   |

**FaultId** Unique в рамках области одного кластера.

**PerceivedSeverity** PerceivedSeverity = {4, 5, 6} = {«Информационное», «Предупреждение» и «Ошибка»} или эквивалентные цвета, такие как синий, желтый и красный цвет.

**FaultingObjectDescription** часть информации для оборудования, обычно пустой объектов по.

**FaultingObjectLocation** сведения о местоположении для оборудования, обычно пустой объектов по.

**RecommendedActions** список рекомендуемых действий, которые зависят друг от друга и в произвольном порядке. В настоящее время этот список часто является длиной 1.

## <a name="properties-of-fault-events"></a>Свойства событий сбоя

В этой таблице представлены несколько ключевых свойств событие сбоя. Схему полной проверки **MSFT\_StorageFaultEvent** класса *storagewmi.mof*.

Примечание **ChangeType**, свидетельствующее ли сбоя создается, удаленные или обновляется и **FaultId**. Событие также содержит все свойства затронутых сбоя.

| **Свойство**              | **Пример**                                                     |
|---------------------------|-----------------------------------------------------------------|
| ChangeType                | 0                                                               |
| FaultId                   | {12345-12345-12345-12345-12345}                                 |
| FaultType                 | Microsoft.Health.FaultType.Volume.Capacity                      |
| Причина                    | «Томе недостаточно свободного места.»                 |
| PerceivedSeverity         | 5                                                               |
| FaultingObjectDescription | Contoso XYZ9000 S.N. 123456789                                  |
| FaultingObjectLocation    | Стойка A06, RU 25, слот 11                                        |
| RecommendedActions        | {«Разверните тома.», «Перенос рабочих нагрузок других томов.»}   |

**ChangeType** ChangeType = {0, 1, 2} = {«создать», «Удалить», «Обновления»}.

## <a name="coverage"></a>Покрытие

В Windows Server 2016 служба работоспособности предоставляет информацию о следующих ошибках:  

### **<a name="physicaldisk-8"></a>Физический диск (8)**

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskfailedmedia"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.FailedMedia
* Серьезность: предупреждение
* Причина: *«сбой физического диска.»*
* RecommendedAction: *«Замене физического диска.»*

#### <a name="faulttype-microsofthealthfaulttypephysicaldisklostcommunication"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.LostCommunication
* Серьезность: предупреждение
* Причина: *«Потеряно подключение к физическому диску.»*
* RecommendedAction: *«Проверьте, что физический диск не работает и правильно подключены.»*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunresponsive"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.Unresponsive
* Серьезность: предупреждение
* Причина: *«физического диска, проявляют повторяющиеся зависания».*
* RecommendedAction: *«Замене физического диска.»*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskpredictivefailure"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.PredictiveFailure
* Серьезность: предупреждение
* Причина: *«возникает скоро предсказать сбоя физического диска.»*
* RecommendedAction: *«Замене физического диска.»*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunsupportedhardware"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.UnsupportedHardware
* Серьезность: предупреждение
* Причина: *«физического диска в карантин, так как не поддерживается поставщиком решений.»*
* RecommendedAction: *«Замените физического диска поддерживаемого оборудования».*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunsupportedfirmware"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.UnsupportedFirmware
* Серьезность: предупреждение
* Причина: *«физический диск — в карантин, так как его версия встроенного по не поддерживается поставщиком решений».*
* RecommendedAction: *«Обновления встроенного по на физическом диске целевую версию.»*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskunrecognizedmetadata"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.UnrecognizedMetadata
* Серьезность: предупреждение
* Причина: *«физический диск Неизвестный метаданных».*
* RecommendedAction: *«этот диск может содержать данные из пула носителей неизвестно. Сначала убедитесь, что нет полезных данных на этом диске, а затем сбросить диска.»*

#### <a name="faulttype-microsofthealthfaulttypephysicaldiskfailedfirmwareupdate"></a>FaultType: Microsoft.Health.FaultType.PhysicalDisk.FailedFirmwareUpdate
* Серьезность: предупреждение
* Причина: *«Сбой попытки обновления встроенного по на физическом диске.»*
* RecommendedAction: *«Попробуйте использовать разные двоичные встроенного по».*

### **<a name="virtual-disk-2"></a>Виртуальный диск (2)**

#### <a name="faulttype-microsofthealthfaulttypevirtualdisksneedsrepair"></a>FaultType: Microsoft.Health.FaultType.VirtualDisks.NeedsRepair
* Серьезность: информационное сообщение
* Причина: *«некоторые данные на этом томе устойчив не полностью. Он остается доступен.»*
* RecommendedAction: *«Восстановление устойчивости данных».*

#### <a name="faulttype-microsofthealthfaulttypevirtualdisksdetached"></a>FaultType: Microsoft.Health.FaultType.VirtualDisks.Detached
* Серьезность: критический
* Причина: *«том недоступен. Некоторые данные могут быть потеряны.»*
* RecommendedAction: *«проверка физических и/или сетевое подключение всех запоминающих устройств. Может потребоваться восстановление из резервной копии.»*

### **<a name="pool-capacity-1"></a>Емкость пула (1)**

#### <a name="faulttype-microsofthealthfaulttypestoragepoolinsufficientreservecapacityfault"></a>FaultType: Microsoft.Health.FaultType.StoragePool.InsufficientReserveCapacityFault
* Серьезность: предупреждение
* Причина: *«в пул носителей не имеет минимальные рекомендуемые резервной мощности. Это может ограничить возможность восстановить данные устойчивости в случае сбоя диска.»*
* RecommendedAction: *«добавить дополнительную емкость пула носителей или освобождения емкости. Минимальное рекомендуемое резерв варьируется в зависимости от развертывания, но не в течение примерно 2 дисков емкости.»*

### <a name="volume-capacity-2sup1sup"></a>**Емкость тома (2)**<sup>1</sup>

#### <a name="faulttype-microsofthealthfaulttypevolumecapacity"></a>FaultType: Microsoft.Health.FaultType.Volume.Capacity
* Серьезность: предупреждение
* Причина: *«томе недостаточно свободного места.»*
* RecommendedAction: *«Увеличить размер тома или перенесите рабочих нагрузок на другие тома».*

#### <a name="faulttype-microsofthealthfaulttypevolumecapacity"></a>FaultType: Microsoft.Health.FaultType.Volume.Capacity
* Серьезность: критический
* Причина: *«томе недостаточно свободного места.»*
* RecommendedAction: *«Увеличить размер тома или перенесите рабочих нагрузок на другие тома».*

### **<a name="server-3"></a>Сервер (3)**

#### <a name="faulttype-microsofthealthfaulttypeserverdown"></a>FaultType: Microsoft.Health.FaultType.Server.Down
* Серьезность: критический
* Причина: *«не удается подключиться к серверу.»*
* RecommendedAction: *«Пуск или заменить сервера.»*

#### <a name="faulttype-microsofthealthfaulttypeserverisolated"></a>FaultType: Microsoft.Health.FaultType.Server.Isolated
* Серьезность: критический
* Причина: *«сервер изолирована от кластера, из-за проблемы с подключением.»*
* RecommendedAction: *«В случае изоляции проверьте сетей или миграция рабочих нагрузок на другие узлы».*

#### <a name="faulttype-microsofthealthfaulttypeserverquarantined"></a>FaultType: Microsoft.Health.FaultType.Server.Quarantined
* Серьезность: критический
* Причина: *«сервер карантин кластером из-за повторяющихся сбоев».*
* RecommendedAction: *«Вместо имени сервера или исправления сети».*

### **<a name="cluster-1"></a>Кластера (1)**

#### <a name="faulttype-microsofthealthfaulttypeclusterquorumwitnesserror"></a>FaultType: Microsoft.Health.FaultType.ClusterQuorumWitness.Error
* Серьезность: критический
* Причина: *«кластера — одна ошибка сервера от переход вниз».*
* RecommendedAction: *«проверьте ресурса-свидетеля и перезапустите при необходимости. Запустите или заменить неисправные серверы».*

### **<a name="network-adapterinterface-4"></a>Сетевой адаптер или интерфейс (4)**

#### <a name="faulttype-microsofthealthfaulttypenetworkadapterdisconnected"></a>FaultType: Microsoft.Health.FaultType.NetworkAdapter.Disconnected
* Серьезность: предупреждение
* Причина: *«сетевой интерфейс был отключен.»*
* RecommendedAction: *«Подключите сетевой кабель».*

#### <a name="faulttype-microsofthealthfaulttypenetworkinterfacemissing"></a>FaultType: Microsoft.Health.FaultType.NetworkInterface.Missing
* Серьезность: предупреждение
* Причина: *«{сервер} есть отсутствует сетевых адаптеров, подключенных к сети кластера {сети кластера}».*
* RecommendedAction: *«Подключите сервер к отсутствует сети кластера».*

#### <a name="faulttype-microsofthealthfaulttypenetworkadapterhardware"></a>FaultType: Microsoft.Health.FaultType.NetworkAdapter.Hardware
* Серьезность: предупреждение
* Причина: *«сетевой интерфейс наблюдалось сбоя оборудования».*
* RecommendedAction: *«Заменить сетевой адаптер».*

#### <a name="faulttype-microsofthealthfaulttypenetworkadapterdisabled"></a>FaultType: Microsoft.Health.FaultType.NetworkAdapter.Disabled
* Серьезность: предупреждение
* Причина: *«сетевой интерфейс {сетевого интерфейса} не включена и не используется.»*
* RecommendedAction: *«включить сетевого интерфейса.»*

### **<a name="enclosure-6"></a>Корпус (6)**

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurelostcommunication"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.LostCommunication
* Серьезность: предупреждение
* Причина: *«Связь потеряна для корпуса хранилища.»*
* RecommendedAction: *«Start или заменить корпуса хранилища.»*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurefanerror"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.FanError
* Серьезность: предупреждение
* Причина: *«сбой вентилятора позиции {позиции} корпуса хранилища.»*
* RecommendedAction: *«Замена вентилятора в массиве хранилища».*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurecurrentsensorerror"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.CurrentSensorError
* Серьезность: предупреждение
* Причина: *«датчика текущей позиции {позиции} корпуса хранилища не удалась.»*
* RecommendedAction: *«Замените текущий датчик в массиве хранилища».*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosurevoltagesensorerror"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.VoltageSensorError
* Серьезность: предупреждение
* Причина: *«Датчик напряжения позиции {позиции} корпуса хранилища не удалась.»*
* RecommendedAction: *«Замена Датчик напряжения в массиве хранилища».*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosureiocontrollererror"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.IoControllerError
* Серьезность: предупреждение
* Причина: *«контроллера ввода-ВЫВОДА в позиции {позиции} корпуса хранилища не удалась.»*
* RecommendedAction: *«Замена контроллер ввода-ВЫВОДА в массиве хранилища».*

#### <a name="faulttype-microsofthealthfaulttypestorageenclosuretemperaturesensorerror"></a>FaultType: Microsoft.Health.FaultType.StorageEnclosure.TemperatureSensorError
* Серьезность: предупреждение
* Причина: *«датчик температуры позиции {позиции} корпуса хранилища не удалась.»*
* RecommendedAction: *«Замена датчик температуры в массиве хранилища».*

### **<a name="firmware-rollout-3"></a>Выпуск встроенного по (3)**

#### <a name="faulttype-microsofthealthfaulttypefaultdomainfailedmaintenancemode"></a>FaultType: Microsoft.Health.FaultType.FaultDomain.FailedMaintenanceMode
* Серьезность: предупреждение
* Причина: *«В настоящее время не удается установить хода выполнения во время выполнения встроенного по время развертывания.»*
* RecommendedAction: *«Проверить все дисковые пространства находятся в работоспособном состоянии, а что нет домен сбоя в настоящее время находится в режиме обслуживания».*

#### <a name="faulttype-microsofthealthfaulttypefaultdomainfirmwareverifyversionfaile"></a>FaultType: Microsoft.Health.FaultType.FaultDomain.FirmwareVerifyVersionFaile
* Серьезность: предупреждение
* Причина: *«развертывание встроенного по был отменен из-за сведения о версии встроенного по нечитаемых или Непредвиденная после применения обновления встроенного по».*
* RecommendedAction: *«перезапуск встроенного по выпускать после устранения проблемы встроенного по.»*

#### <a name="faulttype-microsofthealthfaulttypefaultdomaintoomanyfailedupdates"></a>FaultType: Microsoft.Health.FaultType.FaultDomain.TooManyFailedUpdates
* Серьезность: предупреждение
* Причина: *«развертывание встроенного по был отменен из-за большого количества физических дисков, Сбой попытки обновления встроенного по».*
* RecommendedAction: *«перезапуск встроенного по выпускать после устранения проблемы встроенного по.»*

### <a name="storage-qos-3sup2sup"></a>**Качество обслуживания хранилища (3)**<sup>2</sup>

#### <a name="faulttype-microsofthealthfaulttypestorqosinsufficientthroughput"></a>FaultType: Microsoft.Health.FaultType.StorQos.InsufficientThroughput
* Серьезность: предупреждение
* Причина: *«пропускной способности хранилища недостаточен для удовлетворения резервы.»*
* RecommendedAction: *«Перенастроить политик качества обслуживания хранилища».*

#### <a name="faulttype-microsofthealthfaulttypestorqoslostcommunication"></a>FaultType: Microsoft.Health.FaultType.StorQos.LostCommunication
* Серьезность: предупреждение
* Причина: *«диспетчер политики качества обслуживания хранилища потеряла связь с томом.»*
* RecommendedAction: *«Перезагрузите узлы {узлов}»*

#### <a name="faulttype-microsofthealthfaulttypestorqosmisconfiguredflow"></a>FaultType: Microsoft.Health.FaultType.StorQos.MisconfiguredFlow
* Серьезность: предупреждение
* Причина: *«один или несколько потребителей хранилища (обычно виртуальных машин) используют несуществующее политику с идентификатором {идентификатор}.»*
* RecommendedAction: *«Заново создать все отсутствующие политики качества обслуживания хранилища.»*

<sup>1</sup> указывает том заполнен на 80% (незначительный уровень серьезности) или полного 90% (значительный уровень серьезности).  
<sup>2</sup> указывает некоторые .vhd(s) тома не выполняется их минимальное значение IOPS для более чем 10% (незначительный уровень), 30% (значительный уровень) или 50% (критический уровень) последние 24 часа.  

>[!NOTE]
> Работоспособность компонентов дисковой полки, например, вентиляторы, источников питания и датчики является производным от SCSI Enclosure Services (SES). Если поставщик не предоставляет эту информацию, служба работоспособности не удается отобразить его.  

## <a name="see-also"></a>См. также:

- [Служба работоспособности в Windows Server 2016](health-service-overview.md)
