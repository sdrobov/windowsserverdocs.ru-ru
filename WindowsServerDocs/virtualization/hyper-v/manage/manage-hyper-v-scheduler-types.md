---
title: Общие сведения о и использовании типов заданий гипервизора Hyper-V
description: Предоставляет сведения для администраторов узла Hyper-V на первый взгляд Диспетчер Hyper-V режимы
author: allenma
ms.author: allenma
ms.date: 08/14/2018
ms.topic: article
ms.prod: windows-server-hyper-v
ms.technology: virtualization
ms.localizationpriority: low
ms.assetid: 6cb13f84-cb50-4e60-a685-54f67c9146be
ms.openlocfilehash: 7af6d68b02367d349580eacb27405c6f37e97ff8
ms.sourcegitcommit: 3883eebbba70bfea0221e510863ee1a724a5f926
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2018
ms.locfileid: "5783696"
---
# Управление типами планировщика гипервизора Hyper-V

>Область применения: Windows 10, Windows Server 2016, Windows Server версии 1709, Windows Server версии 1803, Windows Server 2019

В этой статье описываются новые режимы виртуального процессора, планирование логику, впервые появились в Windows Server 2016. Эти режимы, или типы заданий, определяют, как гипервизора Hyper-V выделяет и управляет работы на разных виртуальных процессоров гостевой. Администратор узла Hyper-V можно выбрать типы планировщик низкоуровневой оболочки, которые лучше всего подходят для гостевых виртуальных машин (ВМ) и настройте виртуальные машины, чтобы воспользоваться преимуществами планирования логику.

>[!NOTE]
>Обновления необходимы для использования функций планировщика низкоуровневой оболочки, описанной в этом документе. Дополнительные сведения см. в разделе [обязательных обновлений](#required-updates).

## Фон

Прежде чем обсуждать логики и элементы управления за Hyper-V использования виртуального процессора, полезно ознакомьтесь с основными понятиями, описанные в этой статье.

### Общие сведения о SMT

Одновременное многопоточность или SMT, — это метод, применяемых в проектах современный процессор, позволяющий ресурсов процессора для совместного использования отдельные, независимые выполнение потоков. SMT обычно ускорение скромные производительности для большинства рабочих нагрузок, параллелизации вычислений, когда это возможно, Повышение пропускной способности инструкций, обеспечивающий на то, что производительность не получаете или даже небольшое потери производительности может возникнуть, если конфликтов между потоков для Происходит, ресурсы общего процессора.
Процессоры, поддерживающие SMT доступны из Intel и AMD. Intel относится к их SMT предложения как Intel технологии Hyper Threading или Intel HT.

Для целей этой статьи описания SMT и как его использовать с помощью Hyper-V одинаково применяются к систем Intel и AMD.

* Дополнительные сведения о технологии HT Intel см. [Технологией Hyper Threading](https://www.intel.com/content/www/us/en/architecture-and-technology/hyper-threading/hyper-threading-technology.html)

* Дополнительные сведения о AMD SMT см. [Базовую архитектуру «Zen»](https://www.amd.com/en/technologies/zen-core)

## Общие сведения о том, как Hyper-V виртуализирует процессоров

Перед типы заданий низкоуровневой оболочки, это также необходимо понять архитектура Hyper-V. Общая сводка можно найти в [Обзор технологии Hyper-V](https://docs.microsoft.com/windows-server/virtualization/hyper-v/hyper-v-technology-overview). Ниже перечислены важные понятия в этой статье.

* Hyper-V создает и администрирует разделы виртуальной машины, на какой вычислений ресурсы распределяются и общий доступ, под контроль над гипервизор. Разделы обеспечивают надежную изоляции границы между всеми гостевым виртуальным машинам и гостевые виртуальные машины и корневой раздел.

* Корневой раздел сам является раздела виртуальной машины, несмотря на то, что он имеет уникальные свойства и гораздо больше прав, чем гостевым виртуальным машинам. Корневой раздел предоставляет службы управления, которые управляют все гостевых виртуальных машин, обеспечивает поддержку виртуальное устройство для гостей и управляет все устройства ввода-вывода для гостевых виртуальных машин. Корпорация Майкрософт настоятельно рекомендует не под управлением любой рабочие нагрузки приложений в корневом разделе.

* Каждого виртуального процессора (ВИЦЕ) корневой раздел является сопоставления 1:1 для базовой логический процессор (LP). Узел ВИЦЕ всегда будет выполняться на том же базового LP: его невозможно без переноса вице-президенты корневой раздел.

* По умолчанию логические процессоры, на которых работают вице-президенты узла можно также запустить вице-президенты гостя.

* Гость ВИЦЕ может быть запланирован гипервизором для запуска на любом доступном логические процессоре. Хотя планировщик гипервизора отвечает необходимо учитывать расположение временного кэша, топологию NUMA и многих других факторов при планировании ВИЦЕ гостя, в конечном счете ВИЦЕ может быть запланировано на любом узле LP.

## Типы заданий низкоуровневой оболочки

Начиная с Windows Server 2016, гипервизор Hyper-V поддерживает несколько режимов логики планировщик заданий, которые определяют, как запланировать виртуальных процессоров на базовой логических процессоров низкоуровневой оболочки. Эти типы заданий являются:

- [Планировщик классического, справедливом распределении](#the-classic-scheduler)
- [Планировщик core](#the-core-scheduler)
- [Планировщик корневой](#the-root-scheduler)

### Классический планировщик заданий

Классический планировщик был по умолчанию для всех версий гипервизор Windows Hyper-V с момента ее создания, в том числе Windows Server 2016 Hyper-V. Классический планировщик обеспечивает равноправный общую папку, прерыванием циклического планирования модель виртуальных процессоров гостевой.

Тип планировщика классический лучше всего подходит для подавляющего большинства традиционных Hyper-V использует — для частных облаков, размещения поставщиков и т. д. Показатели производительности хорошо вам понятны и лучше всего оптимизирован для поддержки широкий спектр сценариев виртуализации, например чрезмерных подписки вице-президенты логическим процессорам, управлением многие гетерогенной виртуальных машин и рабочих нагрузок одновременно, под управлением более масштабные высокой производительность виртуальных машин, поддержка функцию полный набор Hyper-V без ограничений и многое другое.

### Планировщик core

Планировщик core гипервизор является новая альтернатива классический планировщика логики, в Windows Server 2016 и Windows 10 версии 1607. Планировщик core предлагает граница надежной системы безопасности для изоляции гостя рабочей нагрузки и особенностей снижение производительности для рабочих нагрузок внутри виртуальных машин, работающих на узле с поддержкой SMT виртуализации. Планировщик core позволяет одновременно под управлением SMT и не SMT виртуальных машин на одном узле с поддержкой SMT виртуализации.

Планировщик core использует топологию SMT на узле виртуализации, а также при необходимости предоставляет пар SMT гостевых виртуальных машин и группы расписания гостевых виртуальных процессоров с той же виртуальной машины на группы SMT логических процессоров. Это делается симметрично, если логические процессоры находятся в группы два, вице-президенты приходят в группах двух ядро никогда не распределяется между виртуальными машинами.
Запланирована ВИЦЕ для виртуальной машины без SMT включена, что ВИЦЕ используют всего основного, когда оно запускается.

Общий результат планировщика основной том, что:

* Гость вице-президенты ограничиваются для запуска на лежащую пар физическое ядро, изолируя виртуальную Машину для процессора основной границы, что сокращает уязвимость к атакам отслеживание канала от вредоносных виртуальных машин.

* Разброса пропускную способность, значительно уменьшается.

* Потенциально снижается, потому что если только один из группы вице-президенты может быть запущено, только один из потоков инструкций в основном выполняемого во время других не используется.

* ОС и приложений, работающих в гостевой виртуальной машины можно использовать поведение SMT и интерфейсам (API) для управления и распределения рабочего потока SMT, так же, как они бы при выполнении без виртуализации.

* Граница надежной системы безопасности для изоляции рабочей нагрузки гостевой - вице-президенты гостевой ограничиваются для запуска на базовой пары физическое ядро, сокращает уязвимость к атакам отслеживание канала.

Планировщик core будут использоваться по умолчанию, начиная с Windows Server 2019. В Windows Server 2016 планировщик core не является обязательным и должно быть явно включено, администратор узла Hyper-V и классический планировщик значение по умолчанию.

#### Поведение планировщика ядра с узлом SMT отключено

Если гипервизор настроено для использования тип планировщика core, но возможность SMT отключено или отсутствует на узле виртуализации, гипервизор будет использовать поведение классический планировщика, независимо от того, параметр типа планировщика низкоуровневой оболочки.

### Планировщик корневой

Планировщик корневой впервые появилась в Windows 10 версии 1803. При включении корневой тип планировщика гипервизор cedes управления планирования работы, который корневой раздел. Планировщик NT в экземпляре ОС корневой раздел управляет всеми аспектами планирования рабочих систему логические процессоры.

Планировщик корневой рассматриваются особые требования, случай с поддержкой раздел служебной программы для обеспечения изоляции надежной рабочей нагрузки, служащие с в Защитнике Windows Application Guard (WDAG). В этом случае оставлять планирования обязанности к корню ОС имеет ряд преимуществ. Например элементы управления ресурсами ЦП, применимы к сценариях с контейнерами может использоваться с раздела служебную программу, упрощением развертывания и управления. Кроме того планировщик ОС корневой можно легко собирать показатели о рабочей нагрузки ЦП в контейнере и использовать эти данные в качестве входных данных для одного планирования политики, применимых для других рабочих нагрузок в системе. Эти же метрики также поможет четко атрибут работать Готово в контейнере приложения для системы узла. Для отслеживания этих показателей труднее с рабочими нагрузками традиционных виртуальной машины, где некоторые действия от имени всех запущенных Виртуальной машины происходит в корневой раздел.

#### Использование планировщика корневой на клиентских систем

Начиная с Windows 10 версии 1803, планировщик корневой используется по умолчанию клиента только в системах, где низкоуровневая оболочка может быть включена функция поддержки безопасности на основе виртуализации и изоляция WDAG рабочей нагрузки, а также для правильной работы будущем в системах с типы архитектуры разнородными core. Это конфигурация планировщика единственным поддерживаемым низкоуровневой оболочки для клиентских систем. Администраторы не следует пытаться переопределить тип планировщика низкоуровневой оболочки по умолчанию на клиентских систем Windows 10.

#### Элементы управления ресурсами ЦП виртуальной машины и планировщик корневой

Элементы управления ресурсами процессора виртуальной машины, предоставляемые Hyper-V, не поддерживаются при включении планировщика корневой гипервизора как логика планировщика корневой операционной системы управление ресурсами узла глобально и не имеет сведений виртуальной Машины определенные параметры конфигурации. Hyper-V-VM процессора элементов управления ресурсами, например caps, насыщенности и резервный, применимы только там, где гипервизор непосредственно управляет ВИЦЕ планирования, например по сравнению с типами планировщика классический и core.

#### Используется планировщик корневой серверных систем

Планировщик корневой не рекомендуется для использования с Hyper-V на серверах в настоящее время, как ее рабочие характеристики еще не были полностью из особенностей и придавать могла широкий спектр типично для многих развертывание виртуализации серверов рабочих нагрузок.

## Включение SMT в гостевых виртуальных машин

После настройки узел виртуализации низкоуровневая оболочка использовать тип планировщика core гостевым виртуальным машинам могут быть настроены для использования SMT при необходимости. Предоставление доступа к тем, что вице-президенты являются гиперпотоковых на гостевой виртуальной машине позволяет планировщик заданий в гостевой операционной системы и рабочие нагрузки, работающие в виртуальной Машины, чтобы определять и использовать топологии SMT в собственные рабочие планирование. В Windows Server 2016 гостевой SMT настроен по умолчанию и должен быть включен явно администратор узла Hyper-V. Начиная с Windows Server 2019 новые виртуальные машины на узле будет наследовать топологии SMT основного приложения по умолчанию.  То есть версии 9.0 виртуальных Машин, созданных на узле с 2 потока SMT на ядро бы см. также 2 потока SMT на ядро.

Необходимо использовать PowerShell для включения SMT гостевой виртуальной машине; Нет не пользовательский интерфейс, предоставляемый в диспетчере Hyper-V.
Чтобы включить SMT в гостевой виртуальной машины, откройте окно PowerShell с необходимых разрешений и введите:

``` powershell
Set-VMProcessor -VMName <VMName> -HwThreadCountPerCore <n>
```

Где <n> — это число потока SMT на ядро гостевой виртуальной Машины будет видеть.  
Обратите внимание, что <n> = 0 будет значение HwThreadCountPerCore соответствует количеству потока SMT узла каждого значения core.

>[!NOTE] 
>Параметр HwThreadCountPerCore = 0 реализована, начиная с Windows Server 2019.

Ниже приведен пример сведения о системе, взятый из виртуальную машину с 2 виртуальных процессоров гостевой операционной системы и SMT включена. Гостевая операционная система определение 2 логических процессоров, принадлежащих то же ядро.

![Снимок экрана, показывающий msinfo32 в гостевой виртуальной Машины с помощью SMT включен](media/Hyper-V-CoreScheduler-VM-Msinfo32.png)

## Настройка типа планировщика низкоуровневой оболочки в Windows Server 2016 Hyper-V

Windows Server 2016 Hyper-V использует модель планировщика классический низкоуровневой оболочки по умолчанию. Гипервизор могут настраиваться при необходимости использовать планировщик core, чтобы повысить безопасность путем ограничения доступа вице-президенты гостевой для запуска на соответствующие физические SMT пары, которые поддерживают использование виртуальных машин с помощью SMT Настройка расписания для своих вице-президенты гостевой.

>[!NOTE]
>Корпорация Майкрософт рекомендует, что все клиенты под управлением Windows Server 2016 Hyper-V выберите планировщика core, чтобы убедиться, что их узлы виртуализации оптимально защищены от потенциально вредоносных гостевые виртуальные машины.

## По умолчанию Windows Server 2019 Hyper-V использует планировщик core

Чтобы убедиться, что узлы Hyper-V при развертывании конфигурации оптимальной безопасности, Windows Server 2019 Hyper-V теперь используют модели core гипервизора планировщика по умолчанию. Администратору узла может при необходимости настройки узла использовать устаревшие планировщика классический. Администраторам следует внимательно прочитайте, понять и учитывать последствиями, который есть у каждого типа заданий на безопасность и производительность узлы виртуализации до переопределение параметров по умолчанию типа планировщика.  Дополнительные сведения см. [Выбор типа планировщика Общие сведения о Hyper-V](https://docs.microsoft.com/windows-server/virtualization/hyper-v/manage/understanding-hyper-v-scheduler-type-selection) .

### Обязательные обновления

>[!NOTE]
>Перечисленные ниже обновления необходимы для использования функций планировщика низкоуровневой оболочки, описанной в этом документе. Эти обновления включают изменения для поддержки новый вариант BCD «hypervisorschedulertype», который необходим для настройки хост-сервера.

| Версия | Выпуск  | Требуется обновление | Статье базы Знаний |
|--------------------|------|---------|-------------:|
|Windows Server 2016 | 1607 | 2018.07 C | [KB4338822](https://support.microsoft.com/help/4338822/windows-10-update-kb4338822) |
|Windows Server 2016 | 1703 | 2018.07 C | [KB4338827](https://support.microsoft.com/help/4338827/windows-10-update-kb4338827) |
|Windows Server 2016 | 1709 | 2018.07 C | [KB4338817](https://support.microsoft.com/help/4338817/windows-10-update-kb4338817) |
|Windows Server 2019 г. | 1804 | Нет | Нет |

## Выбор типа планировщика низкоуровневой оболочки в Windows Server

Настройка планировщика заданий гипервизора управляется с помощью запись BCD hypervisorschedulertype.

Чтобы выбрать тип планировщик, откройте командную строку с правами администратора:

``` command
     bcdedit /set hypervisorschedulertype type
```

Где `type` — это один из:

* Классический
* Базовая

Система необходимо перезагрузить любые изменения типа планировщика гипервизора вступили в силу.

>[!NOTE]
>Планировщик корневой низкоуровневой оболочки не поддерживается на сервере Hyper-V в Windows в данный момент. Администраторам Hyper-V не следует пытаться Настройка планировщика корневой для использования с помощью сценариев виртуализации серверов.

## Определение типа текущего планировщика

Вы можете определить текущий тип планировщика гипервизора используются изучать системный журнал в средстве просмотра событий самые последние презентация гипервизора ID 2 сообщает о типе планировщика низкоуровневой оболочки, настроить при запуске низкоуровневой оболочки. События запуска низкоуровневой оболочки можно получить из средства просмотра событий Windows или через PowerShell.

Гипервизор презентация ID 2 обозначает тип планировщика низкоуровневой оболочки, где:

    1 = Classic scheduler, SMT disabled

    2 = Classic scheduler

    3 = Core scheduler

    4 = Root scheduler

![Снимок экрана, сведения о событии ID 2 показана гипервизора запуска](media/Hyper-V-CoreScheduler-EventID2-Details.png)

![Снимок экрана, показывающий средство просмотра событий гипервизора презентация ID 2](media/Hyper-V-CoreScheduler-EventViewer.png)

### Запрос Hyper-V гипервизора планировщика тип презентация с помощью PowerShell

Для запроса для события гипервизора ID 2 с помощью PowerShell, введите этих следующие команды из командной строки PowerShell.

``` powershell
Get-WinEvent -FilterHashTable @{ProviderName="Microsoft-Windows-Hyper-V-Hypervisor"; ID=2} -MaxEvents 1
```

![Снимок экрана, показывающий PowerShell запросов и результатов для гипервизора презентация ID 2](media/Hyper-V-CoreScheduler-PowerShell.png)