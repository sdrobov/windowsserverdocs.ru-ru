---
title: Отчеты о работоспособности службы
ms.prod: windows-server-threshold
manager: eldenc
ms.author: cosdar
ms.technology: storage-health-service
ms.topic: article
ms.assetid: ''
author: cosmosdarwin
ms.date: 10/05/2017
ms.openlocfilehash: bc21b9fdec5700fec23dc6af7ca15873ded34bea
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821965"
---
# <a name="health-service-reports"></a>Отчеты о работоспособности службы
> Область применения: Windows Server 2016

## <a name="what-are-reports"></a>Что такое отчеты  

Служба работоспособности уменьшает трудозатраты для получения производительность в реальном времени и сведения о емкости из дисковых кластера. Новый командлет предоставляет проверенный список важных метрик, которые эффективно собираются и динамически агрегируются по узлам с встроенную логику для определения членства в кластерах. Все значения предоставляются только в режиме реального времени по состоянию на конкретный момент.  

## <a name="usage-in-powershell"></a>Использование в PowerShell

Чтобы получить метрики для всего кластера дисковых пространств с помощью этого командлета:

```PowerShell
Get-StorageSubSystem Cluster* | Get-StorageHealthReport
```

Необязательный **число** параметр указывает, сколько наборов значений следует возвращать с односекундными интервалами.  

```PowerShell
Get-StorageSubSystem Cluster* | Get-StorageHealthReport -Count <Count>  
```

Можно также получить метрики для одного конкретного тома или сервер:  

```PowerShell
Get-Volume -FileSystemLabel <Label> | Get-StorageHealthReport -Count <Count>  

Get-StorageNode -Name <Name> | Get-StorageHealthReport -Count <Count>
```

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

Вызвать **GetReport** чтобы начать потоковую передачу образцы expert проверенный список важных метрик, которые эффективно собираются и динамически агрегируются по узлам с встроенную логику для определения членства в кластерах. Примеры будут поступать каждую секунду соответственно. Все значения предоставляются только в режиме реального времени по состоянию на конкретный момент.

Метрики можно настроить потоковую передачу для трех областей: любой том, любой узел или кластер.

Полный список метрик, доступных в каждой области видимости в Windows Server 2016 описана ниже.

### <a name="iobserveronnext"></a>IObserver.OnNext()

Этот пример кода использует [шаблон разработки наблюдателя](https://msdn.microsoft.com/en-us/library/ee850490(v=vs.110).aspx) для реализация объекта Observer, **OnNext()** метод будет вызываться при поступлении каждого нового примера метрик. Его **OnCompleted()** будет вызываться метод Если/при потоковой передаче заканчивается. Например можно использовать его чтобы повторно инициировать потоковой передачи, поэтому она продолжается неопределенное время.

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

### <a name="begin-streaming"></a>Начать потоковую передачу

С помощью наблюдателя, который определен можно начать потоковую передачу.

Укажите целевой объект **CimInstance** в котором необходимо метрики с заданной областью. Он может быть любой том, любой узел или кластер.

Параметр count предшествует потоковой передачи заканчивается число выборок.

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

Нечего и говорить эти показатели можно визуализировать, хранимых в базе данных или использовать любым подходящим способом, подходящим.

### <a name="properties-of-reports"></a>Свойства отчетов

Каждый пример метрик — один «отчет», который содержит много «» соответствующие записи отдельные метрики.

Полную схему, проверять **MSFT\_StorageHealthReport** и **MSFT\_HealthRecord** классы в *storagewmi.mof*.

У каждой метрики есть только три свойства, в этой таблице.

| **Свойство** | **Пример**       |
| -------------|-------------------|
| Имя         | IOLatencyAverage  |
| Значение        | 0.00021           |
| Единицы        | 3                 |

Единицы = {0, 1, 2, 3, 4}, где 0 = «Байты», 1 = «BytesPerSecond», 2 = «CountPerSecond», 3 = «Секунд», или 4 = «Percentage».

## <a name="coverage"></a>Покрытие

Ниже приведены метрики, доступные для каждой области в Windows Server 2016.

### <a name="msftstoragesubsystem"></a>MSFT_StorageSubSystem

| **Name**                        | **Единицы** |
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

| **Name**            | **Единицы** |
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

| **Name**            | **Единицы** |
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

## <a name="see-also"></a>См. также

- [Служба работоспособности в Windows Server 2016](health-service-overview.md)
