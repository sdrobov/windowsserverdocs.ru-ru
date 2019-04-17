---
title: "Отчеты о работоспособности службы"
ms.prod: windows-server-threshold
manager: eldenc
ms.author: cosdar
ms.technology: storage-health-service
ms.topic: article
ms.assetid: 
author: cosmosdarwin
ms.date: 10/05/2017
ms.openlocfilehash: bc21b9fdec5700fec23dc6af7ca15873ded34bea
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="health-service-reports"></a>Отчеты о работоспособности службы
> Применяется к Windows Server 2016

## <a name="what-are-reports"></a>Что такое отчеты  

Служба работоспособности уменьшает трудозатраты для получения динамической производительности и емкости сведения с кластером локальных дисковых пространств. Новый командлет предоставляет отбирает список самых важных метрик, которые эффективно собираются и динамически агрегируются с использованием специального алгоритма для определения членства в кластере узлов. Все значения предоставляются только в режиме реального времени и момент времени.  

## <a name="usage-in-powershell"></a>Использование в PowerShell

Этот командлет используется для получения метрики для всего кластера локальных дисковых пространств:

```PowerShell
Get-StorageSubSystem Cluster* | Get-StorageHealthReport
```

Необязательный **число** параметр указывает, сколько наборов значений следует возвращать с односекундными интервалами.  

```PowerShell
Get-StorageSubSystem Cluster* | Get-StorageHealthReport -Count <Count>  
```

Вы также можете получить метрики для одного конкретного тома или сервер:  

```PowerShell
Get-Volume -FileSystemLabel <Label> | Get-StorageHealthReport -Count <Count>  

Get-StorageNode -Name <Name> | Get-StorageHealthReport -Count <Count>
```

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

Вызов **GetReport** начать потоковую передачу выборки подборка expert перечень важных метрик, которые эффективно собираются и динамически агрегируются с использованием специального алгоритма для определения членства в кластере узлов. Примеры будут доставлены каждую секунду соответственно. Все значения предоставляются только в режиме реального времени и момент времени.

Метрики можно выполнять потоковую передачу трех областей: кластера, любой узел или любой другой том.

Полный список метрики в каждой области, в Windows Server 2016, описано ниже.

### <a name="iobserveronnext"></a>IObserver.OnNext()

Этот пример кода использует [шаблон разработки наблюдателя](https://msdn.microsoft.com/en-us/library/ee850490(v=vs.110).aspx) реализовать наблюдатель которого **OnNext()** метод будет вызываться при поступлении каждого нового образца метрики. Его **OnCompleted()** будет вызван метод при/при потоковой передаче заканчивается. Например может используется для нового сеанса потоковой передачи, поэтому он продолжает выполняться неопределенно долго.

```
class MetricsObserver<T> : IObserver<T>
{
    public void OnNext(T Result)
    {
        // Cast
        CimMethodStreamedResult StreamedResult = Result as CimMethodStreamedResult;

        if (StreamedResult != null)
        {
            // For illustration, you could store the metrics in this dictionary
            Dictionary<string, string> Metrics = new Dictionary<string, string>();

            // Unpack
            CimInstance Report = (CimInstance)StreamedResult.ItemValue;
            IEnumerable<CimInstance> Records = (IEnumerable<CimInstance>)Report.CimInstanceProperties["Records"].Value;
            foreach (CimInstance Record in Records)
            {
                /// Each Record has "Name", "Value", and "Units"
                Metrics.Add(
                    Record.CimInstanceProperties["Name"].Value.ToString(),
                    Record.CimInstanceProperties["Value"].Value.ToString()
                    );
            }

            // TODO: Whatever you want!
        }
    }
    public void OnError(Exception e)
    {
        // Handle Exceptions
    }
    public void OnCompleted()
    {
        // Reinvoke BeginStreamingMetrics(), defined in the next section
    }
}
```

### <a name="begin-streaming"></a>Начинайте потоковую передачу

С помощью определенных наблюдатель можно начать потоковой передачи.

Укажите целевой объект **CimInstance** в которых нужно метрики с заданной областью. Он может быть кластера, любой узел или любой другой том.

Параметр count предшествует число выборок, которое заканчивается потоковой передачи.

```
CimInstance Target = Cluster; // From among the objects discovered in DiscoverObjects()

public void BeginStreamingMetrics(CimSession Session, CimInstance HealthService, CimInstance Target)
{
    // Set Parameters
    CimMethodParametersCollection MetricsParams = new CimMethodParametersCollection();
    MetricsParams.Add(CimMethodParameter.Create("TargetObject", Target, CimType.Instance, CimFlags.In));
    MetricsParams.Add(CimMethodParameter.Create("Count", 999, CimType.UInt32, CimFlags.In));
    // Enable WMI Streaming
    CimOperationOptions Options = new CimOperationOptions();
    Options.EnableMethodResultStreaming = true;
    // Invoke API
    CimAsyncMultipleResults<CimMethodResultBase> InvokeHandler;
    InvokeHandler = Session.InvokeMethodAsync(
        HealthService.CimSystemProperties.Namespace, HealthService, "GetReport", MetricsParams, Options
        );
    // Subscribe the Observer
    MetricsObserver<CimMethodResultBase> Observer = new MetricsObserver<CimMethodResultBase>(this);
    IDisposable Disposeable = InvokeHandler.Subscribe(Observer);
}
```

Говорить эти показатели можно визуализировать, хранимых в базе данных или использовать удобным образом.

### <a name="properties-of-reports"></a>Свойства отчетов

Каждый пример метрики — один» отчет», который содержит множество» «соответствующие записи отдельных метрики.

Схему полной проверки **MSFT\_StorageHealthReport** и **MSFT\_HealthRecord** классы в *storagewmi.mof*.

Каждой метрики имеет только три свойства, в этой таблице.

| **Свойство** | **Пример**       |
| -------------|-------------------|
| Имя         | IOLatencyAverage  |
| Значение        | 0.00021           |
| Единицы        | 3                 |

Единицы = {0, 1, 2, 3, 4}, где 0 = 1 «байт» = «BytesPerSecond», 2 = «CountPerSecond», 3 = «Секунд», или 4 = «Процент».

## <a name="coverage"></a>Покрытие

Ниже приведены метрики, доступных для каждой области, в Windows Server 2016.

### <a name="msftstoragesubsystem"></a>MSFT_StorageSubSystem

| **Имя**                        | **Единицы** |
|---------------------------------|-----------|
| CPUUsage                        | 4         |
| CapacityPhysicalPooledAvailable | 0         |
| CapacityPhysicalPooledTotal     | 0         |
| CapacityPhysicalTotal           | 0         |
| CapacityPhysicalUnpooled        | 0         |
| CapacityVolumesAvailable        | 0         |
| CapacityVolumesTotal            | 0         |
| IOLatencyAverage                | 3         |
| IOLatencyRead                   | 3         |
| IOLatencyWrite                  | 3         |
| IOPSRead                        | 2         |
| IOPSTotal                       | 2         |
| IOPSWrite                       | 2         |
| IOThroughputRead                | 1         |
| IOThroughputTotal               | 1         |
| IOThroughputWrite               | 1         |
| MemoryAvailable                 | 0         |
| MemoryTotal                     | 0         |


### <a name="msftstoragenode"></a>MSFT_StorageNode

| **Имя**            | **Единицы** |
|---------------------|-----------|
| CPUUsage            | 4         |
| IOLatencyAverage    | 3         |
| IOLatencyRead       | 3         |
| IOLatencyWrite      | 3         |
| IOPSRead            | 2         |
| IOPSTotal           | 2         |
| IOPSWrite           | 2         |
| IOThroughputRead    | 1         |
| IOThroughputTotal   | 1         |
| IOThroughputWrite   | 1         |
| MemoryAvailable     | 0         |
| MemoryTotal         | 0         |

### <a name="msftvolume"></a>MSFT_Volume

| **Имя**            | **Единицы** |
|---------------------|-----------|
| CapacityAvailable   | 0         |
| CapacityTotal       | 0         |
| IOLatencyAverage    | 3         |
| IOLatencyRead       | 3         |
| IOLatencyWrite      | 3         |
| IOPSRead            | 2         |
| IOPSTotal           | 2         |
| IOPSWrite           | 2         |
| IOThroughputRead    | 1         |
| IOThroughputTotal   | 1         |
| IOThroughputWrite   | 1         |

## <a name="see-also"></a>См. также:

- [Служба работоспособности в Windows Server 2016](health-service-overview.md)
