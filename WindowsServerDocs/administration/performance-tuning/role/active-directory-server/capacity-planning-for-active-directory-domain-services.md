---
title: Планирование емкости для доменных служб Active Directory
description: Подробное описание факторов, которые следует учитывать при планировании загрузки для AD DS.
ms.prod: windows-server-threshold
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: v-tea; kenbrunf
author: Teresa-Motiv
ms.date: 7/3/2019
ms.openlocfilehash: 5a9e2d39d4eedd1e8fdb4bfeaf267ad4cb4c596a
ms.sourcegitcommit: be243a92f09048ca80f85d71555ea6ee3751d712
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67799836"
---
# <a name="capacity-planning-for-active-directory-domain-services"></a>Планирование емкости для доменных служб Active Directory

В этом разделе первоначально написан Майклом Алексей Brumfield, старшего специалиста корпорации Майкрософт и предоставляет рекомендации по планированию для доменных служб Active Directory (AD DS).

## <a name="goals-of-capacity-planning"></a>Цель планирования загрузки

Планирование мощности не является таким же, как Диагностика производительности инцидентов. Они тесно связанных, но существенно отличаются. Цель планирования —:  

- Правильно реализовать и управление средой 
- Свести к минимуму время, затраченное на устранение неполадок производительности.  
  
В планирование емкости организация может использовать базовой целевой платформы в 40% использования процессора в периоды пиковой нагрузки для требований к производительности клиента и время, необходимых для обновления оборудования в центре обработки данных. В свою очередь, чтобы получать уведомления об инцидентах аномалии в производительности, мониторинга порога оповещений может быть настроено на уровне 90% за определенный интервал в 5 минут.

Разница в том, при превышении порогового значения управления постоянно (одноразовым событием не является проблемой), добавление емкости (что добавление в дополнительных или более быстрых процессоров) будет решение или бы масштабирование сервиса на нескольких серверах решение. Пороговые значения производительности указать, что для взаимодействия с пользователем, в настоящее время страдает, так и для немедленного действия необходимы для ее устранения.

По аналогии: управление ресурсами — это Предотвращение автомобиль случайно, (защитных манере, убедившись, что тормоза работают правильно, и так далее), тогда как устранение проблем с производительностью, что сделать полиции, Пожарная и аварийный медицинских специалистов После инцидента. Речь идет о «защитного водил» Active Directory в стиле.

За последние несколько лет руководство по планированию емкости для вертикального масштабирования систем значительно изменился. Следующие изменения в архитектуре систем перейти к прохождению фундаментальные предположения о разработке и масштабирование службы:

- 64-разрядные серверные платформы  
- Виртуализация  
- Повышенная внимание энергопотребление  
- Хранилище SSD  
- Облачные сценарии  

Кроме того этот подход сместилось от планирования упражнения с планирования упражнения загрузки на основе служб загрузки на основе сервера. Доменные службы Active Directory (AD DS), старшего распределенная служба, которая многих продуктов Майкрософт и сторонних использовать в качестве серверной части, становится один наиболее важных продуктов для планирования правильно обеспечить достаточную производительность для запуска других приложений.

### <a name="baseline-requirements-for-capacity-planning-guidance"></a>Базовые требования для планирования емкости

В этой статье ожидаются следующие базовые требования:

- Читатели прочитаны и пользователь знаком с [производительности настройке рекомендации для Windows Server 2012 R2](https://docs.microsoft.com/previous-versions//dn529133(v=vs.85)).
- Платформа Windows Server является x x64 на основе архитектуры. Но даже в том случае, если среда Active Directory устанавливается на Windows Server 2003 x86 (теперь за пределами жизненного цикла поддержки) и имеет информационном дереве каталога (DIT) то есть размером меньше 1,5 ГБ и что можно легко может храниться в памяти, инструкции из этого статьи по-прежнему применимы.
- Планирование мощности — это непрерывный процесс, и должны периодически проверять, насколько хорошо среды является отвечающие ожиданиям.
- Оптимизация будет выполняться по несколько жизненных циклов оборудования как изменение затраты на оборудование. Например память становится дешевле, снижает затраты на ядро или стоимость хранения, отличную параметры изменения.
- Планирование периода занятости пиковой дня. Рекомендуется рассмотреть это с интервалом 30 минут или часов. Больше ничего могут скрыть фактическое пиков и все, что меньше искажается «переходные всплески.»
- Планирование роста сети в ходе жизненного цикла оборудования для предприятия. Сюда могут входить стратегию обновления или добавления оборудования в перемещение перебора или полное обновление каждые три-пять лет. Для каждого потребуется «прогноз» как гораздо нагрузки на Active Directory будет увеличиваться. Статистические данные, если собраны, поможет этой оценки. 
- План для обеспечения отказоустойчивости. После оценки *N* является производным, план для сценариев, включающих *N* &ndash; 1, *N* &ndash; 2, *N* &ndash; *x*.
  - Добавьте дополнительные серверы в соответствии с потребностями организации, чтобы убедиться, что потеря одного или нескольких серверов превышает емкость оценки наибольшая.
  - Также следует учитывать, что план роста и план допуска сбоя необходимо интегрировать. Например если одного контроллера домена требуется для поддержки нагрузки, но оценки является то, что нагрузки будет удвоить в следующем году и требуют двух контроллеров домена, общее, не будут достаточную емкость для обеспечения отказоустойчивости. Решение будет начинаться с трех контроллеров домена. Один может также планируем добавить третий контроллер домена после 3 или 6 месяцев, при непрерывном бюджета.

    >[!NOTE]
    >Добавление учитывал Active Directory приложений возможно значительное воздействие на нагрузку DC, ли нагрузки поступает из серверов приложений или клиентов.

### <a name="three-step-process-for-the-capacity-planning-cycle"></a>Три шага для планирования цикла

При планировании емкости, сначала определите, какие качества обслуживания необходим. Например в основной центр обработки данных поддерживает более высокая степень параллелизма и требует более согласованной работы для пользователей и приложений, которым требуется особое внимание на избыточности и минимизации узкие места системы и инфраструктуры. Напротив расположение вспомогательной с небольшим количеством пользователей не обязательно тот же уровень параллелизма или устойчивость к сбоям. Таким образом дополнительном офисе может не требоваться меньше внимания, оптимизация базовое оборудование и инфраструктуру, которая может привести к снижения затрат. Все рекомендациях и указания здесь предназначены для оптимальной производительности и может быть выборочно нестрогой для сценариев с менее требовательных.

Следующий вопрос: виртуализованный или физический? С точки зрения планирования емкости нет правильного или неправильного ответа; есть только другой набор переменных для работы с. Сценарии виртуализации сводятся к одному из двух вариантов:

- Сообщение об ошибке «прямое сопоставление» с одной гостевой каждого узла (где виртуализации существует исключительно для абстрагирования физического оборудования с сервера)
- «Общего узла»

Тестирования и производственная среда указывают, что в сценарии «прямое отображение» может обрабатываться одинаково на физический узел. Тем не менее, «Общие узла,» появилось несколько аспектов, выраженная в более подробно позже. В сценарии «общего узла» означает, что AD DS также конкуренции за ресурсы и штрафов и настройки рекомендаций для этого.

С помощью Учитывая эти вопросы цикл планирования емкости носит итеративный трех этапов:

1. Измерение существующей среды, определить где узких мест системы в настоящее время и получить необходимые для планирования требуется емкость среды основы.
1. Определите оборудование, необходимое в соответствии с критериями, указанными в шаге 1.
1. Отслеживание и проверка того, что инфраструктура реализованное работает спецификаций. Некоторые данные, собранные на этом шаге он становится базовых показателей для следующего цикла планирования ресурсов.

### <a name="applying-the-process"></a>Применение процесса

Чтобы оптимизировать производительность, убедитесь, правильно выбраны и настроены так, чтобы приложение загружает эти основные компоненты:

1. Память
1. Network
1. Хранилище
1. Процессор
1. Вход в сеть

Требования к хранилищу основные службы AD DS и общее поведение хорошо написанную клиентского программного обеспечения позволяют сред с до 10 000 до 20 000 пользователей, нет смысла серьезный вклад в отношении физического оборудования, почти все современные сервером для оптимизации производительности Класс системы будет справиться с нагрузкой. С другой стороны, в следующей таблице перечислены оценка существующей среды, чтобы выбрать подходящее оборудование. Каждый компонент анализируется подробно в последующих разделах, чтобы оценить инфраструктуру, используя базовые рекомендации и конкретных участников позволяет администраторам AD DS.

В целом:

- Любые изменения размера на основе текущих данных будет только точные для текущей среды.
- Для любой оценок ожидать, что запросу расти в течение жизненного цикла оборудования.
- Определяет, следует ли размера сегодня и расти в среду большего размера или добавляйте ресурсы над жизненным циклом.
- Для виртуализации те же субъекты и методологий для оптимизации производительности применяются, за исключением того, что должен быть добавлен к любому домена связанные с необходимостью поддержки виртуализации.
- Планирование емкости, которая пытается предсказать, что-то подобное не является точным обработки и анализа. Не ожидается вещей, для которого требуется вычислить идеально и с точностью 100%. Здесь инструкции являются leanest рекомендации; добавить емкость для дополнительной безопасности и непрерывно проверять что среде остается на целевом объекте.

### <a name="data-collection-summary-tables"></a>Сводные таблицы сбора данных

#### <a name="new-environment"></a>Новая среда

| Component | Оценки |
|-|-|
|Размер базы данных хранилища|40 КБ до 60 КБ для каждого пользователя|
|ОЗУ|Размер базы данных<br />Базовая операционная система рекомендаций<br />Сторонние приложения|
|Network|1 ГБ|
|ЦП|1000 параллельно работающих пользователей для каждого ядра|

#### <a name="high-level-evaluation-criteria"></a>Критерии оценки высокого уровня

| Component | Критерии оценки | Факторы, которые следует учесть при планировании |
|-|-|-|
|Размер базы данных хранилища|В подразделе под названием «для того, чтобы включить ведение журнала, места на диске, который освобождается при дефрагментации» в [ограничения хранилища](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/cc961769(v=technet.10))| |
|Хранилище / производительности базы данных|<ul><li>"Логический диск ( *\<диск для базы данных NTDS\>* ) \Avg Disk sec/Read,» «логический диск ( *\<диск для базы данных NTDS\>* ) \Avg сек записи на диск,»" Логический диск ( *\<диск для базы данных NTDS\>* ) \Avg диску (сек)»</li><li>«Логический диск ( *\<диск для базы данных NTDS\>* ) \Reads/sec,» «логический диск ( *\<диск для базы данных NTDS\>* ) \Writes/sec,» (логический диск) «  *\<Диск для базы данных NTDS\>* ) \Transfers/sec»</li></ul>|<ul><li>Хранилище имеет две проблемы по адресу<ul><li>Свободное место, с которым размер жестким диском на основе современных и SSD хранилище на основе не имеет значения для большинства сред AD.</li> <li>Операций ввода-вывода (IO), доступных — во многих средах, это часто не уделяют должного внимания. Очень важно оценить только среды, но когда не достаточно ОЗУ для загрузки всей базы данных NTDS в памяти.</li></ul><li>Хранилище может быть непростой проблемой и необходимо привлечь опыт поставщика оборудования для определения правильного размера. Особенно в более сложных сценариев, таких как сценарии iSCSI, SAN и NAS. Тем не менее в общем случае стоимость гигабайта хранилища чаще всего в прямой противоречие, чтобы затраты на операции ввода-ВЫВОДА:<ul><li>RAID 5 требует меньше затрат за гигабайт, чем Raid 1, но Raid 1 требует меньше затрат на операции ввода-ВЫВОДА</li><li>На основе вращения жестких дисков имеют сократить расходы на каждый гигабайт, но SSDs влечет меньшие затраты на операции ввода-ВЫВОДА</li></ul><li>После перезагрузки компьютера или службы доменных служб Active Directory расширенного обработчика хранилищ (ESE) кэш пуст, и производительность будет привязан хотя warms кэша диска.</li><li>В большинстве сред AD считывается с большим объемом операций ввода-вывода в шаблоне случайных к дискам, Инверсия основное преимущество кэширования и чтение стратегии оптимизации.  Кроме того в AD имеется способом большего размера кэша в памяти, чем кэширует большинство системы хранения.</li></ul>
|ОЗУ|<ul><li>Размер базы данных</li><li>Базовая операционная система рекомендаций</li><li>Сторонние приложения</li></ul>|<ul><li>Хранилище — самые медленные компонента на компьютере. Чем больше, может быть постоянно находятся в оперативной памяти, тем менее бывает необходимо перейти на диск.</li><li>Обеспечить достаточный объем оперативной памяти, выделяемый для хранения операционной системы, агенты (антивирусными программами, резервное копирование, мониторинг), базы данных NTDS и роста.</li><li>Для сред, где максимального объема ОЗУ не стоимость эффективно (например, расположения вспомогательной) или не представляется возможной (DIT слишком велик), ссылка, в разделе хранилища, чтобы убедиться, что область хранения соответствующий размер.</li></ul>|
|Network|<ul><li>«Сетевой интерфейс (\*) \Bytes, полученных за секунду»</li><li>«Сетевой интерфейс (\*) \Bytes, отправленных за секунду»|<ul><li>Вообще говоря трафик, отправленный с контроллера домена значительно превышает трафик, отправленный на Контроллере домена.</li><li>Как полный дуплекс коммутируемой Ethernet-подключение, входящий и исходящий сетевой трафик размеры должны соответствовать независимо друг от друга.</li><li>Консолидировать контроллеров домена увеличит объем пропускной способности, используемый для отправки ответов обратно на клиентские запросы для каждого контроллера домена, но будет достаточно близко к линейной для узла в целом.</li><li>Если удаление расположения вспомогательной контроллеров домена, не забудьте добавить пропускную способность для вспомогательной контроллера домена в центр контроллеров домена, а также, можно использовать для оценки, какой объем трафика глобальной сети будет.</li></ul>|
|ЦП«Логический диск ( *\<диск для базы данных NTDS\>* ) \Avg чтения с диска»descripti«Process(lsass)\\"загруженности процессора»tors to consider during capacity planning for AD DS.
ms.prod: windows-server-threshold
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: v-tea; kenbrunf
author: Teresa-Motiv
ms.date: 7/3/2019
---

# Capacity planning for Active Directory Domain Services

This topic is originally written by Ken Brumfield, Senior Premier Field Engineer at Microsoft, and provides recommendations for capacity planning for Active Directory Domain Services (AD DS).

## Goals of capacity planning

Capacity planning is not the same as troubleshooting performance incidents. They are closely related, but quite different. The goals of capacity planning are:  

- Properly implement and operate an environment 
- Minimize the time spent troubleshooting performance issues.  
  
In capacity planning, an organization might have a baseline target of 40% processor utilization during peak periods in order to meet client performance requirements and accommodate the time necessary to upgrade the hardware in the datacenter. Whereas, to be notified of abnormal performance incidents, a monitoring alert threshold might be set at 90% over a 5 minute interval.

The difference is that when a capacity management threshold is continually exceeded (a one-time event is not a concern), adding capacity (that is, adding in more or faster processors) would be a solution or scaling the service across multiple servers would be a solution. Performance alert thresholds indicate that client experience is currently suffering and immediate steps are needed to address the issue.

As an analogy: capacity management is about preventing a car accident (defensive driving, making sure the brakes are working properly, and so on) whereas performance troubleshooting is what the police, fire department, and emergency medical professionals do after an accident. This is about “defensive driving,” Active Directory-style.

Over the last several years, capacity planning guidance for scale-up systems has changed dramatically. The following changes in system architectures have challenged fundamental assumptions about designing and scaling a service:

- 64-bit server platforms  
- Virtualization  
- Increased attention to power consumption  
- SSD storage  
- Cloud scenarios  

Additionally, the approach is shifting from a server-based capacity planning exercise to a service-based capacity planning exercise. Active Directory Domain Services (AD DS), a mature distributed service that many Microsoft and third-party products use as a backend, becomes one the most critical products to plan correctly to ensure the necessary capacity for other applications to run.

### Baseline requirements for capacity planning guidance

Throughout this article, the following baseline requirements are expected:

- Readers have read and are familiar with [Performance Tuning Guidelines for Windows Server 2012 R2](https://docs.microsoft.com/previous-versions//dn529133(v=vs.85)).
- The Windows Server platform is an x64 based architecture. But even if your Active Directory environment is installed on Windows Server 2003 x86 (now beyond the end of the support lifecycle) and has a directory information tree (DIT) that is less 1.5 GB in size and that can easily be held in memory, the guidelines from this article are still applicable.
- Capacity planning is a continuous process and you should regularly review how well the environment is meeting expectations.
- Optimization will occur over multiple hardware lifecycles as hardware costs change. For example, memory becomes cheaper, the cost per core decreases, or the price of different storage options change.
- Plan for the peak busy period of the day. It is recommended to look at this in either 30 minute or hour intervals. Anything greater may hide the actual peaks and anything less may be distorted by “transient spikes.”
- Plan for growth over the course of the hardware lifecycle for the enterprise. This may include a strategy of upgrading or adding hardware in a staggered fashion, or a complete refresh every three to five years. Each will require a “guess” as how much the load on Active Directory will grow. Historical data, if collected, will help with this assessment. 
- Plan for fault tolerance. Once an estimate *N* is derived, plan for scenarios that include *N* &ndash; 1, *N* &ndash; 2, *N* &ndash; *x*.
  - Add in additional servers according to organizational need to ensure that the loss of a single or multiple servers does not exceed maximum peak capacity estimates.
  - Also consider that the growth plan and fault tolerance plan need to be integrated. For example, if one DC is required to support the load, but the estimate is that the load will be doubled in the next year and require two DCs total, there will not be enough capacity to support fault tolerance. The solution would be to start with three DCs. One could also plan to add the third DC after 3 or 6 months if budgets are tight.

    >[!NOTE]
    >Adding Active Directory-aware applications might have a noticeable impact on the DC load, whether the load is coming from the application servers or clients.

### Three-step process for the capacity planning cycle

In capacity planning, first decide what quality of service is needed. For example, a core datacenter supports a higher level of concurrency and requires more consistent experience for users and consuming applications, which requires greater attention to redundancy and minimizing system and infrastructure bottlenecks. In contrast, a satellite location with a handful of users does not need the same level of concurrency or fault tolerance. Thus, the satellite office might not need as much attention to optimizing the underlying hardware and infrastructure, which may lead to cost savings. All recommendations and guidance herein are for optimal performance, and can be selectively relaxed for scenarios with less demanding requirements.

The next question is: virtualized or physical? From a capacity planning perspective, there is no right or wrong answer; there is only a different set of variables to work with. Virtualization scenarios come down to one of two options:

- “Direct mapping” with one guest per host (where virtualization exists solely to abstract the physical hardware from the server)
- “Shared host”

Testing and production scenarios indicate that the “direct mapping” scenario can be treated identically to a physical host. “Shared host,” however, introduces a number of considerations spelled out in more detail later. The “shared host” scenario means that AD DS is also competing for resources, and there are penalties and tuning considerations for doing so.

With these considerations in mind, the capacity planning cycle is an iterative three-step process:

1. Measure the existing environment, determine where the system bottlenecks currently are, and get environmental basics necessary to plan the amount of capacity needed.
1. Determine the hardware needed according to the criteria outlined in step 1.
1. Monitor and validate that the infrastructure as implemented is operating within specifications. Some data collected in this step becomes the baseline for the next cycle of capacity planning.

### Applying the process

To optimize performance, ensure these major components are correctly selected and tuned to the application loads:

1. Memory
1. Network
1. Storage
1. Processor
1. Net Logon

The basic storage requirements of AD DS and the general behavior of well written client software allow environments with as many as 10,000 to 20,000 users to forego heavy investment in capacity planning with regards to physical hardware, as almost any modern server class system will handle the load. That said, the following table summarizes how to evaluate an existing environment in order to select the right hardware. Each component is analyzed in detail in subsequent sections to help AD DS administrators evaluate their infrastructure using baseline recommendations and environment-specific principals.

In general:

- Any sizing based on current data will only be accurate for the current environment.
- For any estimates, expect demand to grow over the lifecycle of the hardware.
- Determine whether to oversize today and grow into the larger environment, or add capacity over the lifecycle.
- For virtualization, all the same capacity planning principals and methodologies apply, except that the overhead of the virtualization needs to be added to anything domain related.
- Capacity planning, like anything that attempts to predict, is NOT an accurate science. Do not expect things to calculate perfectly and with 100% accuracy. The guidance here is the leanest recommendation; add in capacity for additional safety and continuously validate that the environment remains on target.

### Data collection summary tables

#### New environment

| Component | Estimates |
|-|-|
|Storage/Database Size|40 KB to 60 KB for each user|
|RAM|Database Size<br />Base operating system recommendations<br />Third-party applications|
|Network|1 GB|
|CPU|1000 concurrent users for each core|

#### High-level evaluation criteria

| Component | Evaluation criteria | Planning considerations |
|-|-|-|
|Storage/Database size|The section entitled “To activate logging of disk space that is freed by defragmentation” in [Storage Limits](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/cc961769(v=technet.10))| |
|Storage/ Database performance|<ul><li>"LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Read," "LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Write," "LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Transfer"</li><li>"LogicalDisk(*\<NTDS Database Drive\>*)\Reads/sec," "LogicalDisk(*\<NTDS Database Drive\>*)\Writes/sec," "LogicalDisk(*\<NTDS Database Drive\>*)\Transfers/sec"</li></ul>|<ul><li>Storage has two concerns to address<ul><li>Space available, which with the size of today’s spindle based and SSD based storage is irrelevant for most AD environments.</li> <li>Input/Output (IO) Operations available – In many environments, this is often overlooked. But it is important to evaluate only environments where there is not enough RAM to load the entire NTDS Database into memory.</li></ul><li>Storage can be a complex topic and should involve hardware vendor expertise for proper sizing. Particularly with more complex scenarios such as SAN, NAS, and iSCSI scenarios. However, in general, cost per Gigabyte of storage is often in direct opposition to cost per IO:<ul><li>RAID 5 has lower cost per Gigabyte than Raid 1, but Raid 1 has lower cost per IO</li><li>Spindle-based hard drives have lower cost per Gigabyte, but SSDs have a lower cost per IO</li></ul><li>After a restart of the computer or the Active Directory Domain Services service, the Extensible Storage Engine (ESE) cache is empty and performance will be disk bound while the cache warms.</li><li>In most environments AD is read intensive I/O in a random pattern to disks, negating much of the benefit of caching and read optimization strategies.  Plus, AD has a way larger cache in memory than most storage system caches.</li></ul>
|RAM|<ul><li>Database size</li><li>Base operating system recommendations</li><li>Third-party applications</li></ul>|<ul><li>Storage is the slowest component in a computer. The more that can be resident in RAM, the less it is necessary to go to disk.</li><li>Ensure enough RAM is allocated to store the operating system, Agents (antivirus, backup, monitoring), NTDS Database and growth over time.</li><li>For environments where maximizing the amount of RAM is not cost effective (such as a satellite locations) or not feasible (DIT is too large), reference the Storage section to ensure that storage is properly sized.</li></ul>|
|Network|<ul><li>“Network Interface(\*)\Bytes Received/sec”</li><li>“Network Interface(\*)\Bytes Sent/sec”|<ul><li>In general, traffic sent from a DC far exceeds traffic sent to a DC.</li><li>As a switched Ethernet connection is full-duplex, inbound and outbound network traffic need to be sized independently.</li><li>Consolidating the number of DCs will increase the amount of bandwidth used to send responses back to client requests for each DC, but will be close enough to linear for the site as a whole.</li><li>If removing satellite location DCs, don’t forget to add the bandwidth for the satellite DC into the hub DCs as well as use that to evaluate how much WAN traffic there will be.</li></ul>|
|CPU|<ul><li>“Logical Disk(*\<NTDS Database Drive\>*)\Avg Disk sec/Read”</li><li>“Process(lsass)\\% Processor Time”</li></ul>|<ul><li>После устранения хранилища как узкое место, адрес объема вычислительной мощности, которые требуется.</li><li>Не вполне линейной, число ядер процессора, использованных на всех серверах в пределах определенной области (например, на сайте) можно использовать для оценки, сколько процессоров необходимы для поддержки загрузки всего клиента. Добавление минимально необходимой для поддержания текущего уровня службы во всех системах, в области.</li><li>Изменения в скорость процессора, включая управление питанием связанные изменения, влияние чисел, производным от текущей среды. Как правило вы не сможете точно оценить, как переход от 2,5 ГГц для процессора с частотой 3 ГГц сократит число ЦП при необходимости.</li></ul>|
|NetLogon|<ul><li>«Netlogon (\*) получает \Semaphore»</li><li>«Netlogon (\*) \Semaphore время ожидания»</li><li>«Netlogon (\*) времени удержания \Average семафора»</li></ul>|<ul><li>Безопасный канал Net Logon/MaxConcurrentAPI влияет только на сред с помощью проверки подлинности NTLM и/или проверка PAC. Проверка PAC включен по умолчанию в версиях операционной системы до Windows Server 2008. Это параметр, клиента, поэтому контроллеры домена будут затронуты, пока это будет отключен для всех клиентских систем.</li><li>Среды с помощью проверки подлинности значительные перекрестного доверия, включая отношения доверия внутри леса, имеют большему риску в противном случае надлежащего размера.</li><li>Консолидации сервера увеличит параллелизм доверием перекрестной проверки подлинности.</li><li>Скачков должна быть обеспечено, такие как сбой кластера географическими регионами, как пользователи повторно пройти проверку подлинности массе нового узла кластера.</li><li>Отдельные клиентские системы (например, кластер) может потребоваться настройка слишком.</li></ul>|

## <a name="planning"></a>Планирование

В течение длительного времени сообщества рекомендации по регулированию AD DS заключался в «put в количество памяти, так как размер базы данных». В большинстве случаев рекомендуется все, что большинство сред необходимости думать о. Но экосистему использует AD DS стало намного больше, как сами, среды AD DS, с момента своего появления в 1999 г. Несмотря на то что увеличение вычислительной мощности, а также переход с x86 архитектуры для архитектур сделала очевидная аспекты изменения размера для производительности, не имеющие отношения к клиентам, работающим с AD DS на физическом оборудовании, увеличение размера виртуализации большого набора имеет x64 заново введено вопросы настройки для широкой публики.

Следующие рекомендации по таким образом — о том, как определить и спланировать потребности Active Directory как услуга, независимо от того, развернут ли он в физическое устройство, набор виртуальных и физических или исключительно виртуализированных сценарий. Таким образом, мы будет разбить оценки для каждого из четырех основных компонентов: хранилища, памяти, сети и процессора. Иными словами Чтобы добиться максимальной производительности в AD DS, целью является получение как можно ближе к процессор привязанного максимально.

## <a name="ram"></a>ОЗУ

Просто, тем более, могут быть кэшированы в оперативной памяти тем менее, необходимо вернуться на диск. Чтобы максимально увеличить масштабируемость сервера минимальный объем ОЗУ сумму текущий размер базы данных, общий размер SYSVOL, операционной системы рекомендуется сумма, а также рекомендациям производителя для агентов (антивирусные, мониторинга, резервного копирования и т. д. ). Дополнительного должны быть добавлены для роста в течение времени существования сервера. Это будет экологически Субъективная основаны на оценках роста базы данных, в зависимости от изменений в среде.

Для сред, где максимального объема ОЗУ не стоимость эффективно (например, расположения вспомогательной) или не представляется возможной (DIT слишком велик), ссылка, должным образом разработана в разделе хранилища, чтобы убедиться, что область хранения.

Следствие, выводимый в контексте общий размер памяти изменение размера файла подкачки. В том же контексте, все остальные связанные памяти, цель — минимизировать будет значительно медленнее диска. Таким образом вопрос должен составлять от, «как файл подкачки изменения размеров?» для «Для разбиения на страницы приходилось объем ОЗУ?» Ответ на последний вопрос, описанные в оставшейся части этого раздела. При этом основная часть этой дискуссии изменения размера файла подкачки для области операционной системы, общие рекомендации и необходимость настройки системы для дампы памяти, которые не связаны с AD DS производительности.

### <a name="evaluating"></a>Оценка

Объем ОЗУ, которыми контроллером домена (DC) — это действительно сложная задача, требующая по следующим причинам:

- Так как LSASS удалит условиях нехватки памяти, искусственно deflating необходимость требуется высокая вероятность появления ошибки при попытке использовать существующую систему, чтобы оценить объем ОЗУ.
- Субъективная факт, что отдельного контроллера домена, должен кэшировать, что такое «интересный» для своих клиентов. Это означает, что данные, необходимые для кэширования на Контроллере домена в сайте с сервером Exchange будет сильно отличается от данных, который должен кэшироваться на Контроллере домена, только проверяет подлинность пользователей.
- Трудовых ресурсов для оценки ОЗУ для каждого контроллера домена, на индивидуальном-неприемлемо высоки и изменяется во время изменения среды.
- Критерии за рекомендации помогут для принятия обоснованных решений: 
- Чем больше, могут быть кэшированы в оперативной памяти, тем менее бывает необходимо перейти на диск. 
- Хранилища — это, несомненно, самые медленные компонент компьютера. Доступ к данным на основе жестким диском и SSD носителей, составляет примерно 1 000 000 x медленнее, чем доступ к данным в оперативной памяти.

Таким образом Чтобы максимизировать масштабируемость сервера, минимальный объем ОЗУ сумму текущий размер базы данных, общий размер SYSVOL, операционной системы рекомендуется сумма, а также рекомендациям производителя для агентов (антивирусными программами, мониторинга, резервного копирования, и так далее). Добавьте дополнительные суммы для роста в течение времени существования сервера. Это будет экологически Субъективная основаны на оценках роста базы данных. Тем не менее вспомогательных местоположений с небольшой набор конечных пользователей, эти требования можно настроить, так как эти узлы не понадобится кэша образном для обслуживания большая часть запросов.

Для сред, где максимального объема ОЗУ не стоимость эффективно (например, расположения вспомогательной) или не представляется возможной (DIT слишком велик), ссылка, в разделе хранилища, чтобы убедиться, что область хранения соответствующий размер.

> [!NOTE]
> Следствие во время изменения размера памяти изменение размера файла подкачки. Так как целью является свести к минимуму, будут значительно медленнее, диск, вопрос перемещается от «как файл подкачки изменения размеров?» для «Для разбиения на страницы приходилось объем ОЗУ?» Ответ на последний вопрос, описанные в оставшейся части этого раздела. При этом основная часть этой дискуссии изменения размера файла подкачки для области операционной системы, общие рекомендации и необходимость настройки системы для дампы памяти, которые не связаны с AD DS производительности.

### <a name="virtualization-considerations-for-ram"></a>Рекомендации по виртуализации для ОЗУ

Избегайте чрезмерной фиксации памяти на узле. Основная задача behind оптимизации объем ОЗУ является свести к минимуму время, затраченное на переход на диск. В случаях виртуализации концепцию фиксации чрезмерной памяти существует, где выделяется больше оперативной памяти для гостей, то существует на физическом компьютере. Само по себе это не проблема. Он становится проблемой, если общий объем памяти, активно используемой всеми гостевыми компьютерами превышает объем оперативной памяти на узле и базовым узлом начинает разбиения на страницы. Производительность становится к диску в случаях, когда контроллер домена будет NTDS.dit для получения данных, или контроллера домена требуется файл подкачки для получения данных или узле будет диска для получения данных, которое считает гостевой ОС в ОЗУ.

### <a name="calculation-summary-example"></a>Пример сводки вычисления

|Component|Оценка памяти (например)|
|-|-|
|Базовая операционная система Рекомендуемый объем ОЗУ (Windows Server 2008)|2 ГБ|
|Внутренние задачи LSASS|200 МБ|
|Агент мониторинга|100 МБ|
|Антивирусная программа|100 МБ|
|Базы данных (глобальный каталог)|8,5 ГБ действительно код|
|Подкладка для резервного копирования запустить, администраторы могут войти в систему без влияния|1 ГБ|
|Total (Всего)|12 ГБ|

**Рекомендуется: 16 ГБ**

Со временем можно сделать предположение, дополнительные данные будут добавлены в базу данных и сервер, вероятно, находится в рабочей среде для 3-5 лет. Исходя из оценки роста 33%, 16 ГБ бы разумным объемом ОЗУ для размещения в физическом сервере. На виртуальной машине учитывая простота, с помощью которого можно изменить параметры и оперативной памяти могут добавляться к виртуальной Машине, начиная с 12 ГБ с планом для мониторинга и обновления в будущем оправдано.

## <a name="network"></a>Network

### <a name="evaluating"></a>Оценка
В этом разделе меньше об оценке требований относительно трафик репликации, который ориентирован на трафик, проходящий через глобальную сеть и тщательно рассматривается в [трафика репликации Active Directory](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742457(v=technet.10)), а не об оценке всего пропускная способность, пропускная способность сети требуется, включают в себя клиентские запросы, Групповая политика приложений и т. д. Для существующих сред, это можно собирать с помощью счетчиков производительности «сетевой интерфейс (\*) \Bytes получено/сек» и «сетевой интерфейс (\*) \Bytes отправлено/сек.» Интервала выборки для счетчиков сетевого интерфейса в 15, 30 или 60 минут. Что-либо меньше обычно будет слишком volatile для точные показатели; ничего больше будет сгладить ежедневной считывает чрезмерно.

> [!NOTE]
> Как правило большая часть сетевого трафика на Контроллере домена является исходящим, как контроллер домена отвечает на запросы клиентов. Это причина фокус на исходящий трафик, хотя рекомендуется также оценить каждой среды для входящего трафика. Тех же подходов можно использовать для решения и ознакомьтесь с требованиями к входящего сетевого трафика. Дополнительные сведения см. в статье базы знаний [929851 службы: По умолчанию динамический диапазон портов для TCP/IP был изменен в Windows Vista и Windows Server 2008](http://support.microsoft.com/kb/929851).

### <a name="bandwidth-needs"></a>Требования к пропускной способности

Планирование масштабируемости сети покрывает две отдельных категории: объем трафика и ЦП загрузки из сетевого трафика. Каждый из этих сценариев довольно прост, по сравнению с некоторые другие разделы этой статьи.

Оценить объем трафика должен поддерживаться, существует две уникальных категории Планирование емкости для AD DS с точки зрения сетевого трафика. Во-первых, трафик репликации, который проходит по между контроллерами домена и тщательно рассматривается в справочном руководстве [трафика репликации Active Directory](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742457(v=technet.10)) и по-прежнему актуальны для текущих версий AD DS. Второй — трафик внутрисайтовой клиентом и сервером. Один из более простых ситуациях для планирования, внутрисайтовой трафик преимущественно принимает небольших запросов от клиентов относительно больших объемов данных, отправляется обратно клиенту. 100 МБ, обычно подходить в средах, не более 5000 пользователей на каждом сервере, на узле. Сетевой адаптер 1 ГБ и на стороне приема масштабирование (RSS) поддержки рекомендуется использовать для любым более 5000 пользователей. Чтобы проверить этот сценарий, особенно в случае консолидации серверов, взгляните на сетевой интерфейс (\*) \Bytes/sec на все контроллеры домена в сайте, добавьте их друг с другом и деления на целевое количество контроллеров домена, чтобы убедиться, что существует имеет необходимую емкость. Для этого проще для использования в представлении «С областями с накоплением» в Windows монитор надежности и производительности (прежнее название Perfmon), убедившись, что все счетчики, масштабировать же.

Рассмотрим следующий пример (также известный как очень, очень сложный способ проверить, что общее правило применяется к определенной среде). Предполагается следующее:

- Целью является уменьшить занимаемое место для как можно меньшее число серверов, максимально. В идеале, один сервер будет нести нагрузки и развертывании дополнительного сервера для обеспечения избыточности (*N* + 1 сценарий). 
- В этом случае текущий сетевой адаптер поддерживает только 100 МБ и коммутируемых средой.  
  Использование пропускной способности сети максимальное целевое составляет 60% в сценарии N (потеря контроллера домена).
- Каждый сервер имеет приблизительно 10 000 клиентов, подключенных к нему.

Знания, полученные из данных в диаграмме (сетевой интерфейс (\*) \Bytes отправлено/сек):

1. Рабочий день начинается, представляют собой связующее около 5:30 и ураганный ветер вниз в 7:00.
1. Максимальная нагрузка периода наибольшей загрузки — с 8:00 8:15:00, с более чем 25 Отправлено байт/с на самых загруженных контроллере домена.  
   > [!NOTE]
   > Все данные производительности журнала. Поэтому пиковой точки данных в 8:15 указывает нагрузки от 8:00 до 8:15.
1. Есть пиковые нагрузки до 4:00 AM, с более чем 20 отправлено байт/с на самых загруженных контроллере домена, который может указывать либо нагрузки из разных часовых поясах или фоновое действие инфраструктуры, такие как резервное копирование. Поскольку максимальных в 8:00 превышает это действие, это не относится.
1. Существует пять контроллеров домена на сайте.
1. Максимальная нагрузка — около 5,5 МБ/с на контроллере домена, который представляет 44% подключения 100 МБ. Используя эти данные, он может быть оценена — что общая пропускная способность, необходимого между 8:00 до 8:15:00 28 МБ в секунду.
   >[!NOTE]
   >Будьте осторожны с тот факт, что сетевой интерфейс отправки и получения счетчики указываются в байтах и пропускной способности сети измеряется в битах. 100 МБ &divide; 8 = 12,5 МБ, 1 ГБ &divide; 8 = 128 МБ.
  
Выводы:

1. N + 1 уровень отказоустойчивости на 60% целевое использование соответствует ли этот текущей среды. Перевод одной системы в автономный режим будут сдвигаться пропускная способность каждого сервера из около 5,5 МБ/с (44%) около 7 МБ в секунду (56%).
1. Исходя из ранее указанной цели объединения к одному серверу, это превышает максимальное целевое использование и теоретически возможно использование подключения 100 МБ.
1. С помощью подключения 1 ГБ, это будет представлять 22% от общей емкости.
1. Обычной производственных условиях в *N* + 1 сценарий клиента относительно равномерно распределяется нагрузка на около 14 МБ/с на сервере или 11% от общей емкости.
1. Чтобы убедиться, что емкость составляет адекватный во время недоступности контроллера домена, обычной работы целевых объектов для сервера будет приблизительно 30% сеть 38 МБ в секунду на один сервер или использования. Целей отработки отказа будет 60% интенсивность использования глобальной сети или 72 МБ/с на один сервер.  
  
Короче говоря окончательного развертывания систем должен иметь сетевой адаптер 1 ГБ и подключить к сетевой инфраструктуре, которая будет поддерживать эти нагрузки. Дополнительные заметки, что учитывая требуемый объем сетевом трафике, созданном, нагрузку на ЦП из сетевых подключений может оказать существенное влияние и ограничения максимальной масштабируемости службы AD DS. Аналогичным образом можно использовать для оценки входящих сообщений на контроллер домена. Но учитывая predominance исходящего трафика по отношению к входящий трафик, академического упражнения для большинства сред. Обеспечение аппаратную поддержку RSS важно в средах с более чем 5000 пользователей на каждом сервере. Для сценариев с большим объемом сетевого трафика балансировку нагрузки прерываний может быть узким местом. Это можно обнаружить, процессор (\*)\% времени прерываний, неравномерно распределенный между несколькими ЦП. RSS включена сетевых адаптеров может устранить это ограничение и повысить масштабируемость.

> [!NOTE]
> Аналогичный подход можно использовать для оценки необходимости дополнительной емкости, когда консолидация центров обработки данных, или вывода из эксплуатации контроллера домена в расположение вспомогательной. Просто собрать входящего и исходящего трафика для клиентов, которые будут объем трафика, будет присутствовать по ГЛОБАЛЬНОЙ сети.  
>  
> В некоторых случаях могут возникнуть больше трафика, чем ожидается, потому что трафика занимает больше времени, например при проверке сертификата не соответствует ограниченное время ожидания глобальной сети. По этой причине изменения размера глобальной сети и об использовании должны быть итеративный текущий процесс.

### <a name="virtualization-considerations-for-network-bandwidth"></a>Рекомендации по виртуализации для пропускной способности сети

Это легко сделать рекомендации для физического сервера: 1 ГБ для серверов, поддерживающих более 5000 пользователей. После несколько гостевых начать совместное использование базовой инфраструктуры виртуального коммутатора, необходимо гарантировать, что узел имеет достаточно полосы пропускания для поддержки всех гостей в системе и следовательно, требует дополнительных жесткости уделить особое внимание. Это всего лишь расширением обеспечения сетевой инфраструктуры в хост-компьютере. Это независимо от того, выполняется ли сети идет в комплекте с контроллера домена под управлением гостевой виртуальной машины на узле с помощью сетевого трафика, идущие через виртуальный коммутатор, а напрямую подключены к физическому коммутатору. Виртуальный коммутатор является только один компонент дополнительные где должно поддерживать объем данных, передаваемых исходящей связи. Таким образом физический сетевой адаптер физического узла, связанного с параметром должен быть поддерживать нагрузки контроллера домена, а также других гостей, совместного использования виртуальный коммутатор, подключенный к физическому сетевому адаптеру.

### <a name="calculation-summary-example"></a>Пример сводки вычисления

|Система|Пиковая пропускная способность|
|-|-|
КОНТРОЛЛЕР ДОМЕНА 1|6.5 МБ/с|
2 КОНТРОЛЛЕРА ДОМЕНА|6,25 МБ/с|
|DC 3|6,25 МБ/с|
|КОНТРОЛЛЕР ДОМЕНА 4|5,75 МБ/с|
|КОНТРОЛЛЕР ДОМЕНА 5|4,75 МБ/с|
|Total (Всего)|28,5 МБ/с|

**Рекомендуется: 72 МБ в секунду** (28.5 МБ в секунду, разделенное на 40%)

|Количество систем|Общая пропускная способность (выше)|
|-|-|
|2|28,5 МБ/с|
|Итоговый нормальное поведение|28,5 &divide; 2 = подсистемы 14.25 МБ в секунду.|

Как всегда со временем предполагается можно сделать что клиентская нагрузка будет увеличиваться, и этот рост следует как можно лучше планировать для. Рекомендуемый объем планирование позволит Предполагаемый рост в сетевой трафик, 50%.

## <a name="storage"></a>Хранилище

Планирование хранилища составляет два компонента:

- Емкость, или размер при хранении
- Производительность

Значительную времени и документации расходуется на планированию емкости, оставляя производительности полностью часто упускают из виду. С текущего затраты на оборудование, в большинстве окружений не больших недостаточно, это фактически является проблемой, а также рекомендации по «put в количество памяти, так как размер базы данных» обычно охватывает rest, хотя он может быть избыточным средством для расположения вспомогательной в большего размера сред.

### <a name="sizing"></a>Изменения размера

#### <a name="evaluating-for-storage"></a>Вычисления для хранилища

По сравнению с 13 лет назад при появилась Active Directory, время, когда 4 ГБ и 9 ГБ диски были наиболее распространенные размеры дисков, определение размера для Active Directory не даже следует учитывать для всех, но наибольший сред. С наименьшей доступных жесткого диска размеры в диапазоне 180 ГБ, всю операционную систему, SYSVOL и NTDS.dit можно легко разместить на одном диске. Таким образом рекомендуется отказаться от больших вложений в этой области.

Только для рассмотрения рекомендуется убедиться в доступности, чтобы включить дефрагментации 110% от размера NTDS.dit. Кроме того должны быть доступны размещений расширения в течение жизненного цикла оборудования.

Рассмотрения первый и самый важный оценивает размер NTDS.dit и SYSVOL будет. Эти измерения приводит к sizing фиксированного диска и выделения памяти. Связи (относительно) низкую стоимость этих компонентов расчеты не должен быть строгой и точной. Материалы о том, как оценивать этот контент для существующих и новых сред можно найти в [хранения данных](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/cc961771(v=technet.10)) серию статей. В частности см. в следующих статьях:

- **Для существующих сред &ndash;**  разделе под названием «для того, чтобы включить ведение журнала, места на диске, который освобождается при дефрагментации» в статье [ограничения хранилища](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc961769(v=technet.10)).
- **Для новых сред &ndash;**  в статье, посвященной [рост оценки для Active Directory — пользователи и организационными подразделениями](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc961779(v=technet.10)).

  > [!NOTE]
  > Статьи основаны на оценках размер данных во время выпуска Active Directory в Windows 2000. Используйте размеры объектов, которые отражают фактический размер объектов в вашей среде.

При просмотре существующие среды с несколькими доменами, могут существовать варианты размеров базы данных. Это не так, используйте наименьший глобального каталога (GC) и размеров без глобального Каталога.  

Размер базы данных может изменяться от версии операционной системы. Контроллеры домена, что запустить более ранних операционных систем, таких как Windows Server 2003 имеет меньший размер базы данных, чем контроллера домена под управлением более поздней версии операционной системы, такие как Windows Server 2008 R2, особенно в том случае, если корзины таких Active Directory функции Bin или перемещение учетных данных включены.

> [!NOTE]  
  >
>- Для новых сред следует отметить, быть оценок в рост оценки для Active Directory — пользователи и организационными подразделениями потребляемых около 450 МБ пространства на 100 000 пользователей (в том же домене). Обратите внимание на то, что заполненными атрибутами может иметь огромное влияние на общую сумму. Для многих объектов будет заполнять атрибуты независимых производителей и продуктов Майкрософт, включая Microsoft Exchange Server и Lync. Рекомендуется использовать оценку на основе портфель продуктов в среде, но упражнения по подробным описанием out математические и проверка на наличие точные оценки для всех, но наибольший сред могут стоить фактически значительное время и усилия.
>- Убедитесь, что дефрагментации 110% от NTDS.dit, размер доступен как свободного места, чтобы включить в автономном режиме и спланировать рост за год трех до пяти существования оборудования. Как удешевление хранения данных является, оценка хранения на 300% размера дерева КАТАЛОГОВ как выделением безопасна учесть рост инфраструктуры и потенциальную необходимость автономной дефрагментации.

#### <a name="virtualization-considerations-for-storage"></a>Рекомендации по виртуализации для хранилища

В сценарии, где несколько файлов виртуального жесткого диска (VHD) выделенных на одном томе используйте фиксированный размер диска, по крайней мере 210% (100% DIT + 110% свободного пространства) размера дерева каталогов для убедитесь в наличии достаточного пространства зарезервированные.  

#### <a name="calculation-summary-example"></a>Пример сводки вычисления

|Данные, собранные на этапе испытаний| |
|-|-|
|Размер NTDS.dit|35 ГБ ИСХОДЯЩЕГО ТРАФИКА|
|Модификатор, чтобы разрешить для автономной дефрагментации|2.1|
|Необходимая для его хранения|73.5 ГБ|

> [!NOTE]
> Это хранилище при необходимости является дополнением к пространства, необходимого для SYSVOL, операционной системы, файл подкачки, временные файлы, локальные кэшированные данные (например, файлы установщика) и приложений.

### <a name="storage-performance"></a>Производительность хранилища

#### <a name="evaluating-performance-of-storage"></a>Оценка производительности хранилища

Самые медленные компонентом в рамках любого компьютера хранилище может иметь наибольшее отрицательное влияние на взаимодействие с клиентом. Для этих больших сред достаточно для которого рекомендации по выбору размера ОЗУ вам не подходят, последствия пропуску планированию хранилища для повышения производительности может быть иметь серьезные последствия.  Кроме того сложностей и разновидности дополнительные технологии хранения увеличить риск сбоя как полезные сценарии ограничен релевантность длительные устоявшиеся, советы и рекомендации из «put операционной системы, журналы и базы данных» на отдельных физических дисках.  Это обусловлено рекомендуется длительные устоявшиеся основана на предположении, что «диск» выделенный вращения и это позволило ввода-вывода изолировать.  Этого предположения, которые делают это значение true, которые больше не нужны, с появлением:

- Новые типы хранилища и сценариях виртуализированной и общего хранилища
- Общие шпинделей в сети хранения данных (SAN)
- Файл виртуального жесткого диска на SAN или сетевое хранилище
- Твердотельные накопители
- Многоуровневое хранилище архитектуры (т. е. хранилище уровня SSD кэширование хранилище большего размера на основе жестким диском)

Короче говоря конечной целью все усилия производительности хранилища, независимо от базовой архитектуры хранилища и разработки, необходимо, чтобы необходимый объем операций ввода-вывода в секунду (IOPS), доступны и что эти операции ввода-ВЫВОДА происходят в течение допустимого промежутка времени . В этом разделе описывается, как оценить, какие требования AD DS базового хранилища для обеспечения решений для хранения предназначены должным образом.  Учитывая разнообразие периодов современных технологий хранения, лучше всего работают с такими поставщиками хранилища, чтобы обеспечить достаточно операций ввода-ВЫВОДА.  Для этих сценариев с помощью локального хранилища ссылаться на приложении В основы в том, как разрабатывать сценарии традиционного локального хранилища.  Этот участников применимы для более сложных уровни хранилища и также поможет в диалоговом окне с поставщиками, поддержка решений серверной части хранилища.

- Учитывая широкий спектр варианты хранения, доступные, рекомендуется задействовать опыт группы поддержки оборудования или поставщиков, чтобы убедиться, что конкретное решение соответствует требованиям AD DS. Следующие номера — это сведения, которое предоставляется специалистам хранилища.

Для сред, где базы данных слишком велик для хранения в оперативной памяти используйте счетчики производительности, чтобы определить, какое количество операций ввода-вывода должно поддерживаться:

- Логический диск (\*) \Avg чтения с диска (например, в том случае, если NTDS.dit хранится на диске D: / диск, полный путь будет иметь логический диск (D:) \Avg Disk sec/Read)
- Логический диск (\*) \Avg сек время записи на диск
- Логический диск (\*) \Avg диску (сек)
- Логический диск (\*) \Reads/sec
- Логический диск (\*) \Writes/sec
- Логический диск (\*) \Transfers/sec

Они должны считываться в 15, 30/60-минутные интервалы в измерении производительности требования текущей среды.

#### <a name="evaluating-the-results"></a>Оценка результатов

> [!NOTE]
> Фокус установлен на операции чтения из базы данных, так как это обычно компонента самых требовательных, ту же логику, которая может применяться к записи в файл журнала, подставляя логический диск ( *\<журнала NTDS\>* ) \Avg сек время записи на диск и логический диск ( *\<журнала NTDS\>* ) \Writes/sec):
>  
> - Логический диск ( *\<NTDS\>* ) \Avg Disk sec/Read указывает ли текущий режим хранения достаточного размера.  Если результаты примерно равное на время доступа к диску для типа диска, логический диск ( *\<NTDS\>* ) \Reads/sec имеет допустимую меру.  Проверьте спецификации изготовителя для хранения на серверной стороне, но хорошо диапазоны для логический диск ( *\<NTDS\>* ) будет примерно соответствовать \Avg чтения с диска:
>   - 7200 – 12,5 9 в миллисекундах (мс)
>   - 10 000 – 6 – 10 мс
>   - 15 000 – 4 – 6 мс  
>   - SSD — 1 – 3 мс  
>   - >[!NOTE]
>     >Рекомендации существует, о том, что хранилище производительность снижается по 15 мс до 20 мс (в зависимости от источника).  Разница между указанным выше значениям и другие руководства является приведенными выше значениями обычный рабочий диапазон.  Рекомендации по для идентификации, когда взаимодействие с клиентом, значительно снижает и становится заметной устранению неполадок всех прочих рекомендаций.  Справочник по C приложение более подробно.
> - Логический диск ( *\<NTDS\>* ) \Reads/sec — это объем операций ввода-вывода, выполняемая в данный момент.
>   - Если логический диск ( *\<NTDS\>* ) \Avg Disk sec/Read находится в пределах оптимальный диапазон для серверного хранилища, логический диск ( *\<NTDS\>* ) \Reads/ сек можно непосредственно выбрать размер хранилища.
>   - Если логический диск ( *\<NTDS\>* ) \Avg чтения с диска не является оптимальной диапазона для хранения базы данных, дополнительных операций ввода-вывода по следующей формуле:
>     > (Логический диск ( *\<NTDS\>* ) \Avg Disk sec/Read) &divide; (физическом носителе на диске время доступа) &times; (логический диск ( *\<NTDS\>* ) \Avg disk sec/Read)

Замечания:

- Обратите внимание, что если сервер настроен с недостаточной объемом оперативной памяти, эти значения будут неточными для целей планирования.  Они будут ошибочно на высокой и по-прежнему может использоваться как худший случай сценария.
- Добавление/оптимизация ОЗУ специально и определят уменьшение объема операций ввода-вывода (логический диск ( *\<NTDS\>* ) \Reads/Sec.  Это означает, что может не быть настолько надежно, как изначально вычисляемые решение хранилища.  К сожалению ничего более точным, чем экологически зависит от загрузки клиента и общие рекомендации общего правила не может поступать.  Лучшим вариантом является изменение размера хранилища после оптимизации ОЗУ.

#### <a name="virtualization-considerations-for-performance"></a>Рекомендации по виртуализации для производительности

Как и все предыдущего обсуждения виртуализации, важно убедиться, что базовая инфраструктура общего может поддерживать нагрузки контроллера домена, а также другие ресурсы, с помощью базовой общий доступ к мультимедиа и все пути к нему. Это верно ли физический контроллер домена использует тот же базовый носитель на SAN, NAS или iSCSI инфраструктуры как другим серверам или приложениям, будь то Гость с транзитной доступ по сети SAN, NAS или iSCSI инфраструктуру, которая совместно использует Базовый носитель, или если Гость использует файл виртуального жесткого диска, который находится на локально общего мультимедийного содержимого или инфраструктуры SAN, NAS или iSCSI. Планирования упражнения не заменит живого убедившись, что носителя могут поддерживать общую нагрузку для всех объектов-получателей.

Кроме того с точки зрения гостевой как нет пути дополнительный код, который должен просматриваться, есть повлиять на производительность на необходимость выхода узла для доступа к памяти. Не удивительно, что тестирование производительности хранилища указывает, что виртуализация оказывает влияние на пропускную способность, которой субъективной загрузки процессора системы узла (см. приложение а. Условия изменения размера ЦП), очевидно, что которого зависит от ресурсов узла затребованы гостевой ОС. Это помогает реализовать виртуализации вопросы, касающиеся требований к обработке в виртуализированной сценарии (см. в разделе [рекомендации по виртуализации для обработки](#virtualization-considerations-for-processing)).

Как сделать это более сложный: существуют разнообразные разных вариантах хранения, доступные, имеющих влияние на производительность другой. Безопасный оценки, при переносе из физического в виртуальный используйте множителя 1,10 для настройки для разных вариантах хранения для виртуализированных гостевых систем в Hyper-V, например к серверу хранилища, адаптер SCSI или IDE. Изменения, которые должны быть выполнены при передаче между разными сценариями несущественны для ли оно является локальным, SAN, NAS или iSCSI.

#### <a name="calculation-summary-example"></a>Пример сводки вычисления

Определение объема ввода-вывода, необходимых для работоспособность системы при нормальных рабочих условиях:

- Логический диск ( *\<диск для базы данных NTDS\>* ) \Transfers/sec в период пиковой 15 минут периода 
- Чтобы определить объем операций ввода-вывода, необходимых для хранения, где превышена емкость базовое хранилище:
  >*Необходимые операции ввода-ВЫВОДА* = (логический диск ( *\<диск для базы данных NTDS\>* ) \Avg Disk sec/Read &divide; *\<предназначенных для чтения с диска Avg\>* ) &times; Логический диск ( *\<диск для базы данных NTDS\>* ) \Read/sec

|Счетчик|Значение|
|-|-|
|Фактический логический диск ( *\<диск для базы данных NTDS\>* ) \Avg диску (сек)|.02 секунд (20 миллисекунд)|
|Целевой логический диск ( *\<диск для базы данных NTDS\>* ) \Avg диску (сек)|.01 секунд|
|Множитель для изменения доступных операций ввода-ВЫВОДА|0.02 &divide; 0.01 = 2|  
  
|Значение|Значение|
|-|-|
|Логический диск ( *\<диск для базы данных NTDS\>* ) \Transfers/sec|400|
|Множитель для изменения доступных операций ввода-ВЫВОДА|2|
|Всего операций ввода-ВЫВОДА, необходимые во время периода наибольшей загрузки|800|

Чтобы определить скорость, с которой кэша по замыслу быть подготовлены:

- Определите максимальное время допустимо, чтобы подготовить кэш. Это интервал времени, может потребоваться загрузить всю базу данных с диска, или для сценариев, где не удается загрузить всю базу данных в оперативной памяти, это будет максимальное время для заполнения оперативной памяти.
- Определите размер базы данных, за исключением пробелов.  Дополнительные сведения см. в разделе [вычисления для хранилища](#evaluating-for-storage).  
- Деление размера базы данных на 8 КБ; которые будут total IOs, необходимо загрузить базу данных.
- Разделите total IOs количество секунд в определенный промежуток времени.

Обратите внимание на то, что скорость, вычисляются, пока точные, не будут точно так, как ранее загруженную страниц вытесняются в том случае, если ESE не должна иметь размер основного кэша и AD DS, по умолчанию используется размер переменной кэша.

|Доступ к данным для сбора|Значения
|-|-|
|Максимальное время, допустимо для "теплые"|10 минут (600 секунд)
|Размер базы данных|2 ГБ|  
  
|Этап вычисления|Формулы|Результат|
|-|-|-|
|Рассчитайте размер базы данных на страницах|(2 ГБ &times; 1024 &times; 1024) = *размер базы данных в КБ*|2 097 152 КБ|
|Вычисления числа страниц в базе данных|2 097 152 КБ &divide; 8 КБ = *количество страниц*|262 144 страниц|
|Вычислить операций ввода-ВЫВОДА, необходимые, чтобы полностью подготовить кэш|262 144 страниц &divide; = 600 секунд *необходимых операций ввода-ВЫВОДА*|437 ОПЕРАЦИЙ ВВОДА-ВЫВОДА|

## <a name="processing"></a>Processing

### <a name="evaluating-active-directory-processor-usage"></a>Оценке использования процессора Active Directory

Для большинства сред после хранения, оперативной памяти и сети правильно настроены как описано в разделе «Планирование» управление объем вычислительной мощности будут компонент, который заслуживает Наибольшее внимание. Существует две проблемы при оценке необходимости мощности ЦП.

- Ли они хорошо работающие в инфраструктуре общих служб приложения в среде, а также рассматривается в разделе «Отслеживание дорого и неэффективно запросы поиска» в статье Создание более эффективный Microsoft Active Работающих с каталогами приложений или отказа от использования SAM нижнего уровня вызывает вызовам LDAP.  
  
  В больших средах — причина, по которой это важно, что плохо закодированных приложений диск изменчивости в нагрузку на ЦП, «украсть» чрезмерное количество времени ЦП из других приложений, искусственно вести к потребности в мощности и неравномерно распределить нагрузку на контроллеры домена.  
- Как AD DS распределенной среде с помощью множества различных потенциальных клиентов, оценка расходов «одного клиента» — это экологически Субъективная из-за шаблонов использования и тип или количество приложений, использующих AD DS. Короче говоря подобно разделе работы с сетью, для широкого применимости, это лучше достижении с точки зрения вычисления общая емкость, необходимых в окружении.

Для существующих сред как изменение размера хранилища, которые обсуждались ранее, предполагается, что хранилище имеет размер теперь правильно, и таким образом данные, касающиеся нагрузки процессора является допустимым. Таким образом, важно, чтобы убедиться, что узкое место в системе не от производительности хранилища. Узкое место существует, и обработчик находится в состоянии ожидания, при состояний простоя, исчезнут после удаления узкое место.  Удаляются состояния ожидания процессора, по определению, так как он больше не нужно ожидать данных увеличивается ЦП. Таким образом, сбор данных счетчиков производительности «логический диск ( *\<диск для базы данных NTDS\>* ) \Avg Disk sec/Read» и «Process(lsass)\\% Processor Time». Данные в «Process(lsass)\\% Processor Time» будет небольшим Если «логический диск ( *\<диск для базы данных NTDS\>* ) \Avg Disk sec/Read» превышает 10 – 15 мс, в которой — это общие пороговое значение, Корпорация Майкрософт использует для устранения проблем с производительностью, связанных с хранилищем. Как и раньше рекомендуется обеспечить интервала выборки, 15, 30 или 60 минут. Что-либо меньше обычно будет слишком volatile для точные показатели; ничего больше будет сгладить ежедневной считывает чрезмерно.

### <a name="introduction"></a>Введение

Для планирования, планирование мощности для контроллеров домена, вычислительной мощности требуется максимального внимания и понимание. При планировании размера систем для обеспечения максимальной производительности, всегда есть это компонент, который является узким местом и в контроллер домена правильно размера это будет процессора.

Как и где анализируется запросу среды на основе узла разделе работы с сетью, то же необходимо сделать за вычислительные ресурсы, которые требуются. В отличие от разделе работы с сетью, где доступны сетевые технологии гораздо шире, чем обычные требования, внимание дополнительные изменения размера мощности ЦП.  В любой среде даже скромных ресурсов; остальное несколько тысяч одновременных пользователей можно поместить существенную нагрузку на ЦП.

К сожалению из-за огромных изменчивость клиентских приложений, использующих AD, общая оценка пользователей на один ЦП — прискорбно распространяется на все среды. В частности требования вычислений, распространяются профиль поведение и приложения пользователя. Таким образом каждая среда должна определяться по отдельности.

#### <a name="target-site-behavior-profile"></a>Целевой профиль поведение сайта

Как упоминалось ранее, при планировании емкости для всего узла, целью является целевой Дизайн с помощью *N* + 1 емкости разработки, так что для продолжения службы в приемлемых пределах позволит сбою одной системы в период пиковой уровень качества. Это означает, что в «*N*"сценарии нагрузки для всех полей должно быть меньше 100% (еще лучше с менее 80%) в периоды пиковой нагрузки.

Кроме того приложения и клиенты на сайте используются советы и рекомендации для обнаружения контроллеров домена (то есть с помощью [функция DsGetDcName](http://msdn.microsoft.com/en-us/library/windows/desktop/ms675983(v=vs.85).aspx)), клиенты должны быть относительно равномерно распределены с незначительными Переходные всплески из-за любое количество факторов.

В следующем примере выполняются следующие предположения:

- Каждый из пяти контроллеров домена на сайте имеет четыре ЦП.
- Общее целевой процент использования ЦП в рабочее время — 40% при нормальных рабочих условиях («*N* + 1») и 60% в противном случае («*N*«). Во время нерабочего времени, использования ЦП составляет 80%, так как программное обеспечение резервного копирования и другое обслуживание должны использовать все доступные ресурсы.

![Диаграмма использования ЦП](media/capacity-planning-considerations-cpu-chart.png)

Анализ данных в диаграмме (процессор Information(_Total)\% процессоров) для каждого из контроллеров домена:

- По большей части относительно равномерно распределяется нагрузка которого является то, что было бы ожидать, когда клиенты использовать локатора Контроллеров домена, а также написали поисковые запросы. 
- Существует ряд до пяти минут пики 10%, с некоторыми большой 20%. Как правило если только они смогут нанести целевого плана емкости превышен, исследование их не является необходимой.  
- Периода наибольшей загрузки для всех систем — между около 8:00 до 9:15 AM. С помощью плавный переход от около 5:00 до около 17:00:00 это обычно свидетельствует о бизнес-цикл. За пределами забот о планировании производительности будет более случайного пиков использования ЦП на сценарии поля», «между 17:00:00 и 4:00.

  >[!NOTE]
  >В хорошо управляемой системе указанного пики происходят возможно выполняется программное обеспечение резервного копирования, полную антивирусную проверку, инвентаризации оборудования или программного обеспечения, развертывание программного обеспечения или исправления и т. д. Так как они выходящих за пределы рабочего цикла пиковой пользователя, целевые объекты не превышены.

- Каждой системы составляет около 40% и всех систем тем же количеством процессоров, следует один сбой или перевести в автономный режим, выполнить оставшиеся системы предполагаемое 53% (система System D 40% нагрузки равномерно разделить который добавляется в объект системы и системы C существующие нагрузки 40%). По ряду причин это линейной предположение не вполне точные, но предоставляет точностью, достаточной для оценки.  

  **Альтернативный сценарий:** два контроллера домена под управлением 40%: Происходит сбой контроллера одного домена, предполагаемый уровень загрузки Процессора оставшиеся один бы предполагаемое 80%. Это намного превышает пороговые значения, описанные выше, для плана емкости и также начинает строго ограничить количество головной свободного места для 10 – 20% в профиль нагрузки выше, это означает, что также пиковые нагрузки бы диска контроллера домена до 90% до 100%, во время "*N*"сценарии и определенно привести к снижению скорости реагирования.

### <a name="calculating-cpu-demands"></a>Расчет требований к ЦП

«Процесс\\% загруженности процессора» объекта счетчика производительности выполняет суммирование количества времени, что все потоки приложения можно потратить на ЦП и время делится на общее количество системы прохождения. Это действует многопоточного приложения в системе с несколькими ЦП может превышать 100% времени ЦП что будет очень по-разному интерпретироваться чем «сведения о процессоре\\процессоров %». На практике «Process(lsass)\\% Processor Time» можно рассматривать как число процессоров на 100%, необходимые для поддержки требований процесса. Значение 200% означает, что 2 процессора, каждой 100%, необходимых для поддержки полной загрузки AD DS. Несмотря на то, что находится под управлением 100% загруженности Процессора наиболее экономически эффективным решением с точки зрения деньги, затраченное на ЦП и потребление мощности и энергии, по ряду причин, подробно описаны в приложении A, повысить скорость реагирования в многопоточных системе происходит, когда система не запущена на 100%.

Чтобы адаптировать переходные всплески нагрузки клиента, рекомендуется для пикового периода ЦП из диапазона от 40% до 60% от мощности системы. Работа в приведенном выше примере, это означает что между 3,33 (60% в целевой объект) и 5 (целевой объект 40%) ЦП потребуется для загрузки (процесс lsass) AD DS. Дополнительные ресурсы должны быть добавлены в в соответствии с требованиями базовой операционной системы и другие агенты, необходимые (например антивирусными программами, резервного копирования, мониторинга и т. д.). Несмотря на то, что последствия агенты должны обрабатываться по принципу в среде, можно сделать оценку от 5% до 10% одного ЦП. В этом примере это предположить, что между выпуска версии 3.43 (60% в целевой объект) и 5.1 (целевой объект 40%) процессоров необходимы в периоды пиковой нагрузки.

Для этого проще для использования в представлении «С областями с накоплением» в Windows монитор надежности и производительности (perfmon), убедившись, что все счетчики, масштабировать же.

Допущения:

- Цель — уменьшить занимаемое место для как можно меньшее число серверов, максимально. В идеале, один сервер будет содержать нагрузки и дополнительный сервер добавлен для обеспечения избыточности (*N* + 1 сценарий).

![График процессорного времени для процесса lsass (через всех процессоров)](media/capacity-planning-considerations-proc-time-chart.png)

Знания, полученные из данных в диаграмме (Process(lsass)\\% загруженности процессора):

- Рабочий день начинается представляют собой связующее около 7:00 и уменьшается в 17:00:00.
- Максимальная нагрузка периода наибольшей загрузки — с 9:30:11: 00 по. 
  > [!NOTE]
  > Все данные производительности журнала. Точки данных (пик) в 9:15 указывает нагрузку с 9:00 до 9:15.
- Есть пиковые нагрузки до 7:00:00 это может указывать либо нагрузки из разных часовых поясах, либо фоновой активности инфраструктуры, такие как резервное копирование. Так как максимальных в 9:30 превышает это действие, это не относится.
- Существует три контроллера домена на сайте.

При максимальной нагрузке lsass занимает около 485% одного ЦП или 4.85 ЦП на 100%. Согласно математические ранее, это означает, что сайт должен около указано 12,25 ЦП для AD DS. Добавьте приведенные выше предложения из 5 – 10% для фоновых процессов, и это означает, что сегодня замены сервера необходимо приблизительно: 12,35 12.30 для процессоров для поддержки одинаковой нагрузки. Среды оценки для увеличения размера теперь должен вынесены.

### <a name="when-to-tune-ldap-weights"></a>Когда следует настроить веса LDAP

Существует несколько сценариев при настройке [LdapSrvWeight](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc957291(v=technet.10)) следует учитывать. В контексте планирования загрузки это можно сделать при загрузке приложением или пользователем не распределяются равномерно, или базовых систем не распределяются равномерно с точки зрения возможностей. Ниже приведены причины для этого за планирование производительности выходит за рамки этой статьи.

Существуют две распространенные причины для настройки веса LDAP:

- Эмулятор основного контроллера домена приведен пример, который влияет на любой среды, для которых пользователь или приложение поведение при загрузке не распределяется равномерно. Как определенные инструменты и действия целевой эмулятор основного контроллера домена, такие как средства управления групповой политики, второй попытки в случае ошибки проверки подлинности, установление доверия и т. д ресурсов ЦП на эмулятор основного контроллера домена может быть более интенсивно затребованное, чем в любом месте веб-узел.
  - Ключ используется только для настройки этого, если имеется существенное различие в ЦП, чтобы снизить нагрузку на эмулятор основного контроллера домена и увеличить нагрузку на другие контроллеры домена позволит более равномерное распределение нагрузки.
  - В этом случае задайте LDAPSrvWeight от 50 до 75 для эмулятора основного контроллера домена.
- Серверы с разными значениями счетчиков ЦП (и скорость) на сайте.  Например предположим, что существуют два восьмиядерных сервера и один сервер с четырьмя ядрами.  Последний сервер имеет половина процессоров двух других серверов.  Это означает, что клиент также распределенного нагрузочного увеличит средняя загрузка ЦП в окне Четырехъядерная, чтобы примерно в два раза, восемь полей.
  - Например два восьмиядерных поля будет выполняться на 40% и поле Четырехъядерная будет выполняться на 80%.
  - Кроме того стоит последствия потери одной восьмиядерных поля в этом сценарии, в частности тот факт, что поле Четырехъядерная теперь будет можно перегружать.

#### <a name="example-1---pdc"></a>Пример 1 - основного контроллера домена

| |Использование со значениями по умолчанию|Новый LdapSrvWeight|Предполагаемое использование нового|
|-|-|-|-|
|1 контроллер домена (эмуляторе PDC)|53%|57|40 %|
|2 КОНТРОЛЛЕРА ДОМЕНА|33%|100|40 %|
|DC 3|33%|100|40 %|

Проблема здесь в том, что если роль эмулятора основного контроллера домена, передаваемые или заняты, особенно на другом контроллере домена на сайте будет значительное увеличение на новый эмулятор основного контроллера домена.

Используя пример из раздела [целевой профиль поведение сайта](#target-site-behavior-profile), был сделан допущение, что все контроллеры домена на сайте есть четыре ЦП. Что делать, в нормальных условиях, если один из контроллеров домена имеет восемь ЦП? Будет два контроллера домена с загрузкой 40% и одну в загружена на 20%. Хотя это не неправильный, имеется возможность балансировки нагрузки немного лучше. Использовать LDAP весовые коэффициенты для выполнения этой задачи.  Пример сценария будет следующим:

#### <a name="example-2---differing-cpu-counts"></a>Пример 2 - подсчитывает отличающийся ЦП

| |Сведения о процессоре\\ %&nbsp;Utility(_Total) процессора<br />Использование со значениями по умолчанию|Новый LdapSrvWeight|Предполагаемое использование нового|
|-|-|-|-|
|КОНТРОЛЛЕР ДОМЕНА 4 ЦП 1|40|100|30 %|
|ЦП 4 КОНТРОЛЛЕРА ДОМЕНА 2|40|100|30 %|
|8-ПРОЦЕССОРНОМ DC 3|20|200|30 %|

Однако следует очень тщательно с помощью этих сценариев. Как видно выше, математические выглядит очень удобная и аккуратная на бумаге. Но в этой статье, планирование "*N* + 1" Сценарий имеет первостепенное значение. Влияние одного контроллера домена переходит в автономный режим должен вычисляться для каждого сценария. В ближайший предшествующий сценарии, где распределение нагрузки четное, чтобы обеспечить 60% загрузки во время "*N*" сценарии с нагрузкой, равномерно распределяется среди всех серверов распределение будет вполне достаточно как оставаться пропорции согласованность. Глядя на эмулятор основного контроллера домена, настройке и в целом любого сценария где несбалансированной нагрузки пользователя или приложения, результат отличается очень:

| |Оптимальные настройки использования|Новый LdapSrvWeight|Предполагаемое использование нового|
|-|-|-|-|
|1 контроллер домена (эмуляторе PDC)|40 %|85|47%|
|2 КОНТРОЛЛЕРА ДОМЕНА|40 %|100|53%|
|DC 3|40 %|100|53%|

### <a name="virtualization-considerations-for-processing"></a>Рекомендации по виртуализации для обработки

Существует два уровня планирования ресурсов, которые необходимо выполнить в виртуальной среде. На уровне узла, аналогичную код бизнес-цикла, описанные для контроллера домена, ранее, обработка пороговые значения в период пиковой должны быть идентифицированы. Так как для базовых участников одинаковы для хост-компьютере, планирование гостевой потоков на ЦП, что и для получения AD DS потоков на ЦП на физическом компьютере, рекомендуется использовать одной и той же цели из 40 до 60% на базового узла. На следующий уровень на уровне гостя, с момента участников планирование потоков не изменены, цель в рамках остается гостя в диапазоне от 40 до 60%.

В direct сопоставленные сценарии один гостевой каждого узла, все планирование загрузки для этой точки должен быть добавлен требованиям операционной системы узла (оперативной памяти, диска, сети). В случае общего узла показывает, что существует 10% влияние на эффективность базовой процессоров. Это означает, что если сайту требуются 10 процессоров на 40%, рекомендуемый объем виртуальных ЦП для распределения по всем целевым "*N*" гости бы 11. На сайте со смешанной распространение физических серверов и виртуальных серверов модификатор применяется только к виртуальным машинам. Например, если у сайта "*N* + 1", один сервер физических или размещенный direct с 10 процессоров будут о эквивалент одной виртуальной машине с 11 ЦП на узле, с 11 ЦП, зарезервированных для контроллера домена.

На протяжении всего анализа и вычисления количества ЦП необходимые для поддержки нагрузки AD DS, числа процессоров, которые сопоставляются с как можно приобрести в физическом оборудовании условия не соответствуют обязательно аккуратно. Виртуализация избавляет от необходимости округление вверх. Виртуализация сокращает усилия, необходимые для добавления вычислительной мощности на узле, учитывая простота, с которой ЦП могут добавляться к виртуальной Машине. Оно не устраняет необходимость точно оценить вычислительную мощность, необходимые, чтобы оборудование был доступен, когда дополнительные ЦП должны быть добавлены гостевым виртуальным машинам.  Как всегда не забудьте планирования и отслеживания для роста спроса.

### <a name="calculation-summary-example"></a>Пример сводки вычисления

|Система|Пиковая загрузка ЦП|
|-|-|-|
|КОНТРОЛЛЕР ДОМЕНА 1|120%|
|2 КОНТРОЛЛЕРА ДОМЕНА|147%|
|Dc 3|218%|
|Используется общее время ЦП|485%|  
  
|Количество систем|Общая пропускная способность (выше)|
|-|-|
|ЦП, необходимые на целевом объекте 40%|4.85 &divide; .4 = 12.25|

Повторение из-за важности этого момента *запомнить для дальнейшего развития*. При условии, что рост 50% в течение следующих трех лет, этой среды потребуется 18.375 ЦП (12.25 &times; 1.5) на метке три года. Просмотр после первого года и при необходимости добавьте дополнительную емкость будет альтернативному плану.

### <a name="cross-trust-client-authentication-load-for-ntlm"></a>Кросс trust клиента проверки подлинности нагрузки при использовании NTLM

#### <a name="evaluating-cross-trust-client-authentication-load"></a>Оценка нагрузки кросс trust клиента проверки подлинности

Во многих средах может иметь один или несколько доменов, соединенных отношение доверия. Запрос на проверку подлинности для удостоверения в другом домене, который не использует проверку подлинности Kerberos необходимо просматривающие доверие с помощью безопасного канала контроллера домена на другой контроллер домена в конечный домен или следующий домен в пути конечный домены. Количество одновременных вызовов, с помощью безопасного канала, которая может сделать контроллером домена к контроллеру домена в доверенном домене контролируется с помощью параметра, известный как **MaxConcurrentAPI**. Для контроллеров домена, гарантируя, что защищенный канал может обрабатывать объем нагрузки можно сделать одним из двух подходов: Помощник по настройке **MaxConcurrentAPI** или в лесу, создание установленного напрямую доверия. Чтобы оценить объем трафика отдельных доверия, обратитесь к [как настройка производительности для проверки подлинности NTLM с использованием настройки MaxConcurrentApi](https://support.microsoft.com/kb/2688798).

Во время сбора данных, как и в любом другом варианте должны собираться во время пиков занят дня для данных быть полезным.

> [!NOTE]
> Внутри леса и между лесами сценариев могут привести к аутентификации для обхода несколькими отношениями, и каждый этап должен настраиваться.

#### <a name="planning"></a>Планирование

Существует ряд приложений, которые по умолчанию используют проверку подлинности NTLM, или использовать его в определенные сценарии конфигурации. Серверы приложений увеличению емкости и обслуживать все большее число активных клиентов. Имеется также тренда, что клиенты не закрывайте сеансов в течение ограниченного времени, а вместо повторного подключения на регулярной основе (например, синхронизация электронной почты по запросу). Другой распространенный пример на высокую нагрузку NTLM — серверы веб-прокси, требующих проверки подлинности для доступа к Интернету.

Эти приложения могут вызвать значительные нагрузки для проверки подлинности NTLM, что можно разместить значительные нагрузки на контроллеры домена, особенно в том случае, если пользователи и ресурсы находятся в разных доменах.

Существует несколько подходов к Управление доверием между нагрузки, которые фактически используются совместно, а не в монопольную либо / или сценарии. Возможными параметрами являются:

- Уменьшите проверки подлинности клиента кросс trust, обнаружение служб, которые использует пользователь в том же домене, в которой является пользователь, находящихся во.
- Увеличение числа secure-доступных каналов. Это относится к внутри леса и трафика между лесами и известны как установленное напрямую доверие.
- Настроить параметры по умолчанию **MaxConcurrentAPI**.

Для настройки **MaxConcurrentAPI** на существующем сервере, является уравнение:

> *New_MaxConcurrentApi_setting* &ge; (*semaphore_acquires* + *semaphore_time подробно*) &times; *average_semaphore_ hold_time* &divide; *time_collection_length*

Дополнительные сведения см. в разделе [статье базы Знаний 2688798: Как сделать, Настройка производительности для проверки подлинности NTLM с использованием настройки MaxConcurrentApi](http://support.microsoft.com/kb/2688798).

## <a name="virtualization-considerations"></a>Сведения о виртуализации

Нет, это настройки параметров операционной системы.

### <a name="calculation-summary-example"></a>Пример сводки вычисления

|Тип данных|Значение|
|-|-|
|Семафор получает (минимум)|6,161|
|Семафор получает (максимум)|6,762|
|Время ожидания семафора|0|
|Семафор среднее время удержания|0.012|
|Длительность коллекции (в секундах)|1:11 мин (71 секунд)|
|Формулы (из базы Знаний 2688798)|((6762 &ndash; 6161) + 0) &times; 0.012 /|
|Минимальное значение для **MaxConcurrentAPI**|((6762 &ndash; 6161) + 0) &times; 0.012 &divide; 71 = .101|

Для этой системы для этого периода времени допустимые значения по умолчанию.

## <a name="monitoring-for-compliance-with-capacity-planning-goals"></a>Мониторинг соответствия целей при планировании емкости

В этой статье он описан планировать и масштабирование перейти на использование целевых объектов. Здесь находится Сводная диаграмма рекомендуемые пороговые значения, которые необходимо отслеживать. Это позволит убедиться, что при работе системы выходит за пределы необходимую емкость. Имейте в виду, что это не пороговых значений производительности, но планирование пороговых значений загрузки. Сервер, работающий сверх эти пороговые значения будет работать, но сейчас нужно запустить проверку, что все приложения хорошо работает. Если сказал, что приложения правильно, пришло время начать оценку продукта обновления оборудования или другие изменения в конфигурацию.

|Category|Счетчик производительности|Интервал/выборки|Целевой объект|Предупреждение|
|-|-|-|-|-|
|Процессор|Processor Information(_Total)\\% Processor Utility|60 min|40%|60%|
|RAM (Windows Server 2008 R2 or earlier)|Memory\Available MB|< 100 MB|N/A|< 100 MB|
|RAM (Windows Server 2012)|Memory\Long-Term Average Standby Cache Lifetime(s)|30 min|Must be tested|Must be tested|
|Network|Network Interface(\*)\Bytes Sent/sec<br /><br />Network Interface(\*)\Bytes Received/sec|30 min|40%|60%|
|Storage|LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Read<br /><br />LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Write|60 min|10 ms|15 ms|
|AD Services|Netlogon(\*)\Average Semaphore Hold Time|60 min|0|1 second|

## Appendix A: CPU sizing criteria

### Definitions

**Processor (microprocessor) –** a component that reads and executes program instructions  

**CPU –** Central Processing Unit  

**Multi-Core processor –** multiple CPUs on the same integrated circuit  

**Multi-CPU –** multiple CPUs, not on the same integrated circuit  

**Logical Processor –** one logical computing engine from the perspective of the operating system  

This includes hyper-threaded, one core on multi-core processor, or a single core processor.  

As today’s server systems have multiple processors, multiple multi-core processors, and hyper-threading, this information is generalized to cover both scenarios. As such, the term logical processor will be used as it represents the operating system and application perspective of the available computing engines.

### Thread-level parallelism

Each thread is an independent task, as each thread has its own stack and instructions. Because AD DS is multi-threaded and the number of available threads can be tuned by using [How to view and set LDAP policy in Active Directory by using Ntdsutil.exe](http://support.microsoft.com/kb/315071), it scales well across multiple logical processors.

### Data-level parallelism

This involves sharing data across multiple threads within one process (in the case of the AD DS process alone) and across multiple threads in multiple processes (in general). With concern to over-simplifying the case, this means that any changes to data are reflected to all running threads in all the various levels of cache (L1, L2, L3) across all cores running said threads as well as updating shared memory. Performance can degrade during write operations while all the various memory locations are brought consistent before instruction processing can continue.

### CPU speed vs. multiple-core considerations

The general rule of thumb is faster logical processors reduce the duration it takes to process a series of instructions, while more logical processors means that more tasks can be run at the same time. These rules of thumb break down as the scenarios become inherently more complex with considerations of fetching data from shared-memory, waiting on data-level parallelism, and the overhead of managing multiple threads. This is also why scalability in multi-core systems is not linear.

Consider the following analogies in these considerations: think of a highway, with each thread being an individual car, each lane being a core, and the speed limit being the clock speed.

1. If there is only one car on the highway, it doesn’t matter if there are two lanes or 12 lanes. That car is only going to go as fast as the speed limit will allow.
1. Assume that the data the thread needs is not immediately available. The analogy would be that a segment of road is shutdown. If there is only one car on the highway, it doesn’t matter what the speed limit is until the lane is reopened (data is fetched from memory).
1. As the number of cars increase, the overhead to manage the number of cars increases. Compare the experience of driving and the amount of attention necessary when the road is practically empty (such as late evening) versus when the traffic is heavy (such as mid-afternoon, but not rush hour). Also, consider the amount of attention necessary when driving on a two-lane highway, where there is only one other lane to worry about what the drivers are doing, versus a six-lane highway where one has to worry about what a lot of other drivers are doing.
   > [!NOTE]
   > The analogy about the rush hour scenario is extended in the next section: Response Time/How the System Busyness Impacts Performance.

As a result, specifics about more or faster processors become highly subjective to application behavior, which in the case of AD DS is very environmentally specific and even varies from server to server within an environment. This is why the references earlier in the article do not invest heavily in being overly precise, and a margin of safety is included in the calculations. When making budget-driven purchasing decisions, it is recommended that optimizing usage of the processors at 40% (or the desired number for the environment) occurs first, before considering buying faster processors. The increased synchronization across more processors reduces the true benefit of more processors from the linear progression (2&times; the number of processors provides less than 2&times; available additional compute power).

> [!NOTE]
> Amdahl’s Law and Gustafson’s Law are the relevant concepts here.

### Response time/How the system busyness impacts performance

Queuing theory is the mathematical study of waiting lines (queues). In queuing theory, the Utilization Law is represented by the equation:

*U* k = *B* &divide; *T*

Where *U* k is the utilization percentage, *B* is the amount of time busy, and *T* is the total time the system was observed. Translated into the context of Windows, this means the number of 100-nanosecond (ns) interval threads that are in a Running state divided by how many 100-ns intervals were available in given time interval. This is exactly the formula for calculating % Processor Utility (reference [Processor Object](https://docs.microsoft.com/previous-versions/ms804036(v=msdn.10)) and [PERF_100NSEC_TIMER_INV](https://docs.microsoft.com/previous-versions/windows/embedded/ms901169(v=msdn.10))).

Queuing theory also provides the formula: *N* = *U* k &divide; (1 &ndash; *U* k) to estimate the number of waiting items based on utilization ( *N* is the length of the queue). Charting this over all utilization intervals provides the following estimates to how long the queue to get on the processor is at any given CPU load.

![Queue length](media/capacity-planning-considerations-queue-length.png)

It is observed that after 50% CPU load, on average there is always a wait of one other item in the queue, with a noticeably rapid increase after about 70% CPU utilization.

Returning to the driving analogy used earlier in this section:

- The busy times of “mid-afternoon” would, hypothetically, fall somewhere into the 40% to 70% range. There is enough traffic such that one’s ability to pick any lane is not majorly restricted, and the chance of another driver being in the way, while high, does not require the level of effort to “find” a safe gap between other cars on the road.
- One will notice that as traffic approaches rush hour, the road system approaches 100% capacity. Changing lanes can become very challenging because cars are so close together that increased caution must be exercised to do so.

This is why the long term averages for capacity conservatively estimated at 40% allows for head room for abnormal spikes in load, whether said spikes transitory (such as poorly coded queries that run for a few minutes) or abnormal bursts in general load (the morning of the first day after a long weekend).

The above statement regards % Processor Time calculation being the same as the Utilization Law is a bit of a simplification for the ease of the general reader. For those more mathematically rigorous:  
- Translating the [PERF_100NSEC_TIMER_INV](https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms901169(v=msdn.10))
  - *B* = The number of 100-ns intervals “Idle” thread spends on the logical processor. The change in the “*X*” variable in the [PERF_100NSEC_TIMER_INV](https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms901169(v=msdn.10)) calculation
  - *T* = the total number of 100-ns intervals in a given time range. The change in the “*Y*” variable in the [PERF_100NSEC_TIMER_INV](https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms901169(v=msdn.10)) calculation.
  - *U* k = The utilization percentage of the logical processor by the “Idle Thread” or % Idle Time.  
- Working out the math:
  - *U* k = 1 – %Processor Time
  - %Processor Time = 1 – *U* k
  - %Processor Time = 1 – *B* / *T*
  - %Processor Time = 1 – *X1* – *X0* / *Y1* – *Y0*

### Applying the concepts to capacity planning

The preceding math may make determinations about the number of logical processors needed in a system seem overwhelmingly complex. This is why the approach to sizing the systems is focused on determining maximum target utilization based on current load and calculating the number of logical processors required to get there. Additionally, while logical processor speeds will have a significant impact on performance, cache efficiencies, memory coherence requirements, thread scheduling and synchronization, and imperfectly balanced client load will all have significant impacts on performance that will vary on a server-by-server basis. With the relatively cheap cost of compute power, attempting to analyze and determine the perfect number of CPUs needed becomes more an academic exercise than it does provide business value.

Forty percent is not a hard and fast requirement, it is a reasonable start. Various consumers of Active Directory require various levels of responsiveness. There may be scenarios where environments can run at 80% or 90% utilization as a sustained average, as the increased wait times for access to the processor will not noticeably impact client performance. It is important to re-iterate that there are many areas in the system that are much slower than the logical processor in the system, including access to RAM, access to disk, and transmitting the response over the network. All of these items need to be tuned in conjunction. Examples:

- Adding more processors to a system running 90% that is disk-bound is probably not going to significantly improve performance. Deeper analysis of the system will probably identify that there are a lot of threads that are not even getting on the processor because they are waiting on I/O to complete.
- Resolving the disk-bound issues potentially means that threads that were previously spending a lot of time in a waiting state will no longer be in a waiting state for I/O and there will be more competition for CPU time, meaning that the 90% utilization in the previous example will go to 100% (because it can not go higher). Both components need to be tuned in conjunction.
  > [!NOTE]
  > Processor Information(*)\\% Processor Utility can exceed 100% with systems that have a "Turbo" mode.  This is where the CPU exceeds the rated processor speed for short periods.  Reference CPU manufacturers documentation and description of the counter for greater insight.  

Discussing whole system utilization considerations also brings into the conversation domain controllers as virtualized guests. [Response time/How the system busyness impacts performance](#response-timehow-the-system-busyness-impacts-performance) applies to both the host and the guest in a virtualized scenario. This is why in a host with only one guest, a domain controller (and generally any system) has near the same performance it does on physical hardware. Adding additional guests to the hosts increases the utilization of the underlying host, thereby increasing the wait times to get access to the processors as explained previously. In short, logical processor utilization needs to be managed at both the host and at the guest levels.

Extending the previous analogies, leaving the highway as the physical hardware, the guest VM will be analogized with a bus (an express bus that goes straight to the destination the rider wants). Imagine the following four scenarios:

- It is off hours, a rider gets on a bus that is nearly empty, and the bus gets on a road that is also nearly empty. As there is no traffic to contend with, the rider has a nice easy ride and gets there just as fast as if the rider had driven instead. The rider’s travel times are still constrained by the speed limit.
- It is off hours so the bus is nearly empty but most of the lanes on the road are closed, so the highway is still congested. The rider is on an almost-empty bus on a congested road. While the rider does not have a lot of competition in the bus for where to sit, the total trip time is still dictated by the rest of the traffic outside.
- It is rush hour so the highway and the bus are congested. Not only does the trip take longer, but getting on and off the bus is a nightmare because people are shoulder to shoulder and the highway is not much better. Adding more busses (logical processors to the guest) does not mean they can fit on the road any more easily, or that the trip will be shortened.
- The final scenario, though it may be stretching the analogy a little, is where the bus is full, but the road is not congested. While the rider will still have trouble getting on and off the bus, the trip will be efficient after the bus is on the road. This is the only scenario where adding more busses (logical processors to the guest) will improve guest performance.

From there it is relatively easy to extrapolate that there are a number of scenarios in between the 0%-utilized and the 100%-utilized state of the road and the 0%- and 100%-utilized state of the bus that have varying degrees of impact.

Applying the principals above of 40% CPU as reasonable target for the host as well as the guest is a reasonable start for the same reasoning as above, the amount of queuing.

## Appendix B: Considerations regarding different processor speeds, and the effect of processor power management on processor speeds

Throughout the sections on processor selection the assumption is made that the processor is running at 100% of clock speed the entire time the data is being collected and that the replacement systems will have the same speed processors. Despite both assumptions in practice being false, particularly with Windows Server 2008 R2 and later, where the default power plan is **Balanced**, the methodology still stands as it is the conservative approach. While the potential error rate may increase, it only increases the margin of safety as processor speeds increase.

- For example, in a scenario where 11.25 CPUs are demanded, if the processors were running at half speed when the data was collected, the more accurate estimate might be 5.125 &divide; 2.
- It is impossible to guarantee that doubling the clock speeds would double the amount of processing that happens for a given time period. This is due to the fact the amount of time that the processors spend waiting on RAM or other system components could stay the same. The net effect is that the faster processors might spend a greater percentage of the time idle while waiting on data to be fetched. Again, it is recommended to stick with the lowest common denominator, being conservative, and avoid trying to calculate a potentially false level of accuracy by assuming a linear comparison between processor speeds.

Alternatively, if processor speeds in replacement hardware are lower than current hardware, it would be safe to increase the estimate of processors needed by a proportionate amount. For example, it is calculated that 10 processors are needed to sustain the load in a site, and the current processors are running at 3.3 Ghz and replacement processors will run at 2.6 Ghz, this is a 21% decrease in speed. In this case, 12 processors would be the recommended amount.

That said, this variability would not change the Capacity Management processor utilization targets. As processor clock speeds will be adjusted dynamically based on the load demanded, running the system under higher loads will generate a scenario where the CPU spends more time in a higher clock speed state, making the ultimate goal to be at 40% utilization in a 100% clock speed state at peak. Anything less than that will generate power savings as CPU speeds will be throttled back during off peak scenarios.

> [!NOTE]
> An option would be to turn off power management on the processors (setting the power plan to **High Performance**) while data is collected. That would give a more accurate representation of the CPU consumption on the target server.

To adjust estimates for different processors, it used to be safe, excluding other system bottlenecks outlined above, to assume that doubling processor speeds doubled the amount of processing that could be performed.  Today, the internal architecture of processors is different enough between processors, that a safer way to gauge the effects of using different processors than data was taken from is to leverage the SPECint_rate2006 benchmark from Standard Performance Evaluation Corporation.

1. Find the SPECint_rate2006 scores for the processor that are in use and that plan to be used.
    1. On the website of the Standard Performance Evaluation Corporation, select **Results**, highlight **CPU2006**, and select **Search all SPECint_rate2006 results**.
    1. Under **Simple Request**, enter the search criteria for the target processor, for example **Processor Matches E5-2630 (baselinetarget)** and **Processor Matches E5-2650 (baseline)**.
    1. Find the server and processor configuration to be used (or something close, if an exact match is not available) and note the value in the **Result** and **# Cores** columns.
1. To determine the modifier use the following equation:
   >((*Target platform per-core score value*) &times; (*MHz per-core of baseline platform*)) &divide; ((*Baseline per-core score value*) &times; (*MHz per-core of target platform*))  

    Using the above example:
   >(35.83 &times; 2000) &divide; (33.75 &times; 2300) = 0.92
1. Multiply the estimated number of processors by the modifier.  In the above case to go from the E5-2650 processor to the E5-2630 processor multiply the calculated 11.25 CPUs &times; 0.92 = 10.35 processors needed.

## Appendix C: Fundamentals regarding the operating system interacting with storage

The queuing theory concepts outlined in [Response time/How the system busyness impacts performance](#response-timehow-the-system-busyness-impacts-performance) are also applicable to storage. Having a familiarity of how the operating system handles I/O is necessary to apply these concepts. In the Microsoft Windows operating system, a queue to hold the I/O requests is created for each physical disk. However, a clarification on physical disk needs to be made. Array controllers and SANs present aggregations of spindles to the operating system as single physical disks. Additionally, array controllers and SANs can aggregate multiple disks into one array set and then split this array set into multiple “partitions”, which is in turn presented to the operating system as multiple physical disks (ref. figure).

![Block spindles](media/capacity-planning-considerations-block-spindles.png)  

In this figure the two spindles are mirrored and split into logical areas for data storage (Data 1 and Data 2). These logical areas are viewed by the operating system as separate physical disks.

Although this can be highly confusing, the following terminology is used throughout this appendix to identify the different entities:

- **Spindle –** the device that is physically installed in the server.
- **Array –** a collection of spindles aggregated by controller.
- **Array partition –** a partitioning of the aggregated array
- **LUN –** an array, used when referring to SANs
- **Disk –** What the operating system observes to be a single physical disk.
- **Partition –** a logical partitioning of what the operating system perceives as a physical disk.

### Operating system architecture considerations

The operating system creates a First In/First Out (FIFO) I/O queue for each disk that is observed; this disk may be representing a spindle, an array, or an array partition. From the operating system perspective, with regard to handling I/O, the more active queues the better. As a FIFO queue is serialized, meaning that all I/Os issued to the storage subsystem must be processed in the order the request arrived. By correlating each disk observed by the operating system with a spindle/array, the operating system now maintains an I/O queue for each unique set of disks, thereby eliminating contention for scarce I/O resources across disks and isolating I/O demand to a single disk. As an exception, Windows Server 2008 introduces the concept of I/O prioritization, and applications designed to use the “Low” priority fall out of this normal order and take a back seat. Applications not specifically coded to leverage the “Low” priority default to “Normal.”

### Introducing simple storage subsystems

Starting with a simple example (a single hard drive inside a computer) a component-by-component analysis will be given. Breaking this down into the major storage subsystem components, the system consists of:

- **1 –** 10,000 RPM Ultra Fast SCSI HD (Ultra Fast SCSI has a 20 MB/s transfer rate)
- **1 –** SCSI Bus (the cable)
- **1 –** Ultra Fast SCSI Adapter
- **1 –** 32-bit 33 MHz PCI bus

Once the components are identified, an idea of how much data can transit the system, or how much I/O can be handled, can be calculated. Note that the amount of I/O and quantity of data that can transit the system is correlated, but not the same. This correlation depends on whether the disk I/O is random or sequential and the block size. (All data is written to the disk as a block, but different applications using different block sizes.) On a component-by-component basis:

- **The hard drive –** The average 10,000-RPM hard drive has a 7-millisecond (ms) seek time and a 3 ms access time. Seek time is the average amount of time it takes the read/write head to move to a location on the platter. Access time is the average amount of time it takes to read or write the data to disk, once the head is in the correct location. Thus, the average time for reading a unique block of data in a 10,000-RPM HD constitutes a seek and an access, for a total of approximately 10 ms (or .010 seconds) per block of data.

  When every disk access requires movement of the head to a new location on the disk, the read/write behavior is referred to as “random.” Thus, when all I/O is random, a 10,000-RPM HD can handle approximately 100 I/O per second (IOPS) (the formula is 1000 ms per second divided by 10 ms per I/O or 1000/10=100 IOPS).

  Alternatively, when all I/O occurs from adjacent sectors on the HD, this is referred to as sequential I/O. Sequential I/O has no seek time because when the first I/O is complete, the read/write head is at the start of where the next block of data is stored on the HD. Thus a 10,000-RPM HD is capable of handling approximately 333 I/O per second (1000 ms per second divided by 3 ms per I/O).

  >[!NOTE]
  >This example does not reflect the disk cache, where the data of one cylinder is typically kept. In this case, the 10 ms are needed on the first I/O and the disk reads the whole cylinder. All other sequential I/O is satisfied from the cache. As a result, in-disk caches might improve sequential I/O performance.
  
  So far, the transfer rate of the hard drive has been irrelevant. Whether the hard drive is 20 MB/s Ultra Wide or an Ultra3 160 MB/s, the actual amount of IOPS the can be handled by the 10,000-RPM HD is ~100 random or ~300 sequential I/O. As block sizes change based on the application writing to the drive, the amount of data that is pulled per I/O is different. For example, if the block size is 8 KB, 100 I/O operations will read from or write to the hard drive a total of 800 KB. However, if the block size is 32 KB, 100 I/O will read/write 3,200 KB (3.2 MB) to the hard drive. As long as the SCSI transfer rate is in excess of the total amount of data transferred, getting a “faster” transfer rate drive will gain nothing. See the following tables for comparison.

  | |7200 RPM 9ms seek, 4ms access|10,000 RPM 7ms seek, 3ms access|15,000 RPM 4ms seek, 2ms access
  |-|-|-|-|
  |Random I/O|80|100|150|
  |Sequential I/O|250|300|500|  
  
  |10,000 RPM drive|8 KB block size (Active Directory Jet)|
  |-|-|
  |Random I/O|800 KB/s|
  |Sequential I/O|2400 KB/s|

- **SCSI backplane (bus) –** Understanding how the “SCSI backplane (bus)”, or in this scenario the ribbon cable, impacts throughput of the storage subsystem depends on knowledge of the block size. Essentially the question would be, how much I/O can the bus handle if the I/O is in 8 KB blocks? In this scenario, the SCSI bus is 20 MB/s, or 20480 KB/s. 20480 KB/s divided by 8 KB blocks yields a maximum of approximately 2500 IOPS supported by the SCSI bus.

  >[!NOTE]
  >The figures in the following table represent an example. Most attached storage devices currently use PCI Express, which provides much higher throughput.  
  
  |I/O supported by SCSI bus per block size|2 KB block size|8 KB block size (AD Jet) (SQL Server 7.0/SQL Server 2000)
  |-|-|-|
  |20 MB/s|10,000|2,500|
  |40 MB/s|20,000|5,000|
  |128 MB/s|65,536|16,384|
  |320 MB/s|160,000|40,000|

  As can be determined from this chart, in the scenario presented, no matter what the use, the bus will never be a bottleneck, as the spindle maximum is 100 I/O, well below any of the above thresholds.

  >[!NOTE]
  >This assumes that the SCSI bus is 100% efficient.
  
- **SCSI adapter –** For determining the amount of I/O that this can handle, the manufacturer’s specifications need to be checked. Directing I/O requests to the appropriate device requires processing of some sort, thus the amount of I/O that can be handled is dependent on the SCSI adapter (or array controller) processor.

  In this example, the assumption that 1,000 I/O can be handled will be made.

- **PCI bus –** This is an often overlooked component. In this example, this will not be the bottleneck; however as systems scale up, it can become a bottleneck. For reference, a 32 bit PCI bus operating at 33Mhz can in theory transfer 133 MB/s of data. Following is the equation:  
  > 32 bits &divide; 8 bits per byte &times; 33 MHz = 133 MB/s.  

  Note that is the theoretical limit; in reality only about 50% of the maximum is actually reached, although in certain burst scenarios, 75% efficiency can be obtained for short periods.

  A 66Mhz 64-bit PCI bus can support a theoretical maximum of (64 bits &divide; 8 bits per byte &times; 66 Mhz) = 528 MB/sec. Additionally, any other device (such as the network adapter, second SCSI controller, and so on) will reduce the bandwidth available as the bandwidth is shared and the devices will contend for the limited resources.

After analysis of the components of this storage subsystem, the spindle is the limiting factor in the amount of I/O that can be requested, and consequently the amount of data that can transit the system. Specifically, in an AD DS scenario, this is 100 random I/O per second in 8 KB increments, for a total of 800 KB per second when accessing the Jet database. Alternatively, the maximum throughput for a spindle that is exclusively allocated to log files would suffer the following limitations: 300 sequential I/O per second in 8 KB increments, for a total of 2400 KB (2.4 MB) per second.

Now, having analyzed a simple configuration, the following table demonstrates where the bottleneck will occur as components in the storage subsystem are changed or added.

|Notes|Bottleneck analysis|Disk|Bus|Adapter|PCI bus|
|-|-|-|-|-|-|
|This is the domain controller configuration after adding a second disk. The disk configuration represents the bottleneck at 800 KB/s.|Add 1 disk (Total=2)<br /><br />I/O is random<br /><br />4 KB block size<br /><br />10,000 RPM HD|200 I/Os total<br />800 KB/s total.| | | |
|After adding 7 disks, the disk configuration still represents the bottleneck at 3200 KB/s.|**Add 7 disks (Total=8)**  <br /><br />I/O is random<br /><br />4 KB block size<br /><br />10,000 RPM HD|800 I/Os total.<br />3200 KB/s total| | | |
|After changing I/O to sequential, the network adapter becomes the bottleneck because it is limited to 1000 IOPS.|Add 7 disks (Total=8)<br /><br />**I/O is sequential**<br /><br />4 KB block size<br /><br />10,000 RPM HD| | |2400 I/O sec can be read/written to disk, controller limited to 1000 IOPS| |
|After replacing the network adapter with a SCSI adapter that supports 10,000 IOPS, the bottleneck returns to the disk configuration.|Add 7 disks (Total=8)<br /><br />I/O is random<br /><br />4 KB block size<br /><br />10,000 RPM HD<br /><br />**Upgrade SCSI adapter (now supports 10,000 I/O)**|800 I/Os total.<br />3,200 KB/s total| | | |
|After increasing the block size to 32 KB, the bus becomes the bottleneck because it only supports 20 MB/s.|Add 7 disks (Total=8)<br /><br />I/O is random<br /><br />**32 KB block size**<br /><br />10,000 RPM HD| |800 I/Os total. 25,600 KB/s (25 MB/s) can be read/written to disk.<br /><br />The bus only supports 20 MB/s| | |
|After upgrading the bus and adding more disks, the disk remains the bottleneck.|**Add 13 disks (Total=14)**<br /><br />Add second SCSI adapter with 14 disks<br /><br />I/O is random<br /><br />4 KB block size<br /><br />10,000 RPM HD<br /><br />**Upgrade to 320 MB/s SCSI bus**|2800 I/Os<br /><br />11,200 KB/s (10.9 MB/s)| | | |
|After changing I/O to sequential, the disk remains the bottleneck.|Add 13 disks (Total=14)<br /><br />Add second SCSI Adapter with 14 disks<br /><br />**I/O is sequential**<br /><br />4 KB block size<br /><br />10,000 RPM HD<br /><br />Upgrade to 320 MB/s SCSI bus|8,400 I/Os<br /><br />33,600 KB\s<br /><br />(32.8 MB\s)| | | |
|After adding faster hard drives, the disk remains the bottleneck.|Add 13 disks (Total=14)<br /><br />Add second SCSI adapter with 14 disks<br /><br />I/O is sequential<br /><br />4 KB block size<br /><br />**15,000 RPM HD**<br /><br />Upgrade to 320 MB/s SCSI bus|14,000 I/Os<br /><br />56,000 KB/s<br /><br />(54.7 MB/s)| | | |
|After increasing the block size to 32 KB, the PCI bus becomes the bottleneck.|Add 13 disks (Total=14)<br /><br />Add second SCSI adapter with 14 disks<br /><br />I/O is sequential<br /><br />**32 KB block size**<br /><br />15,000 RPM HD<br /><br />Upgrade to 320 MB/s SCSI bus| | | |14,000 I/Os<br /><br />448,000 KB/s<br /><br />(437 MB/s) is the read/write limit to the spindle.<br /><br />The PCI bus supports a theoretical maximum of 133 MB/s (75% efficient at best).|

### Introducing RAID

The nature of a storage subsystem does not change dramatically when an array controller is introduced; it just replaces the SCSI adapter in the calculations. What does change is the cost of reading and writing data to the disk when using the various array levels (such as RAID 0, RAID 1, or RAID 5).

In RAID 0, the data is striped across all the disks in the RAID set. This means that during a read or a write operation, a portion of the data is pulled from or pushed to each disk, increasing the amount of data that can transit the system during the same time period. Thus, in one second, on each spindle (again assuming 10,000-RPM drives), 100 I/O operations can be performed. The total amount of I/O that can be supported is N spindles times 100 I/O per second per spindle (yields 100*N I/O per second).

![Logical d: drive](media/capacity-planning-considerations-logical-d-drive.png)

In RAID 1, the data is mirrored (duplicated) across a pair of spindles for redundancy. Thus, when a read I/O operation is performed, data can be read from both of the spindles in the set. This effectively makes the I/O capacity from both disks available during a read operation. The caveat is that write operations gain no performance advantage in a RAID 1. This is because the same data needs to be written to both drives for the sake of redundancy. Though it does not take any longer, as the write of data occurs concurrently on both spindles, because both spindles are occupied duplicating the data, a write I/O operation in essence prevents two read operations from occurring. Thus, every write I/O costs two read I/O. A formula can be created from that information to determine the total number of I/O operations that are occurring:  

> *Read I/O* + 2 &times; *Write I/O* = *Total available disk I/O consumed*  

When the ratio of reads to writes and the number of spindles are known, the following equation can be derived from the above equation to identify the maximum I/O that can be supported by the array:  

> *Maximum IOPS per spindle* &times; 2 spindles &times; [(*%Reads* + *%Writes*) &divide; (*%Reads* + 2 &times; *%Writes*)] = *Total IOPS*

RAID 1+ 0, behaves exactly the same as RAID 1 regarding the expense of reading and writing. However, the I/O is now striped across each mirrored set. If  

> *Maximum IOPS per spindle* &times; 2 spindles &times; [(*%Reads* + *%Writes*) &divide; (*%Reads* + 2 &times; *%Writes*)] = *Total I/O*  

in a RAID 1 set, when a multiplicity (*N*) of RAID 1 sets are striped, the Total I/O that can be processed becomes N &times; I/O per RAID 1 set:  

> *N* &times; {*Maximum IOPS per spindle* &times; 2 spindles &times; [(*%Reads* + *%Writes*) &divide; (*%Reads* + 2 &times; *%Writes*)] } = *Total IOPS*

In RAID 5, sometimes referred to as *N* + 1 RAID, the data is striped across *N* spindles and parity information is written to the “+ 1” spindle. However, RAID 5 is much more expensive when performing a write I/O than RAID 1 or 1 + 0. RAID 5 performs the following process every time a write I/O is submitted to the array:

1. Read the old data
1. Read the old parity
1. Write the new data
1. Write the new parity

As every write I/O request that is submitted to the array controller by the operating system requires four I/O operations to complete, write requests submitted take four times as long to complete as a single read I/O. To derive a formula to translate I/O requests from the operating system perspective to that experienced by the spindles:  

> *Read I/O* + 4 &times; *Write I/O* = *Total I/O*  

Similarly in a RAID 1 set, when the ratio of reads to writes and the number of spindles are known, the following equation can be derived from the above equation to identify the maximum I/O that can be supported by the array (Note that total number of spindles does not include the “drive” lost to parity):  

> *IOPS per spindle* &times; (*Spindles* – 1) &times; [(*%Reads* + *%Writes*) &divide; (*%Reads* + 4 &times; *%Writes*)] = *Total IOPS*

### Introducing SANs

Expanding the complexity of the storage subsystem, when a SAN is introduced into the environment, the basic principles outlined do not change, however I/O behavior for all of the systems connected to the SAN needs to be taken into account. As one of the major advantages in using a SAN is an additional amount of redundancy over internally or externally attached storage, capacity planning now needs to take into account fault tolerance needs. Also, more components are introduced that need to be evaluated. Breaking a SAN down into the component parts:

- SCSI or Fibre Channel hard drive
- Storage unit channel backplane
- Storage units
- Storage controller module
- SAN switch(es)
- HBA(s)
- The PCI bus

When designing any system for redundancy, additional components are included to accommodate the potential of failure. It is very important, when capacity planning, to exclude the redundant component from available resources. For example, if the SAN has two controller modules, the I/O capacity of one controller module is all that should be used for total I/O throughput available to the system. This is due to the fact that if one controller fails, the entire I/O load demanded by all connected systems will need to be processed by the remaining controller. As all capacity planning is done for peak usage periods, redundant components should not be factored into the available resources and planned peak utilization should not exceed 80% saturation of the system (in order to accommodate bursts or anomalous system behavior). Similarly, the redundant SAN switch, storage unit, and spindles should not be factored into the I/O calculations.

When analyzing the behavior of the SCSI or Fibre Channel hard drive, the method of analyzing the behavior as outlined previously does not change. Although there are certain advantages and disadvantages to each protocol, the limiting factor on a per disk basis is the mechanical limitation of the hard drive.

Analyzing the channel on the storage unit is exactly the same as calculating the resources available on the SCSI bus, or bandwidth (such as 20 MB/s) divided by block size (such as 8 KB). Where this deviates from the simple previous example is in the aggregation of multiple channels. For example, if there are 6 channels, each supporting 20 MB/s maximum transfer rate, the total amount of I/O and data transfer that is available is 100 MB/s (this is correct, it is not 120 MB/s). Again, fault tolerance is a major player in this calculation, in the event of the loss of an entire channel, the system is only left with 5 functioning channels. Thus, to ensure continuing to meet performance expectations in the event of failure, total throughput for all of the storage channels should not exceed 100 MB/s (this assumes load and fault tolerance is evenly distributed across all channels). Turning this into an I/O profile is dependent on the behavior of the application. In the case of Active Directory Jet I/O, this would correlate to approximately 12,500 I/O per second (100 MB/s &divide; 8 KB per I/O).

Next, obtaining the manufacturer’s specifications for the controller modules is required in order to gain an understanding of the throughput each module can support. In this example, the SAN has two controller modules that support 7,500 I/O each. The total throughput of the system may be 15,000 IOPS if redundancy is not desired. In calculating maximum throughput in the case of failure, the limitation is the throughput of one controller, or 7,500 IOPS. This threshold is well below the 12,500 IOPS (assuming 4 KB block size) maximum that can be supported by all of the storage channels, and thus, is currently the bottleneck in the analysis. Still for planning purposes, the desired maximum I/O to be planned for would be 10,400 I/O.

When the data exits the controller module, it transits a Fibre Channel connection rated at 1 GB/s (or 1 Gigabit per second). To correlate this with the other metrics, 1 GB/s turns into 128 MB/s (1 GB/s &divide; 8 bits/byte). As this is in excess of the total bandwidth across all channels in the storage unit (100 MB/s), this will not bottleneck the system. Additionally, as this is only one of the two channels (the additional 1 GB/s Fibre Channel connection being for redundancy), if one connection fails, the remaining connection still has enough capacity to handle all the data transfer demanded.

En route to the server, the data will most likely transit a SAN switch. As the SAN switch has to process the incoming I/O request and forward it out the appropriate port, the switch will have a limit to the amount of I/O that can be handled, however, manufacturers specifications will be required to determine what that limit is. For example, if there are two switches and each switch can handle 10,000 IOPS, the total throughput will be 20,000 IOPS. Again, fault tolerance being a concern, if one switch fails, the total throughput of the system will be 10,000 IOPS. As it is desired not to exceed 80% utilization in normal operation, using no more than 8000 I/O should be the target.

Finally, the HBA installed in the server would also have a limit to the amount of I/O that it can handle. Usually, a second HBA is installed for redundancy, but just like with the SAN switch, when calculating maximum I/O that can be handled, the total throughput of *N* &ndash; 1 HBAs is what the maximum scalability of the system is.

### Caching considerations

Caches are one of the components that can significantly impact the overall performance at any point in the storage system. Detailed analysis about caching algorithms is beyond the scope of this article; however, some basic statements about caching on disk subsystems are worth illuminating:

- Caching does improved sustained sequential write I/O as it can buffer many smaller write operations into larger I/O blocks and de-stage to storage in fewer, but larger block sizes. This will reduce total random I/O and total sequential I/O, thus providing more resource availability for other I/O.
- Caching does not improve sustained write I/O throughput of the storage subsystem. It only allows for the writes to be buffered until the spindles are available to commit the data. When all the available I/O of the spindles in the storage subsystem is saturated for long periods, the cache will eventually fill up. In order to empty the cache, enough time between bursts, or extra spindles, need to be allotted in order to provide enough I/O to allow the cache to flush.

  Larger caches only allow for more data to be buffered. This means longer periods of saturation can be accommodated.

  In a normally operating storage subsystem, the operating system will experience improved write performance as the data only needs to be written to cache. Once the underlying media is saturated with I/O, the cache will fill and write performance will return to disk speed.

- When caching read I/O, the scenario where the cache is most advantageous is when the data is stored sequentially on the disk, and the cache can read-ahead (it makes the assumption that the next sector contains the data that will be requested next).
- When read I/O is random, caching at the drive controller is unlikely to provide any enhancement to the amount of data that can be read from the disk. Any enhancement is non-existent if the operating system or application-based cache size is greater than the hardware-based cache size.

  In the case of Active Directory, the cache is only limited by the amount of RAM.

### SSD considerations

SSDs are a completely different animal than spindle-based hard disks. Yet the two key criteria remain: “How many IOPS can it handle?” and “What is the latency for those IOPS?” In comparison to spindle-based hard disks, SSDs can handle higher volumes of I/O and can have lower latencies. In general and as of this writing, while SSDs are still expensive in a cost-per-Gigabyte comparison, they are very cheap in terms of cost-per-I/O and deserve significant consideration in terms of storage performance.

Considerations:

- Both IOPS and latencies are very subjective to the manufacturer designs and in some cases have been observed to be poorer performing than spindle based technologies. In short, it is more important to review and validate the manufacturer specs drive by drive and not assume any generalities.
- IOPS types can have very different numbers depending on whether it is read or write. AD DS services, in general, being predominantly read-based, will be less affected than some other application scenarios.
- “Write endurance” – this is the concept that SSD cells will eventually wear out. Various manufacturers deal with this challenge different fashions. At least for the database drive, the predominantly read I/O profile allows for downplaying the significance of this concern as the data is not highly volatile.

### Summary

One way to think about storage is picturing household plumbing. Imagine the IOPS of the media that the data is stored on is the household main drain. When this is clogged (such as roots in the pipe) or limited (it is collapsed or too small), all the sinks in the household back up when too much water is being used (too many guests). This is perfectly analogous to a shared environment where one or more systems are leveraging shared storage on an SAN/NAS/iSCSI with the same underlying media. Different approaches can be taken to resolve the different scenarios:

- A collapsed or undersized drain requires a full scale replacement and fix. This would be similar to adding in new hardware or redistributing the systems using the shared storage throughout the infrastructure.
- A “clogged” pipe usually means identification of one or more offending problems and removal of those problems. In a storage scenario this could be storage or system level backups, synchronized antivirus scans across all servers, and synchronized defragmentation software running during peak periods.

In any plumbing design, multiple drains feed into the main drain. If anything stops up one of those drains or a junction point, only the things behind that junction point back up. In a storage scenario, this could be an overloaded switch (SAN/NAS/iSCSI scenario), driver compatibility issues (wrong driver/HBA Firmware/storport.sys combination), or backup/antivirus/defragmentation. To determine if the storage “pipe” is big enough, IOPS and I/O size needs to be measured. At each joint add them together to ensure adequate “pipe diameter.”

## Appendix D - Discussion on storage troubleshooting - Environments where providing at least as much RAM as the database size is not a viable option

It is helpful to understand why these recommendations exist so that the changes in storage technology can be accommodated. These recommendations exist for two reasons. The first is isolation of IO, such that performance issues (that is, paging) on the operating system spindle do not impact performance of the database and I/O profiles. The second is that log files for AD DS (and most databases) are sequential in nature, and spindle-based hard drives and caches have a huge performance benefit when used with sequential I/O as compared to the more random I/O patterns of the operating system and almost purely random I/O patterns of the AD DS database drive. By isolating the sequential I/O to a separate physical drive, throughput can be increased. The challenge presented by today’s storage options is that the fundamental assumptions behind these recommendations are no longer true. In many virtualized storage scenarios, such as iSCSI, SAN, NAS, and Virtual Disk image files, the underlying storage media is shared across multiple hosts, thus completely negating both the “isolation of IO” and the “sequential I/O optimization” aspects. In fact these scenarios add an additional layer of complexity in that other hosts accessing the shared media can degrade responsiveness to the domain controller.

In planning storage performance, there are three categories to consider: cold cache state, warmed cache state, and backup/restore. The cold cache state occurs in scenarios such as when the domain controller is initially rebooted or the Active Directory service is restarted and there is no Active Directory data in RAM. Warm cache state is where the domain controller is in a steady state and the database is cached. These are important to note as they will drive very different performance profiles, and having enough RAM to cache the entire database does not help performance when the cache is cold. One can consider performance design for these two scenarios with the following analogy, warming the cold cache is a “sprint” and running a server with a warm cache is a “marathon.”

For both the cold cache and warm cache scenario, the question becomes how fast the storage can move the data from disk into memory. Warming the cache is a scenario where, over time, performance improves as more queries reuse data, the cache hit rate increases, and the frequency of needing to go to disk decreases. As a result the adverse performance impact of going to disk decreases. Any degradation in performance is only transient while waiting for the cache to warm and grow to the maximum, system-dependent allowed size. The conversation can be simplified to how quickly the data can be gotten off of disk, and is a simple measure of the IOPS available to Active Directory, which is subjective to IOPS available from the underlying storage. From a planning perspective, because warming the cache and backup/restore scenarios happen on an exceptional basis, normally occur off hours, and are subjective to the load of the DC, general recommendations do not exist except in that these activities be scheduled for non-peak hours.

AD DS, in most scenarios, is predominantly read IO, usually a ratio of 90% read/10% write. Read I/O often tends to be the bottleneck for user experience, and with write IO, causes write performance to degrade. As I/O to the NTDS.dit is predominantly random, caches tend to provide minimal benefit to read IO, making it that much more important to configure the storage for read I/O profile correctly.

For normal operating conditions, the storage planning goal is minimize the wait times for a request from AD DS to be returned from disk. This essentially means that the number of outstanding and pending I/O is less than or equivalent to the number of pathways to the disk. There are a variety of ways to measure this. In a performance monitoring scenario, the general recommendation is that LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Read be less than 20 ms. The desired operating threshold must be much lower, preferably as close to the speed of the storage as possible, in the 2 to 6 millisecond (.002 to .006 second) range depending on the type of storage.

Example:

![Storage latency chart](media/capacity-planning-considerations-storage-latency.png)

Analyzing the chart:

- **Green oval on the left –** The latency remains consistent at 10 ms. The load increases from 800 IOPS to 2400 IOPS. This is the absolute floor to how quickly an I/O request can be processed by the underlying storage. This is subject to the specifics of the storage solution.
- **Burgundy oval on the right –** The throughput remains flat from the exit of the green circle through to the end of the data collection while the latency continues to increase. This is demonstrating that when the request volumes exceed the physical limitations of the underlying storage, the longer the requests spend sitting in the queue waiting to be sent out to the storage subsystem.

Applying this knowledge:

- **Impact to a user querying membership of a large group –** Assume this requires reading 1 MB of data from the disk, the amount of I/O and how long it takes can be evaluated as follows:
  - Active Directory database pages are 8 KB in size. 
  - A minimum of 128 pages need to be read in from disk. 
  - Assuming nothing is cached, at the floor (10 ms) this is going to take a minimum 1.28 seconds to load the data from disk in order to return it to the client. At 20 ms, where the throughput on storage has long since maxed out and is also the recommended maximum, it will take 2.5 seconds to get the data from disk in order to return it to the end user.  
- **At what rate will the cache be warmed –** Making the assumption that the client load is going to maximize the throughput on this storage example, the cache will warm at a rate of 2400 IOPS &times; 8 KB per IO. Or, approximately 20 MB/s per second, loading about 1 GB of database into RAM every 53 seconds.

> [!NOTE]
> It is normal for short periods to observe the latencies climb when components aggressively read or write to disk, such as when the system is being backed up or when AD DS is running garbage collection. Additional head room on top of the calculations should be provided to accommodate these periodic events. The goal being to provide enough throughput to accommodate these scenarios without impacting normal function.

As can be seen, there is a physical limit based on the storage design to how quickly the cache can possibly warm. What will warm the cache are incoming client requests up to the rate that the underlying storage can provide. Running scripts to “pre-warm” the cache during peak hours will provide competition to load driven by real client requests. That can adversely affect delivering data that clients need first because, by design, it will generate competition for scarce disk resources as artificial attempts to warm the cache will load data that is not relevant to the clients contacting the DC.Процессор Information(_Total)\\"процессоров Domain Services
description: Detailed discussion of the factors to consider during capacity planning for AD DS.
ms.prod: windows-server-threshold
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: v-tea; kenbrunf
author: Teresa-Motiv
ms.date: 7/3/2019
---

# Capacity planning for Active Directory Domain Services

This topic is originally written by Ken Brumfield, Senior Premier Field Engineer at Microsoft, and provides recommendations for capacity planning for Active Directory Domain Services (AD DS).

## Goals of capacity planning

Capacity planning is not the same as troubleshooting performance incidents. They are closely related, but quite different. The goals of capacity planning are:  

- Properly implement and operate an environment 
- Minimize the time spent troubleshooting performance issues.  
  
In capacity planning, an organization might have a baseline target of 40% processor utilization during peak periods in order to meet client performance requirements and accommodate the time necessary to upgrade the hardware in the datacenter. Whereas, to be notified of abnormal performance incidents, a monitoring alert threshold might be set at 90% over a 5 minute interval.

The difference is that when a capacity management threshold is continually exceeded (a one-time event is not a concern), adding capacity (that is, adding in more or faster processors) would be a solution or scaling the service across multiple servers would be a solution. Performance alert thresholds indicate that client experience is currently suffering and immediate steps are needed to address the issue.

As an analogy: capacity management is about preventing a car accident (defensive driving, making sure the brakes are working properly, and so on) whereas performance troubleshooting is what the police, fire department, and emergency medical professionals do after an accident. This is about “defensive driving,” Active Directory-style.

Over the last several years, capacity planning guidance for scale-up systems has changed dramatically. The following changes in system architectures have challenged fundamental assumptions about designing and scaling a service:

- 64-bit server platforms  
- Virtualization  
- Increased attention to power consumption  
- SSD storage  
- Cloud scenarios  

Additionally, the approach is shifting from a server-based capacity planning exercise to a service-based capacity planning exercise. Active Directory Domain Services (AD DS), a mature distributed service that many Microsoft and third-party products use as a backend, becomes one the most critical products to plan correctly to ensure the necessary capacity for other applications to run.

### Baseline requirements for capacity planning guidance

Throughout this article, the following baseline requirements are expected:

- Readers have read and are familiar with [Performance Tuning Guidelines for Windows Server 2012 R2](https://docs.microsoft.com/previous-versions//dn529133(v=vs.85)).
- The Windows Server platform is an x64 based architecture. But even if your Active Directory environment is installed on Windows Server 2003 x86 (now beyond the end of the support lifecycle) and has a directory information tree (DIT) that is less 1.5 GB in size and that can easily be held in memory, the guidelines from this article are still applicable.
- Capacity planning is a continuous process and you should regularly review how well the environment is meeting expectations.
- Optimization will occur over multiple hardware lifecycles as hardware costs change. For example, memory becomes cheaper, the cost per core decreases, or the price of different storage options change.
- Plan for the peak busy period of the day. It is recommended to look at this in either 30 minute or hour intervals. Anything greater may hide the actual peaks and anything less may be distorted by “transient spikes.”
- Plan for growth over the course of the hardware lifecycle for the enterprise. This may include a strategy of upgrading or adding hardware in a staggered fashion, or a complete refresh every three to five years. Each will require a “guess” as how much the load on Active Directory will grow. Historical data, if collected, will help with this assessment. 
- Plan for fault tolerance. Once an estimate *N* is derived, plan for scenarios that include *N* &ndash; 1, *N* &ndash; 2, *N* &ndash; *x*.
  - Add in additional servers according to organizational need to ensure that the loss of a single or multiple servers does not exceed maximum peak capacity estimates.
  - Also consider that the growth plan and fault tolerance plan need to be integrated. For example, if one DC is required to support the load, but the estimate is that the load will be doubled in the next year and require two DCs total, there will not be enough capacity to support fault tolerance. The solution would be to start with three DCs. One could also plan to add the third DC after 3 or 6 months if budgets are tight.

    >[!NOTE]
    >Adding Active Directory-aware applications might have a noticeable impact on the DC load, whether the load is coming from the application servers or clients.

### Three-step process for the capacity planning cycle

In capacity planning, first decide what quality of service is needed. For example, a core datacenter supports a higher level of concurrency and requires more consistent experience for users and consuming applications, which requires greater attention to redundancy and minimizing system and infrastructure bottlenecks. In contrast, a satellite location with a handful of users does not need the same level of concurrency or fault tolerance. Thus, the satellite office might not need as much attention to optimizing the underlying hardware and infrastructure, which may lead to cost savings. All recommendations and guidance herein are for optimal performance, and can be selectively relaxed for scenarios with less demanding requirements.

The next question is: virtualized or physical? From a capacity planning perspective, there is no right or wrong answer; there is only a different set of variables to work with. Virtualization scenarios come down to one of two options:

- “Direct mapping” with one guest per host (where virtualization exists solely to abstract the physical hardware from the server)
- “Shared host”

Testing and production scenarios indicate that the “direct mapping” scenario can be treated identically to a physical host. “Shared host,” however, introduces a number of considerations spelled out in more detail later. The “shared host” scenario means that AD DS is also competing for resources, and there are penalties and tuning considerations for doing so.

With these considerations in mind, the capacity planning cycle is an iterative three-step process:

1. Measure the existing environment, determine where the system bottlenecks currently are, and get environmental basics necessary to plan the amount of capacity needed.
1. Determine the hardware needed according to the criteria outlined in step 1.
1. Monitor and validate that the infrastructure as implemented is operating within specifications. Some data collected in this step becomes the baseline for the next cycle of capacity planning.

### Applying the process

To optimize performance, ensure these major components are correctly selected and tuned to the application loads:

1. Memory
1. Network
1. Storage
1. Processor
1. Net Logon

The basic storage requirements of AD DS and the general behavior of well written client software allow environments with as many as 10,000 to 20,000 users to forego heavy investment in capacity planning with regards to physical hardware, as almost any modern server class system will handle the load. That said, the following table summarizes how to evaluate an existing environment in order to select the right hardware. Each component is analyzed in detail in subsequent sections to help AD DS administrators evaluate their infrastructure using baseline recommendations and environment-specific principals.

In general:

- Any sizing based on current data will only be accurate for the current environment.
- For any estimates, expect demand to grow over the lifecycle of the hardware.
- Determine whether to oversize today and grow into the larger environment, or add capacity over the lifecycle.
- For virtualization, all the same capacity planning principals and methodologies apply, except that the overhead of the virtualization needs to be added to anything domain related.
- Capacity planning, like anything that attempts to predict, is NOT an accurate science. Do not expect things to calculate perfectly and with 100% accuracy. The guidance here is the leanest recommendation; add in capacity for additional safety and continuously validate that the environment remains on target.

### Data collection summary tables

#### New environment

| Component | Estimates |
|-|-|
|Storage/Database Size|40 KB to 60 KB for each user|
|RAM|Database Size<br />Base operating system recommendations<br />Third-party applications|
|Network|1 GB|
|CPU|1000 concurrent users for each core|

#### High-level evaluation criteria

| Component | Evaluation criteria | Planning considerations |
|-|-|-|
|Storage/Database size|The section entitled “To activate logging of disk space that is freed by defragmentation” in [Storage Limits](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/cc961769(v=technet.10))| |
|Storage/ Database performance|<ul><li>"LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Read," "LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Write," "LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Transfer"</li><li>"LogicalDisk(*\<NTDS Database Drive\>*)\Reads/sec," "LogicalDisk(*\<NTDS Database Drive\>*)\Writes/sec," "LogicalDisk(*\<NTDS Database Drive\>*)\Transfers/sec"</li></ul>|<ul><li>Storage has two concerns to address<ul><li>Space available, which with the size of today’s spindle based and SSD based storage is irrelevant for most AD environments.</li> <li>Input/Output (IO) Operations available – In many environments, this is often overlooked. But it is important to evaluate only environments where there is not enough RAM to load the entire NTDS Database into memory.</li></ul><li>Storage can be a complex topic and should involve hardware vendor expertise for proper sizing. Particularly with more complex scenarios such as SAN, NAS, and iSCSI scenarios. However, in general, cost per Gigabyte of storage is often in direct opposition to cost per IO:<ul><li>RAID 5 has lower cost per Gigabyte than Raid 1, but Raid 1 has lower cost per IO</li><li>Spindle-based hard drives have lower cost per Gigabyte, but SSDs have a lower cost per IO</li></ul><li>After a restart of the computer or the Active Directory Domain Services service, the Extensible Storage Engine (ESE) cache is empty and performance will be disk bound while the cache warms.</li><li>In most environments AD is read intensive I/O in a random pattern to disks, negating much of the benefit of caching and read optimization strategies.  Plus, AD has a way larger cache in memory than most storage system caches.</li></ul>
|RAM|<ul><li>Database size</li><li>Base operating system recommendations</li><li>Third-party applications</li></ul>|<ul><li>Storage is the slowest component in a computer. The more that can be resident in RAM, the less it is necessary to go to disk.</li><li>Ensure enough RAM is allocated to store the operating system, Agents (antivirus, backup, monitoring), NTDS Database and growth over time.</li><li>For environments where maximizing the amount of RAM is not cost effective (such as a satellite locations) or not feasible (DIT is too large), reference the Storage section to ensure that storage is properly sized.</li></ul>|
|Network|<ul><li>“Network Interface(\*)\Bytes Received/sec”</li><li>“Network Interface(\*)\Bytes Sent/sec”|<ul><li>In general, traffic sent from a DC far exceeds traffic sent to a DC.</li><li>As a switched Ethernet connection is full-duplex, inbound and outbound network traffic need to be sized independently.</li><li>Consolidating the number of DCs will increase the amount of bandwidth used to send responses back to client requests for each DC, but will be close enough to linear for the site as a whole.</li><li>If removing satellite location DCs, don’t forget to add the bandwidth for the satellite DC into the hub DCs as well as use that to evaluate how much WAN traffic there will be.</li></ul>|
|CPU|<ul><li>“Logical Disk(*\<NTDS Database Drive\>*)\Avg Disk sec/Read”</li><li>“Process(lsass)\\% Processor Time”</li></ul>|<ul><li>After eliminating storage as a bottleneck, address the amount of compute power needed.</li><li>While not perfectly linear, the number of processor cores consumed across all servers within a specific scope (such as a site) can be used to gauge how many processors are necessary to support the total client load. Add the minimum necessary to maintain the current level of service across all the systems within the scope.</li><li>Changes in processor speed, including power management related changes, impact numbers derived from the current environment. Generally, it is impossible to precisely evaluate how going from a 2.5 GHz processor to a 3 GHz processor will reduce the number of CPUs needed.</li></ul>|
|NetLogon|<ul><li>“Netlogon(\*)\Semaphore Acquires”</li><li>“Netlogon(\*)\Semaphore Timeouts”</li><li>“Netlogon(\*)\Average Semaphore Hold Time”</li></ul>|<ul><li>Net Logon Secure Channel/MaxConcurrentAPI only affects environments with NTLM authentications and/or PAC Validation. PAC Validation is on by default in operating system versions before Windows Server 2008. This is a client setting, so the DCs will be impacted until this is turned off on all client systems.</li><li>Environments with significant cross trust authentication, which includes intra-forest trusts, have greater risk if not sized properly.</li><li>Server consolidations will increase concurrency of cross-trust authentication.</li><li>Surges need to be accommodated, such as cluster fail-overs, as users re-authenticate en masse to the new cluster node.</li><li>Individual client systems (such as a cluster) might need tuning too.</li></ul>|

## Planning

For a long time, the community’s recommendation for sizing AD DS has been to “put in as much RAM as the database size.” For the most part, that recommendation is all that most environments needed to be concerned about. But the ecosystem consuming AD DS has gotten much bigger, as have the AD DS environments themselves, since its introduction in 1999. Although the increase in compute power and the switch from x86 architectures to x64 architectures has made the subtler aspects of sizing for performance irrelevant to a larger set of customers running AD DS on physical hardware, the growth of virtualization has reintroduced the tuning concerns to a larger audience than before.

The following guidance is thus about how to determine and plan for the demands of Active Directory as a service regardless of whether it is deployed in a physical, a virtual/physical mix, or a purely virtualized scenario. As such, we will break down the evaluation to each of the four main components: storage, memory, network, and processor. In short, in order to maximize performance on AD DS, the goal is to get as close to processor bound as possible.

## RAM

Simply, the more that can be cached in RAM, the less it is necessary to go to disk. To maximize the scalability of the server the minimum amount of RAM should be the sum of the current database size, the total SYSVOL size, the operating system recommended amount, and the vendor recommendations for the agents (antivirus, monitoring, backup, and so on). An additional amount should be added to accommodate growth over the lifetime of the server. This will be environmentally subjective based on estimates of database growth based on environmental changes.

For environments where maximizing the amount of RAM is not cost effective (such as a satellite locations) or not feasible (DIT is too large), reference the Storage  section to ensure that storage is properly designed.

A corollary that comes up in the general context in sizing memory is sizing of the page file. In the same context as everything else memory related, the goal is to minimize going to the much slower disk. Thus the question should go from, “how should the page file be sized?” to “how much RAM is needed to minimize paging?” The answer to the latter question is outlined in the rest of this section. This leaves most of the discussion for sizing the page file to the realm of general operating system recommendations and the need to configure the system for memory dumps, which are unrelated to AD DS performance.

### Evaluating

The amount of RAM that a domain controller (DC) needs is actually a complex exercise for these reasons:

- High potential for error when trying to use an existing system to gauge how much RAM is needed as LSASS will trim under memory pressure conditions, artificially deflating the need.
- The subjective fact that an individual DC only needs to cache what is “interesting” to its clients. This means that the data that needs to be cached on a DC in a site with only an Exchange server will be very different than the data that needs to be cached on a DC that only authenticates users.
- The labor to evaluate RAM for each DC on a case-by-case basis is prohibitive and changes as the environment changes.
- The criteria behind the recommendation will help to make informed decisions: 
- The more that can be cached in RAM, the less it is necessary to go to disk. 
- Storage is by far the slowest component of a computer. Access to data on spindle-based and SSD storage media is on the order of 1,000,000x slower than access to data in RAM.

Thus, in order to maximize the scalability of the server, the minimum amount of RAM is the sum of the current database size, the total SYSVOL size, the operating system recommended amount, and the vendor recommendations for the agents (antivirus, monitoring, backup, and so on). Add additional amounts to accommodate growth over the lifetime of the server. This will be environmentally subjective based on estimates of database growth. However, for satellite locations with a small set of end users, these requirements can be relaxed as these sites will not need to cache as much to service most of the requests.

For environments where maximizing the amount of RAM is not cost effective (such as a satellite locations) or not feasible (DIT is too large), reference the Storage section to ensure that storage is properly sized.

> [!NOTE]
> A corollary while sizing memory is sizing of the page file. Because the goal is to minimize going to the much slower disk, the question goes from “how should the page file be sized?” to “how much RAM is needed to minimize paging?” The answer to the latter question is outlined in the rest of this section. This leaves most of the discussion for sizing the page file to the realm of general operating system recommendations and the need to configure the system for memory dumps, which are unrelated to AD DS performance.

### Virtualization considerations for RAM

Avoid memory over-commit at the host. The fundamental goal behind optimizing the amount of RAM is to minimize the amount of time spent going to disk. In virtualization scenarios, the concept of memory over-commit exists where more RAM is allocated to the guests then exists on the physical machine. This in and of itself is not a problem. It becomes a problem when the total memory actively used by all the guests exceeds the amount of RAM on the host and the underlying host starts paging. Performance becomes disk-bound in cases where the domain controller is going to the NTDS.dit to get data, or the domain controller is going to the page file to get data, or the host is going to disk to get data that the guest thinks is in RAM.

### Calculation summary example

|Component|Estimated memory (example)|
|-|-|
|Base operating system recommended RAM (Windows Server 2008)|2 GB|
|LSASS internal tasks|200 MB|
|Monitoring agent|100 MB|
|Antivirus|100 MB|
|Database (Global Catalog)|8.5 GB are you sure ???|
|Cushion for backup to run, administrators to log on without impact|1 GB|
|Total|12 GB|

**Recommended: 16 GB**

Over time, the assumption can be made that more data will be added to the database and the server will probably be in production for 3 to 5 years. Based on an estimate of growth of 33%, 16 GB would be a reasonable amount of RAM to put in a physical server. In a virtual machine, given the ease with which settings can be modified and RAM can be added to the VM, starting at 12 GB with the plan to monitor and upgrade in the future is reasonable.

## Network

### Evaluating
This section is less about evaluating the demands regarding replication traffic, which is focused on traffic traversing the WAN and is thoroughly covered in [Active Directory Replication Traffic](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742457(v=technet.10)), than it is about evaluating total bandwidth and network capacity needed, inclusive of client queries, Group Policy applications, and so on. For existing environments, this can be collected by using performance counters “Network Interface(\*)\Bytes Received/sec,” and “Network Interface(\*)\Bytes Sent/sec.” Sample intervals for Network Interface counters in either 15, 30, or за 60 минутutes. Anything less will generally be too volatile for good measurements; anything greater will smooth out daily peeks excessively.

> [!NOTE]
> Generally, the majority of network traffic on a DC is outbound as the DC responds to client queries. This is the reason for the focus on outbound traffic, though it is recommended to evaluate each environment for inbound traffic also. The same approaches can be used to address and review inbound network traffic requirements. For more information, see Knowledge Base article [929851: The default dynamic port range for TCP/IP has changed in Windows Vista and in Windows Server 2008](http://support.microsoft.com/kb/929851).

### Bandwidth needs

Planning for network scalability covers two distinct categories: the amount of traffic and the CPU load from the network traffic. Each of these scenarios is straight-forward compared to some of the other topics in this article.

In evaluating how much traffic must be supported, there are two unique categories of capacity planning for AD DS in terms of network traffic. The first is replication traffic that traverses between domain controllers and is covered thoroughly in the reference [Active Directory Replication Traffic](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742457(v=technet.10)) and is still relevant to current versions of AD DS. The second is the intrasite client-to-server traffic. One of the simpler scenarios to plan for, intrasite traffic predominantly receives small requests from clients relative to the large amounts of data sent back to the clients. 100 MB will generally be adequate in environments up to 5,000 users per server, in a site. Using a 1 GB network adapter and Receive Side Scaling (RSS) support is recommended for anything above 5,000 users. To validate this scenario, particularly in the case of server consolidation scenarios, look at Network Interface(\*)\Bytes/sec across all the DCs in a site, add them together, and divide by the target number of domain controllers to ensure that there is adequate capacity. The easiest way to do this is to use the “Stacked Area” view in Windows Reliability and Performance Monitor (formerly known as Perfmon), making sure all of the counters are scaled the same.

Consider the following example (also known as, a really, really complex way to validate that the general rule is applicable to a specific environment). The following assumptions are made:

- The goal is to reduce the footprint to as few servers as possible. Ideally, one server will carry the load and an additional server is deployed for redundancy (*N* + 1 scenario). 
- In this scenario, the current network adapter supports only 100 MB and is in a switched environment.  
  The maximum target network bandwidth utilization is 60% in an N scenario (loss of a DC).
- Each server has about 10,000 clients connected to it.

Knowledge gained from the data in the chart (Network Interface(\*)\Bytes Sent/sec):

1. The business day starts ramping up around 5:30 and winds down at 7:00 PM.
1. The peak busiest period is from 8:00 AM to 8:15 AM, with greater than 25 Bytes sent/sec on the busiest DC.  
   > [!NOTE]
   > All performance data is historical. So the peak data point at 8:15 indicates the load from 8:00 to 8:15.
1. There are spikes before 4:00 AM, with more than 20 Bytes sent/sec on the busiest DC, which could indicate either load from different time zones or background infrastructure activity, such as backups. Since the peak at 8:00 AM exceeds this activity, it is not relevant.
1. There are five Domain Controllers in the site.
1. The max load is about 5.5 MB/s per DC, which represents 44% of the 100 MB connection. Using this data, it can be estimated that the total bandwidth needed between 8:00 AM and 8:15 AM is 28 MB/s.
   >[!NOTE]
   >Be careful with the fact that Network Interface sent/receive counters are in bytes and network bandwidth is measured in bits. 100 MB &divide; 8 = 12.5 MB, 1 GB &divide; 8 = 128 MB.
  
Conclusions:

1. This current environment does meet the N+1 level of fault tolerance at 60% target utilization. Taking one system offline will shift the bandwidth per server from about 5.5 MB/s (44%) to about 7 MB/s (56%).
1. Based on the previously stated goal of consolidating to one server, this both exceeds the maximum target utilization and theoretically the possible utilization of a 100 MB connection.
1. With a 1 GB connection this will represent 22% of the total capacity.
1. Under normal operating conditions in the *N* + 1 scenario, client load will be relatively evenly distributed at about 14 MB/s per server or 11% of total capacity.
1. To ensure that capacity is adequate during unavailability of a DC, the normal operating targets per server would be about 30% network utilization or 38 MB/s per server. Failover targets would be 60% network utilization or 72 MB/s per server.  
  
In short, the final deployment of systems must have a 1 GB network adapter and be connected to a network infrastructure that will support said load. A further note is that given the amount of network traffic generated, the CPU load from network communications can have a significant impact and limit the maximum scalability of AD DS. This same process can be used to estimate the amount of inbound communication to the DC. But given the predominance of outbound traffic relative to inbound traffic, it is an academic exercise for most environments. Ensuring hardware support for RSS is important in environments with greater than 5,000 users per server. For scenarios with high network traffic, balancing of interrupt load can be a bottleneck. This can be detected by Processor(\*)\% Interrupt Time being unevenly distributed across CPUs. RSS enabled NICs can mitigate this limitation and increase scalability.

> [!NOTE]
> A similar approach can be used to estimate the additional capacity necessary when consolidating data centers, or retiring a domain controller in a satellite location. Simply collect the outbound and inbound traffic to clients and that will be the amount of traffic that will now be present on the WAN links.  
>  
> In some cases, you might experience more traffic than expected because traffic is slower, such as when certificate checking fails to meet aggressive time-outs on the WAN. For this reason, WAN sizing and utilization should be an iterative, ongoing process.

### Virtualization considerations for network bandwidth

It is easy to make recommendations for a physical server: 1 GB for servers supporting greater than 5000 users. Once multiple guests start sharing an underlying virtual switch infrastructure, additional attention is necessary to ensure that the host has adequate network bandwidth to support all the guests on the system, and thus requires the additional rigor. This is nothing more than an extension of ensuring the network infrastructure into the host machine. This is regardless whether the network is inclusive of the domain controller running as a virtual machine guest on a host with the network traffic going over a virtual switch, or whether connected directly to a physical switch. The virtual switch is just one more component where the uplink needs to support the amount of data being transmitted. Thus the physical host physical network adapter linked to the switch should be able to support the DC load plus all other guests sharing the virtual switch connected to the physical network adapter.

### Calculation summary example

|System|Peak bandwidth|
|-|-|
DC 1|6.5 MB/s|
DC 2|6.25 MB/s|
|DC 3|6.25 MB/s|
|DC 4|5.75 MB/s|
|DC 5|4.75 MB/s|
|Total|28.5 MB/s|

**Recommended: 72 MB/s** (28.5 MB/s divided by 40 %)

|Target system(s) count|Total bandwidth (from above)|
|-|-|
|2|28.5 MB/s|
|Resulting normal behavior|28.5 &divide; 2 = 14.25 MB/s|

As always, over time the assumption can be made that client load will increase and this growth should be planned for as best as possible. The recommended amount to plan for would allow for an estimated growth in network traffic of 50%.

## Storage

Planning storage constitutes two components:

- Capacity, or storage size
- Performance

A great amount of time and documentation is spent on planning capacity, leaving performance often completely overlooked. With current hardware costs, most environments are not large enough that either of these is actually a concern, and the recommendation to “put in as much RAM as the database size” usually covers the rest, though it may be overkill for satellite locations in larger environments.

### Sizing

#### Evaluating for storage

Compared to 13 years ago when Active Directory was introduced, a time when 4 GB and 9 GB drives were the most common drive sizes, sizing for Active Directory is not even a consideration for all but the largest environments. With the smallest available hard drive sizes in the 180 GB range, the entire operating system, SYSVOL, and NTDS.dit can easily fit on one drive. As such, it is recommended to deprecate heavy investment in this area.

The only recommendation for consideration is to ensure that 110% of the NTDS.dit size is available in order to enable defrag. Additionally, accommodations for growth over the life of the hardware should be made.

The first and most important consideration is evaluating how large the NTDS.dit and SYSVOL will be. These measurements will lead into sizing both fixed disk and RAM allocation. Due to the (relatively) low cost of these components, the math does not need to be rigorous and precise. Content about how to evaluate this for both existing and new environments can be found in the [Data Storage](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/cc961771(v=technet.10)) series of articles. Specifically, refer to the following articles:

- **For existing environments &ndash;** The section titled “To activate logging of disk space that is freed by defragmentation” in the article [Storage Limits](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc961769(v=technet.10)).
- **For new environments &ndash;** The article titled [Growth Estimates for Active Directory Users and Organizational Units](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc961779(v=technet.10)).

  > [!NOTE]
  > The articles are based on data size estimates made at the time of the release of Active Directory in Windows 2000. Use object sizes that reflect the actual size of objects in your environment.

When reviewing existing environments with multiple domains, there may be variations in database sizes. Where this is true, use the smallest global catalog (GC) and non-GC sizes.  

The database size can vary between operating system versions. DCs that run earlier operating systems such as Windows Server 2003 has a smaller database size than a DC that runs a later operating system such as Windows Server 2008 R2, especially when features such Active Directory Recycle Bin or Credential Roaming are enabled.

> [!NOTE]  
  >
>- For new environments, notice that the estimates in Growth Estimates for Active Directory Users and Organizational Units indicate that 100,000 users (in the same domain) consume about 450 MB of space. Please note that the attributes populated can have a huge impact on the total amount. Attributes will be populated on many objects by both third-party and Microsoft products, including Microsoft Exchange Server and Lync. An evaluation based on the portfolio of the products in the environment is preferred, but the exercise of detailing out the math and testing for precise estimates for all but the largest environments may not actually be worth significant time and effort.
>- Ensure that 110% of the NTDS.dit size is available as free space in order to enable offline defrag, and plan for growth over a three to five year hardware lifespan. Given how cheap storage is, estimating storage at 300% the size of the DIT as storage allocation is safe to accommodate growth and the potential need for offline defrag.

#### Virtualization considerations for storage

In a scenario where multiple Virtual Hard Disk (VHD) files are being allocated on a single volume use a fixed sized disk of at least 210% (100% of the DIT + 110% free space) the size of the DIT to ensure that there is adequate space reserved.  

#### Calculation summary example

|Data collected from evaluation phase| |
|-|-|
|NTDS.dit size|35 GB|
|Modifier to allow for offline defrag|2.1|
|Total storage needed|73.5 GB|

> [!NOTE]
> This storage needed is in addition to the storage needed for SYSVOL, operating system, page file, temporary files, local cached data (such as installer files), and applications.

### Storage performance

#### Evaluating performance of storage

As the slowest component within any computer, storage can have the biggest adverse impact on client experience. For those environments large enough for which the RAM sizing recommendations are not feasible, the consequences of overlooking planning storage for performance can be devastating.  Also, the complexities and varieties of storage technology further increase the risk of failure as the relevance of long standing best practices of “put operating system, logs, and database” on separate physical disks is limited in it’s useful scenarios.  This is because the long standing best practice is based on the assumption that is that a “disk” is a dedicated spindle and this allowed I/O to be isolated.  This assumptions that make this true are no longer relevant with the introduction of:

- New storage types and virtualized and shared storage scenarios
- Shared spindles on a Storage Area Network (SAN)
- VHD file on a SAN or network-attached storage
- Solid State Drives
- Tiered storage architectures (i.e. SSD storage tier caching larger spindle based storage)

In short, the end goal of all storage performance efforts, regardless of underlying storage architecture and design, is to ensure the needed amount of Input/Output Operations per Second (IOPS) are available and that those IOPS happen within an acceptable time frame. This section covers how to evaluate what AD DS demands of the underlying storage in order to ensure storage solutions are properly designed.  Given the variability of today’s storage technologies, it is best to work with the storage vendors to ensure adequate IOPS.  For those scenarios with locally attached storage, reference the Appendix C for the basics in how to design traditional local storage scenarios.  This principals are generally applicable to more complex storage tiers and will also help in dialog with the vendors supporting backend storage solutions.

- Given the wide breadth of storage options available, it is recommended to engage the expertise of hardware support teams or vendors to ensure that the specific solution meets the needs of AD DS. The following numbers are the information that would be provided to the storage specialists.

For environments where the database is too large to be held in RAM, use the performance counters to determine how much I/O needs to be supported:

- LogicalDisk(\*)\Avg Disk sec/Read (for example, if NTDS.dit is stored on the D:/ drive, the full path would be LogicalDisk(D:)\Avg Disk sec/Read)
- LogicalDisk(\*)\Avg Disk sec/Write
- LogicalDisk(\*)\Avg Disk sec/Transfer
- LogicalDisk(\*)\Reads/sec
- LogicalDisk(\*)\Writes/sec
- LogicalDisk(\*)\Transfers/sec

These should be sampled in 15/30/60 minute intervals to benchmark the demands of the current environment.

#### Evaluating the results

> [!NOTE]
> The focus is on reads from the database as this is usually the most demanding component, the same logic can be applied to writes to the log file by substituting LogicalDisk(*\<NTDS Log\>*)\Avg Disk sec/Write and LogicalDisk(*\<NTDS Log\>*)\Writes/sec):
>  
> - LogicalDisk(*\<NTDS\>*)\Avg Disk sec/Read indicates whether or not the current storage is adequately sized.  If the results are roughly equal to the Disk Access Time for the disk type, LogicalDisk(*\<NTDS\>*)\Reads/sec is a valid measure.  Check the manufacturer specifications for the storage on the back end, but good ranges for LogicalDisk(*\<NTDS\>*)\Avg Disk sec/Read would roughly be:
>   - 7200 – 9 to 12.5 milliseconds (ms)
>   - 10,000 – 6 to 10 ms
>   - 15,000 – 4 to 6 ms  
>   - SSD – 1 to 3 ms  
>   - >[!NOTE]
>     >Recommendations exist stating that storage performance is degraded at 15ms to 20ms (depending on source).  The difference between the above values and the other guidance is that the above values are the normal operating range.  The other recommendations are troubleshooting guidance to identify when client experience significantly degrades and becomes noticeable.  Reference Appendix C for a deeper explanation.
> - LogicalDisk(*\<NTDS\>*)\Reads/sec is the amount of I/O that is being performed.
>   - If LogicalDisk(*\<NTDS\>*)\Avg Disk sec/Read is within the optimal range for the backend storage, LogicalDisk(*\<NTDS\>*)\Reads/sec can be used directly to size the storage.
>   - If LogicalDisk(*\<NTDS\>*)\Avg Disk sec/Read is not within the optimal range for the backend storage, additional I/O is needed according to the following formula:
>     > (LogicalDisk(*\<NTDS\>*)\Avg Disk sec/Read) &divide; (Physical Media Disk Access Time) &times; (LogicalDisk(*\<NTDS\>*)\Avg Disk sec/Read)

Considerations:

- Note that if the server is configured with a sub-optimal amount of RAM, these values will be inaccurate for planning purposes.  They will be erroneously on the high side and can still be used as a worst case scenario.
- Adding/Optimizing RAM specifically will drive a decrease in the amount of read I/O (LogicalDisk(*\<NTDS\>*)\Reads/Sec.  This means the storage solution may not have to be as robust as initially calculated.  Unfortunately, anything more specific than this general statement is environmentally dependent on client load and general guidance cannot be provided.  The best option is to adjust storage sizing after optimizing RAM.

#### Virtualization considerations for performance

Similar to all of the preceding virtualization discussions, the key here is to ensure that the underlying shared infrastructure can support the DC load plus the other resources using the underlying shared media and all pathways to it. This is true whether a physical domain controller is sharing the same underlying media on a SAN, NAS, or iSCSI infrastructure as other servers or applications, whether it is a guest using pass through access to a SAN, NAS, or iSCSI infrastructure that shares the underlying media, or if the guest is using a VHD file that resides on shared media locally or a SAN, NAS, or iSCSI infrastructure. The planning exercise is all about making sure that the underlying media can support the total load of all consumers.

Also, from a guest perspective, as there are additional code paths that must be traversed, there is a performance impact to having to go through a host to access any storage. Not surprisingly, storage performance testing indicates that the virtualizing has an impact on throughput that is subjective to the processor utilization of the host system (see Appendix A: CPU Sizing Criteria), which is obviously influenced by the resources of the host demanded by the guest. This contributes to the virtualization considerations regarding processing needs in a virtualized scenario (see [Virtualization considerations for processing](#virtualization-considerations-for-processing)).

Making this more complex is that there are a variety of different storage options that are available that all have different performance impacts. As a safe estimate when migrating from physical to virtual, use a multiplier of 1.10 to adjust for different storage options for virtualized guests on Hyper-V, such as pass-through storage, SCSI Adapter, or IDE. The adjustments that need to be made when transferring between the different storage scenarios are irrelevant as to whether the storage is local, SAN, NAS, or iSCSI.

#### Calculation summary example

Determining the amount of I/O needed for a healthy system under normal operating conditions:

- LogicalDisk(*\<NTDS Database Drive\>*)\Transfers/sec during the peak period 15 minute period 
- To determine the amount of I/O needed for storage where the capacity of the underlying storage is exceeded:
  >*Needed IOPS* = (LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Read &divide; *\<Target Avg Disk sec/Read\>*) &times; LogicalDisk(*\<NTDS Database Drive\>*)\Read/sec

|Counter|Value|
|-|-|
|Actual LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Transfer|.02 seconds (20 milliseconds)|
|Target LogicalDisk(*\<NTDS Database Drive\>*)\Avg Disk sec/Transfer|.01 seconds|
|Multiplier for change in available IO|0.02 &divide; 0.01 = 2|  
  
|Value name|Value|
|-|-|
|LogicalDisk(*\<NTDS Database Drive\>*)\Transfers/sec|400|
|Multiplier for change in available IO|2|
|Total IOPS needed during peak period|800|

To determine the rate at which the cache is desired to be warmed:

- Determine the maximum acceptable time to warm the cache. It is either the amount of time that it should take to load the entire database from disk, or for scenarios where the entire database cannot be loaded in RAM, this would be the maximum time to fill RAM.
- Determine the size of the database, excluding white space.  For more information, see [Evaluating for storage](#evaluating-for-storage).  
- Divide the database size by 8 KB; that will be the total IOs necessary to load the database.
- Divide the total IOs by the number of seconds in the defined time frame.

Note that the rate calculated, while accurate, will not be exact because previously loaded pages are evicted if ESE is not configured to have a fixed cache size, and AD DS by default uses variable cache size.

|Data points to collect|Values
|-|-|
|Maximum acceptable time to warm|10 minutes (600 seconds)
|Database size|2 GB|  
  
|Calculation step|Formula|Result|
|-|-|-|
|Calculate size of database in pages|(2 GB &times; 1024 &times; 1024) = *Size of database in KB*|2,097,152 KB|
|Calculate number of pages in database|2,097,152 KB &divide; 8 KB = *Number of pages*|262,144 pages|
|Calculate IOPS necessary to fully warm the cache|262,144 pages &divide; 600 seconds = *IOPS needed*|437 IOPS|

## Processing

### Evaluating Active Directory processor usage

For most environments, after storage, RAM, and networking are properly tuned as described in the Planning section, managing the amount of processing capacity will be the component that deserves the most attention. There are two challenges in evaluating CPU capacity needed:

- Whether or not the applications in the environment are being well-behaved in a shared services infrastructure, and is discussed in the section titled “Tracking Expensive and Inefficient Searches” in the article Creating More Efficient Microsoft Active Directory-Enabled Applications or migrating away from down-level SAM calls to LDAP calls.  
  
  In larger environments, the reason this is important is that poorly coded applications can drive volatility in CPU load, “steal” an inordinate amount of CPU time from other applications, artificially drive up capacity needs, and unevenly distribute load against the DCs.  
- As AD DS is a distributed environment with a large variety of potential clients, estimating the expense of a “single client” is environmentally subjective due to usage patterns and the type or quantity of applications leveraging AD DS. In short, much like the networking section, for broad applicability, this is better approached from the perspective of evaluating the total capacity needed in the environment.

For existing environments, as storage sizing was discussed previously, the assumption is made that storage is now properly sized and thus the data regarding processor load is valid. To reiterate, it is critical to ensure that the bottleneck in the system is not the performance of the storage. When a bottleneck exists and the processor is waiting, there are idle states that will go away once the bottleneck is removed.  As processor wait states are removed, by definition, CPU utilization increases as it no longer has to wait on the data. Thus, collect performance counters “Logical Disk(*\<NTDS Database Drive\>*)\Avg Disk sec/Read” and “Process(lsass)\\% Processor Time”. The data in “Process(lsass)\\% Processor Time” will be artificially low if “Logical Disk(*\<NTDS Database Drive\>*)\Avg Disk sec/Read” exceeds 10 to 15 ms, which is a general threshold that Microsoft support uses for troubleshooting storage-related performance issues. As before, it is recommended that sample intervals be either 15, 30, or 60 minutes. Anything less will generally be too volatile for good measurements; anything greater will smooth out daily peeks excessively.

### Introduction

In order to plan capacity planning for domain controllers, processing power requires the most attention and understanding. When sizing systems to ensure maximum performance, there is always a component that is the bottleneck and in a properly sized Domain Controller this will be the processor.

Similar to the networking section where the demand of the environment is reviewed on a site-by-site basis, the same must be done for the compute capacity demanded. Unlike the networking section, where the available networking technologies far exceed the normal demand, pay more attention to sizing CPU capacity.  As any environment of even moderate size; anything over a few thousand concurrent users can put significant load on the CPU.

Unfortunately, due to the huge variability of client applications that leverage AD, a general estimate of users per CPU is woefully inapplicable to all environments. Specifically, the compute demands are subject to user behavior and application profile. Therefore, each environment needs to be individually sized.

#### Target site behavior profile

As mentioned previously, when planning capacity for an entire site, the goal is to target a design with an *N* + 1 capacity design, such that failure of one system during the peak period will allow for continuation of service at a reasonable level of quality. That means that in an “*N*” scenario, load across all the boxes should be less than 100% (better yet, less than 80%) during the peak periods.

Additionally, if the applications and clients in the site are using best practices for locating domain controllers (that is, using the [DsGetDcName function](http://msdn.microsoft.com/en-us/library/windows/desktop/ms675983(v=vs.85).aspx)), the clients should be relatively evenly distributed with minor transient spikes due to any number of factors.

In the next example, the following assumptions are made:

- Each of the five DCs in the site has four of CPUs.
- Total target CPU usage during business hours is 40% under normal operating conditions (“*N* + 1”) and 60 % otherwise (“*N*”). During non-business hours, the target CPU usage is 80% because backup software and other maintenance are expected to consume all available resources.

![CPU usage chart](media/capacity-planning-considerations-cpu-chart.png)

Analyzing the data in the chart (Processor Information(_Total)\% Processor Utility) for each of the DCs:

- For the most part, the load is relatively evenly distributed which is what would be expected when clients use DC locator and have well written searches. 
- There are a number of five-minute spikes of 10%, with some as large as 20%. Generally, unless they cause the capacity plan target to be exceeded, investigating these is not worthwhile.  
- The peak period for all systems is between about 8:00 AM and 9:15 AM. With the smooth transition from about 5:00 AM through about 5:00 PM, this is generally indicative of the business cycle. The more randomized spikes of CPU usage on a box-by-box scenario between 5:00 PM and 4:00 AM would be outside of the capacity planning concerns.

  >[!NOTE]
  >On a well-managed system, said spikes are might be backup software running, full system antivirus scans, hardware or software inventory, software or patch deployment, and so on. Because they fall outside the peak user business cycle, the targets are not exceeded.

- As each system is about 40% and all systems have the same numbers of CPUs, should one fail or be taken offline, the remaining systems would run at an estimated 53% (System D's 40% load is evenly split and added to System A's and System C’s existing 40% load). For a number of reasons, this linear assumption is NOT perfectly accurate, but provides enough accuracy to gauge.  

  **Alternate scenario –** Two domain controllers running at 40%: One domain controller fails, estimated CPU on the remaining one would be an estimated 80%. This far exceeds the thresholds outlined above for capacity plan and also starts to severely limit the amount of head room for the 10% to 20% seen in the load profile above, which means that the spikes would drive the DC to 90% to 100% during the “*N*” scenario and definitely degrade responsiveness.

### Calculating CPU demands

The “Process\\% Processor Time” performance object counter sums the total amount of time that all of the threads of an application spend on the CPU and divides by the total amount of system time that has passed. The effect of this is that a multi-threaded application on a multi-CPU system can exceed 100% CPU time, and would be interpreted VERY differently than “Processor Information\\% Processor Utility”. In practice the “Process(lsass)\\% Processor Time” can be viewed as the count of CPUs running at 100% that are necessary to support the process’s demands. A value of 200% means that 2 CPUs, each at 100%, are needed to support the full AD DS load. Although a CPU running at 100% capacity is the most cost efficient from the perspective of money spent on CPUs and power and energy consumption, for a number of reasons detailed in Appendix A, better responsiveness on a multi-threaded system occurs when the system is not running at 100%.

To accommodate transient spikes in client load, it is recommended to target a peak period CPU of between 40% and 60% of system capacity. Working with the example above, that would mean that between 3.33 (60% target) and 5 (40% target) CPUs would be needed for the AD DS (lsass process) load. Additional capacity should be added in according to the demands of the base operating system and other agents required (such as antivirus, backup, monitoring, and so on). Although the impact of agents needs to be evaluated on a per environment basis, an estimate of between 5% and 10% of a single CPU can be made. In the current example, this would suggest that between 3.43 (60% target) and 5.1 (40% target) CPUs are necessary during peak periods.

The easiest way to do this is to use the “Stacked Area” view in Windows Reliability and Performance Monitor (perfmon), making sure all of the counters are scaled the same.

Assumptions:

- Goal is to reduce footprint to as few servers as possible. Ideally, one server would carry the load and an additional server added for redundancy (*N* + 1 scenario).

![Processor time chart for lsass process (over all processors)](media/capacity-planning-considerations-proc-time-chart.png)

Knowledge gained from the data in the chart (Process(lsass)\\% Processor Time):

- The business day starts ramping up around 7:00 and decreases at 5:00 PM.
- The peak busiest period is from 9:30 AM to 11:00 AM. 
  > [!NOTE]
  > All performance data is historical. The peak data point at 9:15 indicates the load from 9:00 to 9:15.
- There are spikes before 7:00 AM which could indicate either load from different time zones or background infrastructure activity, such as backups. Because the peak at 9:30 AM exceeds this activity, it is not relevant.
- There are three domain controllers in the site.

At maximum load, lsass consumes about 485% of one CPU, or 4.85 CPUs running at 100%. As per the math earlier, this means the site needs about 12.25 CPUs for AD DS. Add in the above suggestions of 5% to 10% for background processes and that means replacing the server today would need approximately 12.30 to 12.35 CPUs to support the same load. An environmental estimate for growth now needs to be factored in.

### When to tune LDAP weights

There are several scenarios where tuning [LdapSrvWeight](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc957291(v=technet.10)) should be considered. Within the context of capacity planning, this would be done when the application or user loads are not evenly balanced, or the underlying systems are not evenly balanced in terms of capability. Reasons to do so beyond capacity planning are outside of the scope of this article.

There are two common reasons to tune LDAP Weights:

- The PDC emulator is an example that affects every environment for which user or application load behavior is not evenly distributed. As certain tools and actions target the PDC emulator, such as the Group Policy management tools, second attempts in the case of authentication failures, trust establishment, and so on, CPU resources on the PDC emulator may be more heavily demanded than elsewhere in the site.
  - It is only useful to tune this if there is a noticeable difference in CPU utilization in order  to reduce the load on the PDC emulator and increase the load on other domain controllers will allow a more even distribution of load.
  - In this case, set LDAPSrvWeight between 50 and 75 for the PDC emulator.
- Servers with differing counts of CPUs (and speeds) in a site.  For example, say there are two eight-core servers and one four-core server.  The last server has half the processors of the other two servers.  This means that a well distributed client load will increase the average CPU load on the four-core box to roughly twice that of the eight-core boxes.
  - For example, the two eight-core boxes would be running at 40% and the four-core box would be running at 80%.
  - Also, consider the impact of loss of one eight-core box in this scenario, specifically the fact that the four-core box would now be overloaded.

#### Example 1 - PDC

| |Utilization with defaults|New LdapSrvWeight|Estimated new utilization|
|-|-|-|-|
|DC 1 (PDC emulator)|53%|57|40%|
|DC 2|33%|100|40%|
|DC 3|33%|100|40%|

The catch here is that if the PDC emulator role is transferred or seized, particularly to another domain controller in the site, there will be a dramatic increase on the new PDC emulator.

Using the example from the section [Target site behavior profile](#target-site-behavior-profile), an assumption was made that all three domain controllers in the site had four CPUs. What should happen, under normal conditions, if one of the domain controllers had eight CPUs? There would be two domain controllers at 40% utilization and one at 20% utilization. While this is not bad, there is an opportunity to balance the load a little bit better. Leverage LDAP weights to accomplish this.  An example scenario would be:

#### Example 2 - Differing CPU counts

| |Processor Information\\ %&nbsp;Processor Utility(_Total)<br />Utilization with defaults|New LdapSrvWeight|Estimated new utilization|
|-|-|-|-|
|4-CPU DC 1|40|100|30%|
|4-CPU DC 2|40|100|30%|
|8-CPU DC 3|20|200|30%|

Be very careful with these scenarios though. As can be seen above, the math looks really nice and pretty on paper. But throughout this article, planning for an “*N* + 1” scenario is of paramount importance. The impact of one DC going offline must be calculated for every scenario. In the immediately preceding scenario where the load distribution is even, in order to ensure a 60% load during an “*N*” scenario, with the load balanced evenly across all servers, the distribution will be fine as the ratios stay consistent. Looking at the PDC emulator tuning scenario, and in general any scenario where user or application load is unbalanced, the effect is very different:

| |Tuned Utilization|New LdapSrvWeight|Estimated New Utilization|
|-|-|-|-|
|DC 1 (PDC emulator)|40%|85|47%|
|DC 2|40%|100|53%|
|DC 3|40%|100|53%|

### Virtualization considerations for processing

There are two layers of capacity planning that need to be done in a virtualized environment. At the host level, similar to the identification of the business cycle outlined for the domain controller processing previously, thresholds during the peak period need to be identified. Because the underlying principals are the same for a host machine scheduling guest threads on the CPU as for getting AD DS threads on the CPU on a physical machine, the same goal of 40% to 60% on the underlying host are recommended. At the next layer, the guest layer, since the principals of thread scheduling have not changed, the goal within the guest remains in the 40% to 60% range.

In a direct mapped scenario, one guest per host, all the capacity planning done to this point needs to be added to the requirements (RAM, disk, network) of the underlying host operating system. In a shared host scenario, testing indicates that there is 10% impact on the efficiency of the underlying processors. That means if a site needs 10 CPUs at a target of 40%, the recommended amount of virtual CPUs to allocate across all the “*N*” guests would be 11. In a site with a mixed distribution of physical servers and virtual servers, the modifier only applies to the VMs. For example, if a site has an “*N* + 1” scenario, one physical or direct-mapped server with 10 CPUs would be about equivalent to one guest with 11 CPUs on a host, with 11 CPUs reserved for the domain controller.

Throughout the analysis and calculation of the CPU quantities necessary to support AD DS load, the numbers of CPUs that map to what can be purchased in terms physical hardware do not necessarily map cleanly. Virtualization eliminates the need to round up. Virtualization decreases the effort necessary to add compute capacity to a site, given the ease with which a CPU can be added to a VM. It does not eliminate the need to accurately evaluate the compute power needed so that the underlying hardware is available when additional CPUs need to be added to the guests.  As always, remember to plan and monitor for growth in demand.

### Calculation summary example

|System|Peak CPU|
|-|-|-|
|DC 1|120%|
|DC 2|147%|
|Dc 3|218%|
|Total CPU being used|485%|  
  
|Target system(s) count|Total bandwidth (from above)|
|-|-|
|CPUs needed at 40% target|4.85 &divide; .4 = 12.25|

Repeating due to the importance of this point, *remember to plan for growth*. Assuming 50% growth over the next three years, this environment will need 18.375 CPUs (12.25 &times; 1.5) at the three-year mark. An alternate plan would be to review after the first year and add in additional capacity as needed.

### Cross-trust client authentication load for NTLM

#### Evaluating cross-trust client authentication load

Many environments may have one or more domains connected by a trust. An authentication request for an identity in another domain that does not use Kerberos authentication needs to traverse a trust using the domain controller’s secure channel to another domain controller either in the destination domain or the next domain in the path to the destination domain. The number of concurrent calls using the secure channel that a domain controller can make to a domain controller in a trusted domain is controlled by a setting known as **MaxConcurrentAPI**. For domain controllers, ensuring that the secure channel can handle the amount of load is accomplished by one of two approaches: tuning **MaxConcurrentAPI** or, within a forest, creating shortcut trusts. To gauge the volume of traffic across an individual trust, refer to [How to do performance tuning for NTLM authentication by using the MaxConcurrentApi setting](https://support.microsoft.com/kb/2688798).

During data collection, this, as with all the other scenarios, must be collected during the peak busy periods of the day for the data to be useful.

> [!NOTE]
> Intraforest and interforest scenarios may cause the authentication to traverse multiple trusts and each stage would need to be tuned.

#### Planning

There are a number of applications that use NTLM authentication by default, or use it in a certain configuration scenario. Application servers grow in capacity and service an increasing number of active clients. There is also a trend that clients keep sessions open for a limited time and rather reconnect on a regular basis (such as email pull sync). Another common example for high NTLM load is web proxy servers that require authentication for Internet access.

These applications can cause a significant load for NTLM authentication, which can put significant stress on the DCs, especially when users and resources are in different domains.

There are multiple approaches to managing cross-trust load, which in practice are used in conjunction rather than in an exclusive either/or scenario. The possible options are:

- Reduce cross-trust client authentication by locating the services that a user consumes in the same domain that the user is resident in.
- Increase the number of secure-channels available. This is relevant to intraforest and cross-forest traffic and are known as shortcut trusts.
- Tune the default settings for **MaxConcurrentAPI**.

For tuning **MaxConcurrentAPI** on an existing server, the equation is:

> *New_MaxConcurrentApi_setting* &ge; (*semaphore_acquires* + *semaphore_time-outs*) &times; *average_semaphore_hold_time* &divide; *time_collection_length*

For more information, see [KB article 2688798: How to do performance tuning for NTLM authentication by using the MaxConcurrentApi setting](http://support.microsoft.com/kb/2688798).

## Virtualization considerations

None, this is an operating system tuning setting.

### Calculation summary example

|Data type|Value|
|-|-|
|Semaphore Acquires (Minimum)|6,161|
|Semaphore Acquires (Maximum)|6,762|
|Semaphore Timeouts|0|
|Average Semaphore Hold Time|0.012|
|Collection Duration (seconds)|1:11 minutes (71 seconds)|
|Formula (from KB 2688798)|((6762 &ndash; 6161) + 0) &times; 0.012 /|
|Minimum value for **MaxConcurrentAPI**|((6762 &ndash; 6161) + 0) &times; 0.012 &divide; 71 = .101|

For this system for this time period, the default values are acceptable.

## Monitoring for compliance with capacity planning goals

Throughout this article, it has been discussed that planning and scaling go towards utilization targets. Here is a summary chart of the recommended thresholds that must be monitored to ensure the systems are operating within adequate capacity thresholds. Keep in mind that these are not performance thresholds, but capacity planning thresholds. A server operating in excess of these thresholds will work, but is time to start validating that all the applications are well behaved. If said applications are well behaved, it is time to start evaluating hardware upgrades or other configuration changes.

|Category|Performance counter|Interval/Sampling|Target|Warning|
|-|-|-|-|-|
|Processor|Processor Information(_Total)\\% Processor Utility|60 min|40%|60%|
|ОЗУ (Windows Server 2008 R2 или более ранней версии)|Память\доступно МБ|< 100 МБ.|Н/Д|< 100 МБ.|
|ОЗУ (Windows Server 2012)|Термин Memory\Long среднее Lifetime(s) резервного кэша|30 мин.|Необходимо протестировать|Необходимо протестировать|
|Network|Сетевой интерфейс (\*) \Bytes, отправленных за секунду<br /><br />Сетевой интерфейс (\*) \Bytes, полученных за секунду|30 мин.|40 %|60 %|
|Хранилище|Логический диск ( *\<диск для базы данных NTDS\>* ) \Avg чтения с диска<br /><br />Логический диск ( *\<диск для базы данных NTDS\>* ) \Avg сек время записи на диск|за 60 минут|10 мс|15 мс|
|Службы AD|Netlogon (\*) \Average семафора времени удержания|за 60 минут|0|1 секунда|

## <a name="appendix-a-cpu-sizing-criteria"></a>Приложение A. Условия изменения размера ЦП

### <a name="definitions"></a>Определения

**Процессор (микропроцессор) –** компонент, который считывает и выполняет инструкции программы  

**ЦП —** центральный процессор  

**Многоядерных процессоров —** нескольких процессоров на том же интегральной  

**С несколькими ЦП —** несколько процессоров, а не на том же интегральной  

**Логический процессор —** отдельная логическая вычислительная система с точки зрения операционной системы  

Это включает в себя технологии hyper threading, одно ядро на многоядерных процессоров или одноядерный процессор.  

У современных серверных систем несколько процессоров, несколько многоядерных процессоров и hyper-threading, эти сведения можно обобщить как рассматриваются оба сценария. Таким образом логический процессор термин будет использоваться, так как он представляет операционной системы и точки зрения приложения из доступных вычислительных ядер.

### <a name="thread-level-parallelism"></a>Параллелизм уровня потока

Каждый поток имеет независимые задачи, как каждый поток имеет свой собственный стек и инструкции. Так как AD DS используется несколько потоков и количество доступных потоков может настраиваться с помощью [способы просмотра и задать политики LDAP в Active Directory с помощью Ntdsutil.exe](http://support.microsoft.com/kb/315071), он обеспечивает масштабирование также несколько логических процессоров.

### <a name="data-level-parallelism"></a>Параллелизм на уровне данных

Это включает в себя обмена данными между несколькими потоками в рамках одного процесса (в случае только процесс AD DS) и через несколько потоков в нескольких процессах (в целом). С проблемой чрезмерно упрощению так, это означает, что любые изменения данных отражаются на все запущенные потоки в различных уровней кэша (L1 и L2, L3) во всех ядрах выполнение указанного потоков, а также для обновления общей памяти. Производительность может снизиться при выполнении операций записи, пока все различные области памяти вводятся согласованный, перед продолжением обработки инструкции.

### <a name="cpu-speed-vs-multiple-core-considerations"></a>Скорость ЦП и многоядерными вопросы

Правило работает быстрее логических процессоров сократите длительность, затрачиваемое на обработку серии инструкций, при более логических процессоров означает, что дополнительные задачи, которые могут выполняться одновременно. Эти правила разбить от того, как усложнения сценариев по своей природе следует учитывать выборки данных из общей памяти, ожидающих на параллелизм на уровне данных, а также затраты на управление несколькими потоками. Это также почему масштабируемость в многоядерных системах, не является линейной.

Рассмотрим следующие аналогий в эти вопросы: шоссе, при этом каждый поток выполняется отдельных автомобиля, каждая дорожка, core и выполняется тактовая частота предела скорости обработки.

1. Если имеется только один автомобиль на шоссе, не имеет значения, если имеются два полос или 12 полос. Автомобиля только будут передаваться как можно быстрее в тех предела скорости.
1. Предположим, что данные, позволяющие потоку не сразу становятся доступными. Аналогию бы, что сегмент пути выключена. Если имеется только один автомобиль на шоссе, не важно, какова предела скорости до повторном открытии этой полосы (данные извлекаются из памяти).
1. Как увеличить количество машин, увеличивает расходы на управление количество машин. Сравните возможности разработки решений и объем необходимых внимания при пути является практически пуст (такие как поздно вечером) и когда трафик слишком велик (например, среднего вечера, но не в часы пик). Кроме того, следует учитывать объем внимания необходимые при в двух lane шоссе, где имеется только один lane беспокоиться о действиях драйверы, и шести lane шоссе, где есть беспокоиться о какие массу других драйверов делают.
   > [!NOTE]
   > Аналогию о сценарии в часы пик расширяется в следующем разделе: Время ответа и влияние на производительность системы расписание.

Таким образом подробные сведения о дополнительных или более быстрых процессоров становятся высокой Субъективная на поведение приложения, которое в случае AD DS относится очень осознанности охраны окружающей среды и даже меняется с одного сервера в этой среде. Вот почему ссылки из статьи не инвестировать в, слишком точную и границей безопасности включается в вычислениях. При принятии решения о приобретении на основе бюджета, рекомендуется, что оптимизация использования процессоров на 40% (или количество пропущенных периодических сигналов для среды) происходит во-первых, прежде чем приобретение более быстрые процессоры. Повышенная синхронизации между процессорами дополнительные уменьшает преимуществом дополнительные процессоры линейно возрастает (2&times; число процессоров, содержит меньше 2&times; доступны дополнительные вычислительной мощности).

> [!NOTE]
> Закон Амдала и законе являются важных концепций здесь.

### <a name="response-timehow-the-system-busyness-impacts-performance"></a>Время ответа и влияние на производительность системы расписание

Очереди Теория заключается в математических исследование ожидающих строк (очереди). В теории на очереди закона об использовании представляется с помощью формулы:

*U* k = *B* &divide; *T*

Где *U* k-это процент использования, *B* занят количество времени, и *T* — общее время, система была обнаружена. Преобразуется в контексте Windows, это означает количество 100-наносекундных (ns) интервал потоков, которые находятся в состоянии выполнения, деленное на количество интервалов по 100 нс, были доступны в указанный интервал времени. Это точно формула для вычисления % процессоров (Справочник по [объект процессора](https://docs.microsoft.com/previous-versions/ms804036(v=msdn.10)) и [PERF_100NSEC_TIMER_INV](https://docs.microsoft.com/previous-versions/windows/embedded/ms901169(v=msdn.10))).

Очереди теории также формулы: *N* = *U* k &divide; (1 &ndash; *U* k) для оценки количества элементов ожидания на основе использования ( *N* — Длина очереди). Создание диаграмм, это по всем интервалам использования предоставляет следующие оценки для очереди, чтобы получить на процессоре Каков в любой заданной нагрузки ЦП.

![Длина очереди](media/capacity-planning-considerations-queue-length.png)

Отмечается, что после загрузки ЦП на 50%, в среднем всегда есть ожидания в очереди на один элемент, с заметно быстрого повышения после около 70% загрузки ЦП.

Возвращаясь к вождения аналогию, который использовался ранее в этом разделе:

- Периоды пиковой нагрузки «среднего вечера» гипотетически, находятся где-то в диапазоне 40% до 70%. Таким образом, единицы возможность выбрать любой lane предоставляется не majorly имеется достаточный объем трафика и вероятность другой драйвер, образом, при высокой, не требует усилий в безопасном разрыв между другими автомобили в дороге «найти».
- Один Обратите внимание, что по мере приближения в часы пик трафика road система приближается к 100% емкости. Изменение полос может оказаться очень сложной задачей, так как автомобили близки поэтому друг с другом, повышенная нужно соблюдать осторожность, чтобы сделать это.

Именно по этой причине в долгосрочной перспективе вычисляет среднее значение для емкости консервативно примерно 40% способен головной место для необычные всплески активности в загрузки, ли говорят, что пики исчезающие (например, плохо закодированных запросов, которые выполняются в течение нескольких минут) или Аномальное активности (утром из нагрузки в целом Первый день после длинные выходные дни).

Приведенная выше инструкция относится к % загруженности процессора вычисления одинаков как закон об использовании — часть для простоты упрощения Общие средства чтения. Для этих математически более строгие:  
- Перевод [PERF_100NSEC_TIMER_INV](https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms901169(v=msdn.10))
  - *B* = количество интервалов 100 нс, «Idle» поток тратит на логический процессор. Изменение "*X*" переменной в [PERF_100NSEC_TIMER_INV](https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms901169(v=msdn.10)) вычисления
  - *T* = общее количество интервалов по 100 нс в заданном диапазоне времени. Изменение "*Y*" переменной в [PERF_100NSEC_TIMER_INV](https://docs.microsoft.com/en-us/previous-versions/windows/embedded/ms901169(v=msdn.10)) вычисления.
  - *U* k = процент использования логического процессора «Простоя потока» или % времени простоя.  
- Выработке вычислений:
  - *U* k = 1 — % загруженности процессора
  - % Загруженности процессора = 1 – *U* k
  - % Загруженности процессора = 1 – *B* / *T*
  - % Загруженности процессора = 1 – *X1* — *X0* / *Y1* — *Y0*

### <a name="applying-the-concepts-to-capacity-planning"></a>Применение концепции с планированием загрузки

Может быть выше math показаться чрезвычайно сложными решения о количестве логических процессоров в системе. Именно поэтому способ изменения размеров в системах ориентирован на определение максимальное целевое использование зависимости от текущей нагрузки и подсчета количества логических процессоров, нужно пройти существует. Кроме того логических процессоров с тактовой частотой будет иметь значительное влияние на производительность, эффективность кэша, требования к согласованности памяти, планирование потоков и синхронизации, а клиент несовершенно с балансировкой нагрузки все окажет значительное влияние на производительность, влияющий на уровне сервера с сервера. Относительно недорогим стоимости вычислительной мощности попытка проанализировать и определить идеальное число процессоров требуется становится более академического упражнения превышающие его ценность для бизнеса.

Сорок процентов не обязательно строгими, это разумный start. Различные пользователи Active Directory требуются различные уровни реагирования на запросы. Может возникнуть случаях средах можно работать с загрузкой 80 или 90 процентов как устойчивый среднее, увеличению времени ожидания для доступа к обработчику не повлияет на заметно производительности клиента. Очень важно для повторной итерации, что в системе, в которой выполняются гораздо медленнее, чем логических процессоров в системе, включая доступ к оперативной памяти существует большое количество областей, доступ к диска и передачи ответа по сети. Все эти элементы должны настраиваться в сочетании. Примеры

- Добавление процессоров в системе 90%, который связан с диска, скорее всего, не будет значительно повысить производительность. Более глубокого анализа системы будут, вероятно, определили, что существует множество потоков, которые не даже получаете на процессоре, так как они ожидают завершения ввода-вывода.
- Устранение проблем с дисками потенциально означает, что потоки, которые ранее тратит слишком много времени в состоянии ожидания, больше не будут находиться в состоянии ожидания для операций ввода-вывода и будет существовать дополнительные конкуренция за время ЦП, что означает, что загрузкой 90% в предыдущем Пример изменится на 100% (так как он не может быть больше). Оба компонента должны настраиваться в сочетании.
  > [!NOTE]
  > Процессор Information(*)\\% процессоров может превышать 100% с системами, режим «Turbo».  Это происходит, когда ЦП превышает скорость процессора, оцененных в течение коротких периодов.  Справочник по ЦП производителей документация и описание счетчика для более глубокого анализа.  

Обсуждать вопросы использования всей системы накладывает на контроллеры домена диалога как виртуальным гостям. [Время ответа и влияние на производительность системы расписание](#response-timehow-the-system-busyness-impacts-performance) применяется к узле и гостевой в виртуализированной сценарии. Вот почему в основном приложении с помощью только один гостевой, контроллер домена (и обычно в любой системе) имеет почти такую же производительность, как на физическом оборудовании. Дополнительные администраторы могут добавить узлы повышает степень использования базового узла, тем самым увеличивая время ожидания для получения доступа к процессорам, как описано выше. Короче говоря логических процессора должна управляться на оба узла и гостевой уровнями.

Расширение предыдущего аналогий, оставляя шоссе как физическое оборудование, гостевой виртуальной Машины будет analogized с шиной (хочет express шины, который будет перемещен в месте назначения rider). Представьте следующие четыре сценария:

- Это нерабочие часы, rider возвращает на шине, почти пуст и шиной пути, который также является почти пустой. Отсутствует трафик тем с большими трудностями, rider есть удобная легко поездки и получает существует только как fast так, как если бы на основе rider вместо этого. Rider временем поездки, по-прежнему ограничены предела скорости.
- Это нерабочие часы, шине практически пуст, но большая часть полосы в дороге будут закрыты, так что шоссе по-прежнему перегружена. Rider — по шине почти пустым перегружена пути. Хотя rider имеет массу конкуренции в шине, на который будет находиться, общее время по-прежнему зависит от остальной части трафика за пределами.
- Это в часы пик, благодаря чему шоссе и bus будут перегружены. Не только поездку занять больше времени, но получение включения и отключения шины является настоящим кошмаром, так как люди плечо, сможет узнать для плечо, сможет узнать и шоссе не гораздо лучше. Добавление дополнительных шины (логических процессоров, Гость) не означает, их можно использовать в пути любой более легко или поездку уменьшается.
- Последний сценарий — на то, что он может растягивания аналогию немного, где шины заполнена, но пути не перегружена. Хотя rider по-прежнему будет иметь получении включения и отключения шины, поездку будет эффективным после шине в дороге. Это единственный случай, где Добавление дополнительные шины (логических процессоров, Гость) улучшит производительность гостевых виртуальных машин.

Оттуда относительно несложно экстраполировать, что существует ряд сценариев между используется 0% и 100% загруженные состояния пути и состоянии 0% и 100%-используется шины, которую различной степени влияния.

Применение участников выше 40% ресурсов ЦП, чем разумным целевой узел, а также гостевой является разумным start для тем же причинам, как и выше, объем очереди.

## <a name="appendix-b-considerations-regarding-different-processor-speeds-and-the-effect-of-processor-power-management-on-processor-speeds"></a>Приложение B. Вопросы, касающиеся частоты процессора, отличной от и последствия управление питанием процессора на частот процессоров

Во всех подразделах на выбор процессора делается предположение, что процессор 100% от тактовая частота на весь период сбора данных и у систем замены же скорости процессоров. Несмотря на обоих предположения, на практике, false, особенно при работе с Windows Server 2008 R2 и более поздних версий, где схему управления питанием по умолчанию — **Сбалансированный**, методологии по-прежнему означает, так как это консервативный подход. Частота потенциальных ошибок может увеличиться, оно только увеличивается размер отступа от безопасности по мере увеличения скорости процессора.

- Например, в сценарии, где 11.25 ЦП, которые требуются, если процессоры были запущены на половину скорости сбора данных, более точного подсчета может быть 5.125 &divide; 2.
- Вы не сможете гарантировать, что удвоения частоты одноядерных систем будет вдвое больше объема обработки, что происходит в течение заданного периода времени. Это потому, что количество времени, которое процессор тратит на ожидание оперативной памяти или других компонентов системы может оставаться изменений. В итоге получается, что более быстрыми процессорами может потратить больше процент времени, простаивая в ожидании данных для выборки. Опять же рекомендуется придерживаться наименьшему общему знаменателю, умеренное и не следует вычислить потенциально false уровень точности, при условии, что линейное сравнение между частот процессоров.

Кроме того Если скорость процессора в замене оборудования меньше текущего оборудования, можно с уверенностью для оценки процессоры пропорционально величину увеличения. Например эта величина 10 процессоров необходимы для обработки нагрузки на узле и текущей процессоров в системе 3.3 ГГц и замены процессоров будет частотой 2,6 ГГц, что это 21% снижение скорости. В этом случае 12 процессоров будет рекомендуемого.

С другой стороны, эти изменения не будут изменяться в целевые показатели использования процессора управления емкостью. Так как тактовая частота процессора будет впоследствии скорректирована динамически на основе нагрузки затребованное, запуск системы более высоких нагрузок создаст сценарий, где ЦП тратит больше времени в более высокого состояния скорости часов, что основной задачей в данных об использовании 40% на 100% состояние скорости часов в часы пик. Все, что меньше, чем создаст экономии энергии, как скорость ЦП будет возвращена назад во время off сценариев пиковой.

> [!NOTE]
> Параметр можно отключить управление электропитанием в процессорах (Установка схемы управления питанием **высокопроизводительных**) при сборе данных. Даст более точное представление потребление ресурсов ЦП на целевом сервере.

Чтобы настроить оценку для разных процессоров, раньше приходилось принимать safe, за исключением других узких мест системы, описанные выше, предполагается, что удвоение частот процессоров удвоить объем обработки, которое может быть выполнено.  В настоящее время внутренняя архитектура процессоров отличается достаточно между процессорами, которые является более безопасным способом, чтобы оценить влияние использования разных процессоров, чем данных был взят из использовать SPECint_rate2006 тест производительности на основе стандартных оценки производительности Corporation.

1. Найти SPECint_rate2006 оценок для процессора, используются и который планируется использовать.
    1. На веб-сайте корпорации стандартный оценки производительности, выберите **результатов**, выделите **CPU2006**и выберите **все SPECint_rate2006 результаты поиска**.
    1. В разделе **простой запрос**, введите условия поиска для целевого процессора, например **процессора совпадения E5-2630 (baselinetarget)** и **процессора совпадения E5-2650 (базовый)** .
    1. Найти конфигурацию сервера и процессора для использования (или что-то закрыть, если точное соответствие недоступен) и обратите внимание на значение в **результат** и **# ядер** столбцов.
1. Чтобы определить модификатор применить следующую формулу:
   >((*Целевое значение оценки каждое ядро платформы*) &times; (*МГц каждое ядро базовой платформы*)) &divide; ((*базовых показателей на процессор значение оценки*) &times; (*МГц каждое ядро целевой платформы*))  

    В примере выше:
   >(35.83 &times; 2000) &divide; (33.75 &times; 2300) = 0.92
1. Умножьте предполагаемое количество процессоров с помощью модификатора.  В приведенном выше примере, чтобы перейти из E5-2650 процессора для процессоров E5-2630 умножение вычисляемые 11.25 ЦП &times; 0.92 = 10,35 процессоры.

## <a name="appendix-c-fundamentals-regarding-the-operating-system-interacting-with-storage"></a>Приложение В. Основы работы с наборами операционной системы, взаимодействии с хранилищем

Описанные принципы очередей теории в [время отклика и влияние на производительность системы расписание](#response-timehow-the-system-busyness-impacts-performance) применимы также в хранилище. Наличие хорошо знакомые возможности как дескрипторы операционной системы ввода-вывода необходимо применение этих понятий. В операционной системе Microsoft Windows очередь для хранения запросов ввода-вывода создается для каждого физического диска. Тем не менее также разъяснение на физическом диске должен выполняться. Представления текущих агрегатов шпинделей в операционную систему как один из физических дисков, массива контроллеров устройств и сетей SAN. Кроме того массива контроллеров устройств и сетей SAN можно объединять несколько дисков в один массив набор и затем разделить этот массив набор на несколько «секции», в свою очередь представленное в операционную систему как несколько физических дисков (рис. ссылка).

![Блокирование шпинделей](media/capacity-planning-considerations-block-spindles.png)  

На этом рисунке показано два шпинделей зеркальное отображение и разделить на логические области для хранения данных (Data 1 и 2 данных). Эти логические области просмотра операционной системой как отдельных физических дисках.

Несмотря на то, что это может быть очень запутанным, на протяжении всего в этом приложении для идентификации различных сущностей используется следующая терминология:

- **Жестким диском –** устройство, которое физически устанавливается на сервере.
- **Массив —** коллекцию шпинделей, упорядоченные по контроллера.
- **Массив секции —** секционирование агрегированные массива
- **LUN —** массив, используемый при обращении к сети SAN
- **Диск —** обнаруживает быть одного физического диска операционной системы.
- **Секции —** логическим разбиением пространства операционная система распознает как физический диск.

### <a name="operating-system-architecture-considerations"></a>Рекомендации по архитектуре операционной системы

Операционная система создает очередь первый In/First Out (FIFO) операций ввода-вывода для каждого диска, который является значением, зафиксированным; Этот диск может представлять жестким диском, массив или массив секции. С точки зрения операционной системы, части обработки ввода-вывода чем более активно ставит в очередь тем лучше. Так как очередь FIFO сериализуется, это означает, что все операции ввода-вывода, выданных для подсистемы хранилища, должны обрабатываться в порядке поступления запроса. Путем сопоставления каждого диска, наблюдаемая в операционной системе с жестким диском или массивом, операционной системе теперь поддерживает в очередь операций ввода-вывода для каждого уникального набора дисков, тем самым устраняя состязание за дефицитные ресурсы ввода-вывода на дисках и изоляция запросу ввода-вывода к одному диск. Как исключение Windows Server 2008 введено понятие приоритетов операций ввода-вывода, а приложения, предназначенные для использования с приоритетом «Низкий» само выходит из этого обычном порядке и Сядьте назад. Приложения в коде не только использовать значение по умолчанию приоритетом «Низкий» на «Normal».

### <a name="introducing-simple-storage-subsystems"></a>Знакомство с подсистемами хранения простой

Начиная с простого примера (один жесткий диск внутри компьютера) будет предоставлена анализа компонент. Разбить это на компонентов подсистемы основные хранилища, система состоит из:

- **1 –** 10 000 об/мин Ultra Fast SCSI HD (Ultra SCSI быстрый имеет скорость передачи данных 20 МБ в секунду)
- **1 –** шины SCSI (кабель)
- **1 –** ultra быстрый SCSI-адаптер
- **1 –** шины PCI 32-разрядных 33 МГц

После определения компонентов о том, какой объем данных может проходить системы или объем операций ввода-вывода могут обрабатываться, можно вычислить. Обратите внимание на то, что объем операций ввода-вывода и количества данных, который может проходить система сопоставляется, но не совпадают. Эта связь зависит от ввода-вывода является случайный или последовательный и размер блока. (Все данные записываются на диск в виде блока, но разных приложений, использующих разных блоков). На основе компонента, компонент:

- **Жесткий диск** среднее жесткий диск 10 000 об/мин имеет 7-миллисекунд (мс) поиск времени и времени доступа 3 мс. Поиск время — это среднее время чтения и записи заголовок, чтобы перейти в расположение на жесткий диск. Время доступа — это среднее количество времени, необходимое для чтения или записи данных на диск, после head в нужное место. Таким образом среднее время чтения уникальный блок данных в формате HD 10 000 об/мин составляет предикат seek и доступа, в сумме приблизительно 10 мс (или.010 секунд) каждого блока данных.

  Каждый доступ к диску, требующей перемещения головы в новое расположение на диске, чтение и запись поведение называется «случайные». Таким образом, когда весь ввод/вывод происходит случайным образом, HD 10 000 об/мин может обслуживать примерно 100 операций ввода-вывода в секунду (IOPS) (формула является 1000 мс в секунду, деленное на 10 мс для операций ввода-вывода или 1000/10 = 100 операций ввода-ВЫВОДА).

  Кроме того когда все операции ввода-вывода выполняется из смежных секторов на HD, это называется последовательных операций ввода-вывода. Последовательные операции нет время поиска, так как после завершения первой операции ввода-вывода головки чтения и записи в начале хранения следующего блока данных на жесткий ДИСК. Таким образом может обрабатывать приблизительно 333 HD 10 000 об/мин ввода-вывода в секунду (1000 мс в секунду, деленное на 3 мс для операций ввода-вывода).

  >[!NOTE]
  >В этом примере не отражает дискового кэша, где данные одного цилиндра, обычно хранятся. В этом случае на первой операции ввода-вывода требуются 10 мс и диск считывает всю цилиндра. Все другие последовательные операции удовлетворяется из кэша. В результате в дисковых кэшей может улучшить производительность последовательного ввода-вывода.
  
  На данный момент скорость передачи жесткого диска был не имеет значения. Ли жесткий диск — 20 МБ в секунду Ultra ширину или Ultra3 160 МБ в секунду, фактический объем операций ввода-ВЫВОДА может обрабатываться HD 10 000 об/мин — около 100 случайных или ~ 300 последовательного ввода-вывода. Как блокировать изменения размеров на основе приложения записи на диск, объем данных, которые помещаются на операции ввода-вывода отличается. Например если размер блока 8 КБ, 100 операций ввода-вывода будет считывать из или записывать на жесткий диск в сумме 800 КБ. Тем не менее если размер блока составляет 32 КБ, 100 операций ввода-вывода будет чтение и запись 3200 КБ (3,2 МБ) на жестком диске. До тех пор, пока скорость передачи SCSI превышает общий объем переданных данных, получение передача «ускоряется» скорость диска получит никаких действий. См. в следующих таблицах, для сравнения.

  | |Доступ к 4ms 7200 об/мин 9ms seek,|Получить доступ к seek 10 000 об/мин: %7 мс, мс|15 000 об/мин 4ms seek, доступ к 2 мс.
  |-|-|-|-|
  |Случайных операций ввода-вывода|80|100|150|
  |Последовательных операций ввода-вывода|250|300|500|  
  
  |Диск 10 000 об/мин|Размер блока 8 КБ (Active Directory Jet)|
  |-|-|
  |Случайных операций ввода-вывода|800 Килобайт в секунду.|
  |Последовательных операций ввода-вывода|2400 КБ/с|

- **Объединительной платы SCSI (шины) —** основные сведения о том, как панели «SCSI (шины)», или в этом случае кабель ленты влияет на пропускной способности подсистемы хранилища зависит от знания размеру блока. По сути вопроса может быть, сколько операций ввода-вывода может дескриптор шины, если ввод-вывод в блоках размером 8 КБ? В этом случае шины SCSI — 20 МБ в секунду или 20480 КБ/с. 20480 деления блоков размером 8 КБ на КБ/с обеспечивает более приблизительно 2 500 операций ввода-вывода поддерживает шины SCSI.

  >[!NOTE]
  >Цифры в следующей таблице представляют пример. Наиболее подключенные устройства хранения в настоящее время использовать PCI Express, который обеспечивает более высокую пропускную способность.  
  
  |Поддерживаемые шины SCSI на размер блока ввода-вывода|Размер блока 2 КБ|Размер блока 8 КБ (AD Jet) (SQL Server 7.0 или SQL Server 2000)
  |-|-|-|
  |20 МБ в секунду.|10,000|2,500|
  |40 МБ в секунду.|20,000|5,000|
  |128 МБ в секунду.|65,536|16,384|
  |320 МБ в секунду.|160,000|40,000|

  Как можно определить из этой диаграммы, в сценарии представлены, независимо от того, какой метод шины никогда не будет узким местом, как скорость вращения максимальное значение — 100 операций ввода-вывода, намного меньшее описанных выше пороговых значений.

  >[!NOTE]
  >При этом предполагается, что шины SCSI является эффективным 100%.
  
- **Адаптер SCSI** для определения количества операций ввода-вывода, поддерживающий работу это, необходимо проверить в спецификациях. Направление запросов ввода-вывода для соответствующего устройства требуется обработка какого-либо рода, таким образом объем операций ввода-вывода, которое может быть обработано зависит от адаптера SCSI (или контроллер массива) процессора.

  В этом примере предполагается который 1000 операций ввода-вывода может обрабатываться будут внесены.

- **Шина PCI-** это компонент, часто не уделяют должного внимания. В этом примере это не будет. ее узкое место; Тем не менее как систем увеличить масштаб, он может стать узким местом. Для справки 32-разрядная версия шины PCI, работающей на 33 МГц можно в теории transfer 133 МБ данных. Ниже приведен уравнение.  
  > 32 бита &divide; 8 битов в байте &times; 33 МГц = 133 МБ/s.  

  Обратите внимание, что теоретического ограничения; на самом деле только около 50% от максимально будет достигнуто, несмотря на то, что в некоторых сценариях пакетов, 75% эффективности можно получить в течение коротких периодов.

  66 МГц 64-разрядных PCI может поддерживать теоретического максимума (64 бита &divide; 8 битов в байте &times; 66 МГц) = 528 МБ/с. Кроме того, любом другом устройстве (например, сетевой адаптер, второй контроллер SCSI и т. д.) позволит снизить пропускную способность как пропускная способность является общим и устройства, будут конкурировать за ограниченные ресурсы.

После анализа компонентов этой подсистемы хранилища ограничивающим фактором объема операций ввода-вывода, который может запрашиваться и, следовательно, объем данных, который может проходить система является жестким диском. В частности, в сценариях с AD DS это 100 случайных операций ввода-вывода в секунду с шагом 8 КБ, в сумме 800 КБ на втором случае, если доступ к базе данных Jet. Кроме того максимальная пропускная способность для жестким диском, который выделяется исключительно для файлов журнала, пострадали бы следующие ограничения: 300 последовательных операций ввода-вывода в секунду с шагом 8 КБ, в сумме 2400 КБ (2,4 МБ) в секунду.

Теперь анализа простую конфигурацию, в следующей таблице показаны которых будет выполняться узким местом, как изменяются или добавить компоненты в подсистеме хранилища.

|Примечания|Анализ узких мест|Disk|Bus|Адаптер|Шина PCI|
|-|-|-|-|-|-|
|Это настройка контроллера домена после добавления второго диска. Конфигурация диска представляет узкое место при 800 КБ/с.|Добавить 1 диск (общее = 2)<br /><br />Случайных операций ввода-вывода<br /><br />Размер блока в 4 КБ<br /><br />HD 10 000 ОБ/МИН|200 общее, операций ввода-вывода<br />Общий объем 800 Килобайт в секунду.| | | |
|После добавления 7 дисков, конфигурация диска по-прежнему представляет узкое место при 3200 КБ/с.|**Добавление дисков по 7 (общее = 8)**  <br /><br />Случайных операций ввода-вывода<br /><br />Размер блока в 4 КБ<br /><br />HD 10 000 ОБ/МИН|800 операций ввода-вывода общее.<br />Общее число Килобайт в секунду 3200| | | |
|После изменения последовательных операций ввода-вывода, сетевой адаптер станет узким местом, так как она ограничена 1000 операций ввода-ВЫВОДА.|Добавление дисков по 7 (общее = 8)<br /><br />**Последовательных операций ввода-вывода**<br /><br />Размер блока в 4 КБ<br /><br />HD 10 000 ОБ/МИН| | |Сек 2400 ввода-вывода может нельзя прочитать или записать на диск, контроллер, ограничен 1000 операций ввода-ВЫВОДА| |
|После замены сетевой адаптер SCSI-адаптер, который поддерживает 10 000 операций ввода-ВЫВОДА, узкое место возвращает конфигурации диска.|Добавление дисков по 7 (общее = 8)<br /><br />Случайных операций ввода-вывода<br /><br />Размер блока в 4 КБ<br /><br />HD 10 000 ОБ/МИН<br /><br />**Обновление адаптера SCSI (теперь поддерживает 10 000 операций ввода-вывода)**|800 операций ввода-вывода общее.<br />3200 общее число Килобайт в секунду| | | |
|После увеличения размера блока до 32 КБ, шине становится узким местом, так как он поддерживает только 20 МБ в секунду.|Добавление дисков по 7 (общее = 8)<br /><br />Случайных операций ввода-вывода<br /><br />**Размер блока 32 КБ**<br /><br />HD 10 000 ОБ/МИН| |800 операций ввода-вывода общее. 25,600 КБ/s (25 МБ/с) может быть, прочитанные или записанные на диск.<br /><br />Шина поддерживает только 20 МБ в секунду.| | |
|После обновления шины и добавление дополнительных дисков, диск останется. ее узкое место.|**Добавление 13 дисков (общее = 14)**<br /><br />Добавьте второй адаптер SCSI с 14 дисками<br /><br />Случайных операций ввода-вывода<br /><br />Размер блока в 4 КБ<br /><br />HD 10 000 ОБ/МИН<br /><br />**Обновление до 320 шины SCSI МБ в секунду**|2800 операций ввода-вывода<br /><br />11,200 КБ/с (10.9 МБ/с)| | | |
|После изменения последовательных операций ввода-вывода, диск останется. ее узкое место.|Добавление 13 дисков (общее = 14)<br /><br />Добавьте второй адаптер SCSI с 14 дисками<br /><br />**Последовательных операций ввода-вывода**<br /><br />Размер блока в 4 КБ<br /><br />HD 10 000 ОБ/МИН<br /><br />Обновление до 320 шины SCSI МБ в секунду|8,400 операций ввода-вывода<br /><br />33 600 KB\s<br /><br />(32.8 MB\s)| | | |
|После добавления быстрее жестких дисков, диск останется. ее узкое место.|Добавление 13 дисков (общее = 14)<br /><br />Добавьте второй адаптер SCSI с 14 дисками<br /><br />Последовательных операций ввода-вывода<br /><br />Размер блока в 4 КБ<br /><br />**HD 15 000 ОБ/МИН**<br /><br />Обновление до 320 шины SCSI МБ в секунду|14 000 операций ввода-вывода<br /><br />56 000 Килобайт в секунду.<br /><br />(54.7 МБ/с)| | | |
|После увеличения размера блока до 32 КБ, шины PCI станет узким местом.|Добавление 13 дисков (общее = 14)<br /><br />Добавьте второй адаптер SCSI с 14 дисками<br /><br />Последовательных операций ввода-вывода<br /><br />**Размер блока 32 КБ**<br /><br />HD 15 000 ОБ/МИН<br /><br />Обновление до 320 шины SCSI МБ в секунду| | | |14 000 операций ввода-вывода<br /><br />448,000 КБ/с<br /><br />(437 МБ/с), ограничено чтение и запись к жестким диском.<br /><br />Шина PCI поддерживает теоретического максимума 133 МБ в секунду (эффективный в лучшем 75%).|

### <a name="introducing-raid"></a>Общие сведения о RAID

Когда вводится контроллера массива; значительно изменяется характер подсистемы хранения он просто заменяет SCSI-адаптер в вычислениях. Что приводит к изменению является стоимость чтения и записи данных на диск при использовании различных уровней массива (RAID 0, RAID 1 или RAID 5).

В режиме RAID 0 данные распределяются по все заданные диски в RAID. Это означает, что во время операции чтения или записи, часть данных, извлеченных из или в каждый диск, увеличение объема данных, который может проходить система же период времени. Таким образом в одну секунду на каждый жестким диском (снова при условии, что диски 10 000 об/мин), 100 операций ввода-вывода может выполняться. Общий объем операций ввода-вывода, которые могут поддерживаться является N шпинделей, умноженное на 100 операций ввода-вывода в секунду на жестким диском (100 * N дает ввода-вывода в секунду).

![D: логического диска](media/capacity-planning-considerations-logical-d-drive.png)

В RAID 1 данных зеркальное отображение (дублируется), в пары шпинделей для обеспечения избыточности. Таким образом при выполнении операции ввода-вывода чтения, данные могут считываться из обеих шпинделей в наборе. Это фактически делает емкость ввода-вывода с обоих дисков доступны во время операции чтения. Следует учитывать, что, писать рост операций не прироста производительности в RAID 1. Это так, как и те же данные должны записываться на обоих дисков для обеспечения избыточности. На то, что он не принимает больше времени, в процессе записи данных одновременно на обоих шпинделей, так как оба шпинделей заняты дублирование данных, операции ввода-вывода записи фактически не позволяет две операции чтения. Таким образом каждый затраты на операции ввода-вывода записи двух операций чтения. Формулы можно создавать на основе этих сведений, чтобы определить общее число операций ввода-вывода, которые:  

> *Чтение операций ввода-вывода* + 2 &times; *записи ввода-вывода* = *общее число доступных дискового ввода-вывода потребления*  

При отношение количества операций чтения и записи, количество шпинделей известны, уравнением могут быть производными от выше уравнение для определения максимального операций ввода-вывода, которые могут поддерживаться в массиве:  

> *Максимальное количество IOPS на жестким диском* &times; 2 шпинделей &times; [( *% операций чтения* +  *% операций записи*) &divide; ( *% операций чтения* + 2 &times; *% операций записи*)] = *общее число операций ввода-ВЫВОДА*

RAID 1 + 0, ведет себя так же, как RAID 1 в отношении расходов, чтения и записи. Тем не менее теперь чередуются ввода-вывода на каждый зеркальный набор. Если командлет  

> *Максимальное количество IOPS на жестким диском* &times; 2 шпинделей &times; [( *% операций чтения* +  *% операций записи*) &divide; ( *% операций чтения* + 2 &times; *% операций записи*)] = *общее число операций ввода-вывода*  

в наборе RAID 1, если кратность (*N*) RAID 1, чередующихся наборов, становится общий ввод-вывод, который может быть обработан N &times; ввода-вывода в наборе RAID 1:  

> *N* &times; {*максимальное количество IOPS на жестким диском* &times; 2 шпинделей &times; [( *% операций чтения* +  *% операций записи*) &divide; ( *% Операций чтения* + 2 &times; *% операций записи*)]} = *общее число операций ввода-ВЫВОДА*

В RAID 5, иногда называют *N* + 1 RAID, данные распределяются по *N* шпинделей и четность сведений, записываемых жестким диском «+ 1». Тем не менее RAID 5 гораздо дороже, при выполнении операций ввода-вывода записи чем RAID 1 или 1 + 0. RAID 5 выполняет процесс, каждый раз при отправке операциями записи в массив.

1. Чтение старых данных
1. Чтение старого четность
1. Запись новых данных
1. Запись новых четность

Так как каждый запрос ввода-вывода записи, переданных в контроллер массива операционной системой требуется четыре завершения операций ввода-вывода, отправленных запросов записи занять четыре раза больше времени, чтобы завершить как одного чтения ввода-вывода. Для получения формулы для преобразования запросов ввода-вывода с точки зрения операционной системы, из-за шпинделей:  

> *Чтение операций ввода-вывода* + 4 &times; *записи ввода-вывода* = *общее число операций ввода-вывода*  

Аналогичным образом в наборе RAID 1, когда известны отношение количества операций чтения и записи и количество шпинделей, уравнением могут быть производными от выше уравнение для определения максимального операций ввода-вывода, которые могут поддерживаться в массиве (Обратите внимание, что общее количество шпинделей не включает e «водить» была потеряна четности):  

> *Количество IOPS на жестким диском* &times; (*шпинделей* – 1) &times; [( *% операций чтения* +  *% операций записи*) &divide; ( *% Операций чтения* + 4 &times; *% операций записи*)] = *общее число операций ввода-ВЫВОДА*

### <a name="introducing-sans"></a>Введение в сети SAN

Развернув сложности подсистемы хранения, когда по сети SAN вводится в среду, не изменяйте базовый принципам, описанным, тем не менее поведение ввода-вывода для всех систем, подключенных к сети SAN должны приниматься во внимание. Как один из главных преимуществ в сети хранения данных дополнительного избыточность на внутреннем или внешнем доступе подключенное хранилище, планирования ресурсов теперь должен учитывать потребности допуска сбоя учетной записи. Кроме того, представлены дополнительные компоненты, которые необходимо вычислить. Разбить по сети SAN на составные части:

- Жесткого диска SCSI или Fibre Channel
- Задняя панель канала единицы хранения
- Единицы хранения
- Модуль контроллера хранилища
- Выключатели SAN
- HBA(s)
- Шина PCI

При разработке любой системе для обеспечения избыточности, дополнительные компоненты не включенные в соответствии с вероятность сбоя. Очень важно, когда Планирование емкости, чтобы исключить избыточных компонентов из доступных ресурсов. Например если SAN имеется два модуля контроллера, пропускную способность модуля один контроллер — все, что следует использовать для общей пропускной способности ввода-вывода, доступных в системе. Это связано с тем, что в случае сбоя одного контроллера вся нагрузка операций ввода-вывода затребованы всех подключенных систем нужно будет обрабатываться оставшийся контроллер. Как и все планирование загрузки для периодов пикового использования, избыточных компонентов, не должна быть учтена в доступных ресурсов и планового максимальное значение не должно превышать 80% насыщенность системы (с целью размещения пики или аномальных системы поведение). Аналогичным образом избыточные коммутатора SAN, единицы хранения и шпинделей не учитываться в вычисления ввода-вывода.

При анализе поведения жесткого диска SCSI или Fibre Channel, метод анализа поведения, как описано ранее остается неизменным. Несмотря на то, что есть определенные преимущества и недостатки каждого из протоколов, ограничивающим фактором для каждого диска — это механические ограничение жесткого диска.

Анализ канала на единицу хранения — точно так же, как вычисление ресурсы, доступные на шине SCSI или пропускной способности (например, 20 МБ в секунду), деленное на размер блока (например, 8 КБ). Где это отличается от предыдущего примера находится в агрегирование по нескольким каналам. Например если 6 каналов, каждый из которых поддерживает 20 МБ в секунду максимальную скорость передачи, общий объем операций ввода-вывода и для передачи данных, доступный — 100 МБИТ/с (это верно, это не 120 МБ в секунду). Опять же устойчивость к сбоям является основной проигрывателем рассчитывая это, в случае потери всего канала, системе не только левого входа с 5 работает каналов. Таким образом чтобы обеспечить продолжение в соответствии с ожидаемой производительностью в случае сбоя, общая пропускная способность для всех каналов хранилища не должна превышать 100 МБ в секунду (предполагается, что нагрузки и отказоустойчивость равномерно распределяется по всем каналам). Включение этого в профиль ввода-вывода в зависит от поведения приложения. В случае с Active Directory Jet ввода-вывода, это будет сопоставлять приблизительно 12 500 операций ввода-вывода в секунду (100 МБИТ/с &divide; 8 КБ на операции ввода-вывода).

Затем получение производителя для модулей контроллера необходим для можно получить информацию о пропускной способности, которое может поддерживать каждого модуля. В этом примере SAN имеется два модуля контроллера, поддержка 7500 операций ввода-вывода каждого. Общая пропускная способность системы может быть 15 000 операций ввода-ВЫВОДА, если не требуется избыточность. При вычислении максимальная пропускная способность в случае сбоя, ограничением является пропускная способность одного контроллера или 7500 операций ввода-ВЫВОДА. Это пороговое значение значительно меньше 12 500 максимальное количество операций ввода-ВЫВОДА (при условии, что размер блока в 4 КБ), которое может поддерживаться все каналы, хранения и таким образом, в настоящее время является узким местом в анализе. По-прежнему для целей планирования, нужный максимальное ввода-вывода, чтобы учитывать в планах бы 10,400 ввода-вывода.

После выхода из данных модуль контроллера тому же подключения Fibre Channel, со скоростью 1 ГБИТ/с (или 1 гигабит в секунду). Чтобы сопоставить это с другими метриками, 1 ГБИТ/с превращается в 128 МБ/с (1 ГБИТ/с &divide; 8 битов/байт). Так как это сверх общей пропускной способности по всем каналам в единице хранения (100 МБИТ/с), это будет не образовать узкое место системы. Кроме того, как это только один из двух каналов (дополнительных 1 ГБИТ/с, Fibre Channel соединение, для обеспечения избыточности) в случае сбоя одного подключения оставшиеся подключение по-прежнему имеет достаточную емкость для обработки всех затребованное переноса данных.

Нахождения на маршруте к серверу, данные скорее будет проходить коммутатора SAN. Коммутатор сети хранения данных должен обрабатывать входящий запрос ввода-вывода и пересылать его соответствующий порт, коммутатор будет иметь ограничение на объем операций ввода-вывода, которое может быть обработано, тем не менее, производители спецификации потребуется для определения того, что он составляет. Например если существуют два параметра, и каждый параметр может обрабатывать 10 000 операций ввода-ВЫВОДА, общая пропускная способность будет 20 000 операций ввода-ВЫВОДА. Опять же отказоустойчивость, что неважно, если происходит сбой одного коммутатора, общая пропускная способность системы будет 10 000 операций ввода-ВЫВОДА. Что он не должен превышать 80% использования во время работы, используя не более чем 8000 операций ввода-вывода должен быть целью.

И, наконец HBA, установленного на сервере также будет иметь ограничение на объем операций ввода-вывода, который он может обрабатывать. Как правило, второй HBA устанавливается для обеспечения избыточности, но так же, как с параметром SAN при вычислении максимального ввода-вывода, которое может быть обработано, общую пропускную способность *N* &ndash; 1 HBA новые возможности максимальной масштабируемости системы.

### <a name="caching-considerations"></a>Кэширование вопросы

Кэши являются одним из компонентов, которые могут негативно повлиять на общую производительность в любой момент в системе хранения. Подробный анализ об алгоритмах кэширования выходит за рамки этой статьи. Тем не менее некоторые основные инструкции о кэшировании на дисковые подсистемы стоят освещение:

- Кэширование ввода-вывода улучшенные устойчивый последовательной записи делает, буфера множество небольших операций записи в более крупные блоки ввода-вывода и отмену этапа в хранилище в размеры меньшее число более крупных блоков. Это позволит снизить общее случайных операций ввода-вывода и общее последовательных операций ввода-вывода, обеспечивая доступность дополнительных ресурсов для других операций ввода-вывода.
- Кэширование повышает пропускная способность постоянной записи ввода-вывода подсистемы хранения. Он позволяет только для операций записи, сохраняется в буфере до шпинделей доступны для фиксации данных. При всех доступных операций ввода-вывода шпинделей в подсистеме хранилища используется пропускная способность течение длительных периодов времени, кэш со временем будет заполнить. Для очистки кэша, достаточно времени между пакетами или дополнительные физические диски, должны быть обслужены, чтобы обеспечить достаточное количество операций ввода-вывода для кэша на диск.

  Кэшей большего разрешение только для других данных сохраняется в буфере. Это означает, что может быть размещено более продолжительные отрезки насыщенность.

  В обычном режиме работы подсистемы хранения операционной системы могут возникнуть повышение производительности при записи, как только данные должны записываться в кэш. После мультимедиа насыщено ввода-вывода, заполнит кэш и производительность записи вернется к скорости работы жесткого диска.

- Если кэширование чтения ввода-вывода, сценарии, где кэша наиболее полезно при данных последовательно сохраняются на диске, а кэш можно упреждающего чтения (делает предположения, что следующий сектор с данными, будет запрашиваться далее).
- При чтении ввода-вывода является случайным, кэширование на контроллере диска вряд ли предоставить любое усовершенствование объем данных, который может быть считан с диска. Любое расширение не существует, если операционная система или размер кэша на основе приложения больше, чем размер кэша на основе оборудования.

  В случае с Active Directory кэша ограничивается только объемом памяти.

### <a name="ssd-considerations"></a>Рекомендации по SSD

Службы SSDs являются полностью отличается от жесткие диски на основе жестким диском. Остаются еще два ключа условия: «Сколько операций ввода-ВЫВОДА может его обрабатывать?» и «Какова задержка для этих операций ввода-ВЫВОДА?» По сравнению с жестким диском жесткие диски на основе SSDs можно обрабатывать большие объемы ввода-вывода и может иметь более низкую задержку. В целом, так и на момент написания этой статьи хотя по-прежнему стоимость при сравнении стоимость за каждый гигабайт, SSDs, они являются дорогостоящими с точки зрения затрат на-ввода-вывода и заслуживают оказывают значительного влияния с точки зрения производительности хранилища.

Замечания:

- Операций ввода-ВЫВОДА и задержки являются очень субъективным для схемы производитель и в некоторых случаях наблюдались быть понижению выполнения, чем жестким диском на основе технологий. Короче говоря важнее для просмотра и проверки спецификации производителя с диска и не считать любые generalities.
- Типы операций ввода-ВЫВОДА может иметь очень различное зависимости от того, доступен для чтения или записи. Службы AD DS, как правило, выполняется преимущественно чтения под управлением, будет меньше, чем некоторых других сценариев приложений.
- «Запись нагрузочное тестирование» — это концепция, согласно которой SSD ячеек со временем износ. Разных производителей имеют дело с этой задачи разных fashions. По крайней мере для диска базы данных, преимущественно чтения ввода-вывода профиль позволяет downplaying значимость эту проблему, так как данные изменяются не часто.

### <a name="summary"></a>Сводка

Один из способов думать о хранилище picturing бытовые коммуникаций. Imagine операций ввода-ВЫВОДА носителя, данные, сохраненные в — это бытовые основной стока. Когда это является засорения (например, корни в канале) или (это свернутый или слишком мал) limited, всем приемникам в семье резервного копирования, когда слишком много воды используется (слишком много гостей). Это вполне аналогично совместно используемой среде, где один или несколько систем используют преимущества общего хранилища на SAN/NAS/iSCSI с помощью того же базового носителя. Различные подходы можно предпринять для устранения различных сценариев:

- Свернутый или недостаточного размера стока требует замены полнофункциональных и исправление. Это будет выглядеть для добавления в новое оборудование или повторное распространение в системы с помощью общего хранилища во всей инфраструктуре.
- «Этой» канал обычно означает одна или несколько проблем, вызвавший ошибку код и удаления этих проблем. В сценарии хранения, это может быть хранилище или системе резервных копий уровня, синхронизированные антивирусного сканирования на всех серверах и выполнение программного обеспечения синхронизированных дефрагментация в периоды пиковой нагрузки.

В любой разработки магистрали несколько ее продвижения поступают в основной стока. Если ничего не один из этих продвижения или точку соединения, только те задачи, программной части, соединяющие точки резервного копирования. В случае хранения это может быть коммутатору перегруженных (сценарий SAN и NAS/iSCSI), проблем совместимости (неправильный драйвер/HBA сочетания Firmware/storport.sys) или резервное копирование, антивирусная программа или дефрагментации. Чтобы определить, является ли хранилище «канал» достаточно большой, операций ввода-ВЫВОДА и операций ввода-вывода размер должен измеряться. В каждой совместным добавьте их вместе, чтобы гарантировать достаточный «диаметр канала».

## <a name="appendix-d---discussion-on-storage-troubleshooting---environments-where-providing-at-least-as-much-ram-as-the-database-size-is-not-a-viable-option"></a>Приложение D - обсуждение на устранение неполадок службы хранилища - средах, где предоставляет по крайней мере столько ОЗУ, размер базы данных не является приемлемым вариантом

Рекомендуется понять, почему эти рекомендации находятся, поэтому изменения в технологии хранения может быть размещено. Эти рекомендации существуют по двум причинам. Первый — изоляции операций ввода-ВЫВОДА, таким образом, что проблемы с производительностью (которые разбиение по страницам) на ось операционной системы не влияет на производительность базы данных и профилей ввода-вывода. Второй — файлы журнала для AD DS (и в большинстве баз данных) идут последовательно по своей природе, что жесткие диски на основе жестким диском и кэшей имеют преимущество значительно повышая производительность при использовании с параметром последовательного ввода-вывода по сравнению с более случайный характер шаблонов ввода-вывода операционной системы и почти диск базы данных AD DS чисто случайными шаблонов ввода-вывода. Изолируя последовательных операций ввода-вывода на другой физический диск, можно увеличить пропускную способность. Представленных вариантов хранения современных проблема в том, что больше не выполняются Основные допущения за эти рекомендации. Во многих виртуализировать хранилище сценариев, таких как iSCSI, SAN, NAS и виртуальный диск файлы изображений, базовое хранилище, мультимедиа распределяется по нескольким узлам, тем самым полностью Инверсия «изоляции операций ввода-ВЫВОДА» и «оптимизационным последовательных операций ввода-вывода» аспекты. На самом деле эти сценарии добавить дополнительный уровень сложности, в том, что другие узлы, доступ к общего мультимедийного содержимого может привести к снижению скорости реагирования на контроллер домена.

При планировании производительности хранилища, существует три категории, которые следует учитывать: состояния кэша "холодных" состояние подготовки кэша и резервного копирования и восстановления. Состояния кэша "холодных" происходит в следующих сценариях времени изначально перезагрузки контроллера домена или перезапуска службы Active Directory, и нет данных Active Directory в оперативной памяти. Когда контроллер домена находится в устойчивом состоянии и кэшируется базы данных находится в состоянии «горячего» резервирования кэша. Это важно отметить, как они обеспечат очень разными показателями производительности и необходимости достаточный объем оперативной памяти для кэширования всей базы данных не повысить производительность при холодном кэша. Один рассмотрите возможность разработки производительности для этих двух сценариев с помощью следующей аналогией, подготовки "холодных" кэша «спринта» и сервер работает с кэшем "горячего" резервирования «marathon».

Для кэша "холодных" и "горячего" резервирования кеша вопрос становится, насколько быстро хранилище можно переместить данные с диска в память. Подготовки кэша — это сценарий, где, со временем, производительность улучшается, дополнительные запросы, повторно использовать данные, попадания в кэш увеличивает скорость и снижает частоту необходимости перейти на диск. В результате уменьшается негативно повлиять на производительность происходит на диск. Любой снижение производительности является временным только во время ожидания для кэша "теплые" и увеличиваться до максимального, зависящую от системы разрешенный размер. Диалог может быть упрощен до как быстро можно получить данные, с диска, а также является простой операций ввода-вывода в Active Directory, которой является субъективным доступных операций ввода-ВЫВОДА из базового хранилища. С точки зрения планирования поскольку подготовки кэш и резервное копирование и восстановление сценариев происходит на основе исключительных обычно происходят в нерабочие часы и являются субъективными с загрузкой контроллера домена, общие рекомендации отсутствуют за исключением в том, что эти действия планироваться для нерабочего времени.

AD DS, в большинстве случаев преимущественно считывается операций ввода-ВЫВОДА, обычно соотношением операций записи read/10% 90%. Чтения ввода-вывода часто имеет тенденцию быть узким местом для взаимодействия с пользователем, и с помощью операций записи ввода-ВЫВОДА, причины записи снизиться производительность. Как преимущественно случайных операций ввода-вывода для файла NTDS.dit, кэши, как правило, для обеспечения минимальной результативностью для чтения ввода-ВЫВОДА, благодаря чему намного важнее настроить хранилище для чтения ввода-вывода профиля правильно.

Для нормальных рабочих условиях следует хранилища планирования цель — свести к минимуму время ожидания для запроса из AD DS, возвращаемых с диска. По сути, это означает, что количество необработанных и ожидающих операций ввода-вывода меньше или равное числу пути к диску. Существует ряд способов для этого измерения. В сценарии мониторинга производительности, мы рекомендуем этот логический диск ( *\<диск для базы данных NTDS\>* ) \Avg Disk sec/Read быть меньше 20 мс. Требуемой операционной порог должен быть намного ниже, предпочтительно как можно ближе к скорости хранилища можно, в диапазоне 2 – 6 миллисекунды (.006.002 в секунду) в зависимости от типа хранилища.

Пример.

![Диаграмма задержки хранилища](media/capacity-planning-considerations-storage-latency.png)

Анализ на диаграмме.

- **Зеленый Овал слева —** задержка остается согласованным на 10 мс. От 800 операций ввода-ВЫВОДА для операций ввода-ВЫВОДА 2400 увеличения нагрузки. Это абсолютный floor, насколько быстро запрос ввода-вывода может обрабатываться базовое хранилище. Это зависит от особенностей решение хранилища.
- **Бордового Овал справа —** пропускная способность остается неизменным из выход зеленый круг через в конец коллекции данных в во время задержки продолжает увеличиваться. Это демонстрации, что при тома запроса превышают физические ограничения базового хранилища, тем больше запросов тратят находятся в очереди будут отправлены в подсистеме хранилища.

Применение этой базы знаний:

- **Влияние на запросе членства большой группы —** предполагается это требуется считать 1 МБ данных с диска, объем операций ввода-вывода и время можно вычислить следующим образом:
  - Страниц базы данных Active Directory — 8 КБ в размере. 
  - Не менее 128 страниц должны считываться с диска. 
  - При условии, что ничего не кэшируются, в floor (10 мс), это будет принимать 1,28 с как минимум для загрузки данных с диска, чтобы вернуть его клиенту. В 20 мс, где давно израсходован пропускная способность хранилища, а также это рекомендуемое максимальное, займет 2,5 секунд для получения данных с диска, чтобы вернуть его конечному пользователю.  
- **Как часто будет быть подготовлены кэша —** вносить в предположении, что загрузки клиента будет максимально увеличить пропускную способность, в этом примере хранилища, кэш будет "теплые" со скоростью операций ввода-ВЫВОДА 2400 &times; 8 КБ на операции ввода-ВЫВОДА. Или же приблизительно 20 МБ/с на во-вторых, загрузка около 1 ГБ базы данных в оперативной памяти каждого 53 секунды.

> [!NOTE]
> Это нормально для коротких промежутков времени, который нужно контролировать карабкаться задержек при компоненты агрессивно чтения или записи на диск, например, когда система выполняется резервное копирование или когда AD DS выполняется сбор мусора. Для размещения этих периодические действия должны предоставляться дополнительного головного пространства на основе вычисления. Целью для обеспечивают достаточную пропускную способность реализовать эти сценарии без ущерба для обычной функции.

Как можно увидеть, есть физическое ограничение, основанное на структуре хранилища, чтобы скорость возможно можно подготовить кэш. Что будет подготавливающих кэш входящих клиентских запросов до скорость, предоставляющий базовое хранилище. Выполнение сценариев, чтобы «предварительно подготовить» кэша в часы пик предоставит конкурс для загрузки на основе реальных клиентских запросов. Что может отрицательно сказаться на предоставление данных, клиенты сначала должны так, как намеренно, он создает конкурентной борьбы за дефицитные дисковые ресурсы как искусственный попыток подготавливающих кэш будет загружать данные, которые не относятся к клиентам, обратившись в службу контроллера домена.
