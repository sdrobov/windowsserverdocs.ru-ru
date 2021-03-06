---
title: Использование службы времени Windows для отслеживания
description: Согласно нормативам во многих сферах требуются системы для отслеживания в формате UTC.  Это означает, что должно подтверждаться определенное смещение времени системы относительно UTC.
author: dcuomo
ms.author: dacuo
manager: dougkim
ms.date: 10/17/2018
ms.topic: article
ms.prod: windows-server
ms.technology: networking
ms.openlocfilehash: d58bf445fb8eab25d90a9a837cc038cb3c8109d6
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517659"
---
# <a name="windows-time-for-traceability"></a>Использование службы времени Windows для отслеживания
>Применяется к: Windows Server 2016 версии 1709 или более поздних, а также Windows 10 версии 1703 или более поздних.

Согласно нормативам во многих сферах требуются системы для отслеживания в формате UTC.  Это означает, что должно подтверждаться определенное смещение времени системы относительно UTC.  Согласно сценариям соответствия нормативным требованиям Windows 10 (версии 1703 и более поздних версий) и Windows Server 2016 (версия 1709 и более поздних версий) предоставляют новые журналы событий, чтобы описать картину с точки зрения операционной системы и сформировать понимание действий, выполняемых в системных часах.  Эти журналы событий создаются постоянно для службы времени Windows. Их можно проверять и архивировать для последующего анализа.

Новые события позволяют получить ответы на следующие вопросы:

* изменились ли системные часы;
* изменилась ли тактовая частота;
* изменилась ли конфигурация Службы времени Windows.

## <a name="availability"></a>доступность;

Эти улучшения включены в Windows 10 версии 1703 и более поздние версии, а также в Windows Server 2016 версии 1709 и более поздние версии.

## <a name="configuration"></a>Конфигурация

Чтобы использовать эту возможность, дополнительная настройка не требуется.  Создание журналов событий включено по умолчанию, и их можно найти в средстве просмотра событий в канале **Applications and Services Log\Microsoft\Windows\Time-Service\Operational**.

## <a name="list-of-event-logs"></a>Список журналов событий

В следующем разделе описываются события, регистрируемые для использования в сценариях отслеживания.

# <a name="257"></a>[257](#tab/257)

Это событие регистрируется при запуске службы времени Windows (W32Time) и записывает сведения о текущем времени, текущее количество тактов, конфигурацию среды выполнения, поставщики времени и текущую частоту синхронизации.

|Описание события |Запуск службы |
|---|---|
|Подробности |Происходит при запуске W32Time |
|Зарегистрированные данные |<ul><li>Текущее время в формате UTC</li><li>Текущий счетчик тактов</li><li>Конфигурация W32Time</li><li>Конфигурация поставщика времени</li><li>Частота синхронизации</li></ul> |
|Механизм регулирования  |Нет. Это событие происходит при каждом запуске службы. |

**Пример.**

```
W32time service has started at 2018-02-27T04:25:17.156Z (UTC), System Tick Count 3132937.
```

**Команда:**

Эти сведения также можно запросить с помощью следующих команд.

*W32Time и конфигурация поставщика времени*

```
w32tm.exe /query /configuration
```

*Частота синхронизации*
```
w32tm.exe /query /status /verbose
```

# <a name="258"></a>[258](#tab/258)

Это событие регистрируется при остановке службы времени Windows (W32Time) и записывает сведения о текущем времени и частоте синхронизации.

|Описание события |Остановка службы |
|---|---|
|Подробности |Происходит при остановке W32Time |
|Зарегистрированные данные |<ul><li>Текущее время в формате UTC</li><li>Текущий счетчик тактов</li></ul> |
|Механизм регулирования  |Нет. Это событие срабатывает при каждой остановке службы. |

**Пример текста:** 
`W32time service is stopping at 2018-03-01T05:42:13.944Z (UTC), System Tick Count 6370250.`

# <a name="259"></a>[259](#tab/259)

С этим событием периодически регистрируется текущий список источников времени и выбранный источник времени.  Кроме того, регистрируется текущее количество тактов.  Это событие не происходит при каждом изменении источника времени.  Эту функциональность предоставляют другие события, перечисленные далее в этом документе.

|Описание события |Периодическое состояние поставщика NTP-клиента |
|---|---|
|Подробности |Список источников времени, которые использует NTP-клиент |
|Зарегистрированные данные |<ul><li>Доступные источники времени</li><li>Выбранный сервер отсчета времени на момент ведения журнала</li><li>Текущий счетчик тактов</li></ul> |
|Механизм регулирования  |Заносится в журнал каждые 8 часов. |

**Пример текста:** NTP Client provider periodic status:

Ntp Client is receiving time data from the following NTP Servers:

server1.fabrikam.com,0x8 (ntp.m|0x8|[::]:123->[IPAddress]:123)server2.fabrikam.com,0x8 (ntp.m|0x8|[::]:123->[IPAddress]:123); and the chosen reference time server is Server1.fabrikam.com,0x8 (ntp.m|0x8|[::]:123->[IPAddress]:123) (RefID:0x08d6648e63). System Tick Count 13187937

**Команда.** Эти сведения также можно запросить с помощью следующих команд.

*Одноранговые узлы идентификации*
`w32tm.exe /query /peers`

# <a name="260"></a>[260](#tab/260)

|Описание события |Конфигурация и состояние службы времени |
|---|---|
|Подробности |Служба W32Time периодически регистрирует данные о своих конфигурации и состоянии. Это эквивалент вызова:<br><br>`w32tm /query /configuration /verbose`<br>ИЛИ<br>`w32tm /query /status /verbose` |
|Механизм регулирования  |Заносится в журнал каждые 8 часов. |

# <a name="261"></a>[261](#tab/261)

Каждый экземпляр записывается в журнал при изменении системного времени с помощью API SetSystemTime.

|Описание события |Системное время задано. |
|---|---|
|Механизм регулирования  |Нет.<p>Это редко происходит в системах с рациональной синхронизацией времени и нам требуется регистрировать каждый такой случай. Параметр TimeJumpAuditOffset следует игнорировать при регистрации этого события, так как он предназначен для регулирования событий в журнале системных событий Windows. |

# <a name="262"></a>[262](#tab/262)

|Описание события |Частота системных часов скорректирована. |
|---|---|
|Подробности |Служба W32Time постоянно изменяет частоту системных часов, если синхронизация часов происходит часто. Нам необходимо получить значимые изменения частоты часов без перезапуска журнала событий. |
|Механизм регулирования  |Настройки часов ниже значения TimeAdjustmentAuditThreshold (минимальное — 128 миллионных долей, по умолчанию — 800 миллионных долей) не регистрируются.<p>Изменения частоты часов на 2 доли в минуту с текущей степенью детализации добавляет 120 мкс/с к точности часов.<p>В синхронизированной системе большая часть корректировок выполняется ниже этого уровня. Если требуется более точное отслеживание, этот параметр можно скорректировать, уменьшив значение, или использовать PerfCounters. Также можно выполнить оба действия. |

# <a name="263"></a>[263](#tab/263)

|Описание события |Изменение параметров службы времени или списка загруженных поставщиков времени. |
|--|--|
|Подробности |Повторное чтение параметров W32Time может привести к изменению определенных критических параметров в памяти, что может повлиять на общую точность синхронизации времени.<br><br>Служба W32Time регистрирует каждое событие при повторном считывании его параметров, что обеспечивает потенциальное влияние на синхронизацию времени. |
|Механизм регулирования  |Нет.<br><br>Это событие возникает только тогда, когда администратор или групповая политика изменяют поставщиков времени, а затем активируют службу W32Time. Нам нужно записать каждый экземпляр изменения параметров. |

# <a name="264"></a>[264](#tab/264)

|Описание события |Изменение источников времени, которые использует NTP-клиент. |
|---|---|
|Подробности |NTP-клиент записывает событие с текущим состоянием серверов или узлов времени, когда состояние сервера или однорангового узла изменяется (**Ожидание -> Синхронизация**, **Синхронизация -> Недоступно** или при других переходах). |
|Механизм регулирования  |Максимальная частота — только один раз в 5 минут для защиты журнала от временных проблем и неправильной реализации поставщика. |

# <a name="265"></a>[265](#tab/265)

|Описание события |Изменение источника или номера страты службы времени. |
|---|---|
|Подробности |Источник времени и номер страты W32Time — это важные факторы, влияющие на возможность отслеживания времени, и все изменения, внесенные в них, должны регистрироваться. Если у службы W32Time нет источника времени и вы не настроили ее в качестве надежного источника времени, то она перестанет объявляться в качестве сервера времени и будет отвечать на запросы недопустимыми параметрами. Это событие важно для отслеживания изменений состояния в топологии NTP. |
|Механизм регулирования  |Нет. |

# <a name="266"></a>[266](#tab/266)

|Описание события |Запрошено время повторной синхронизации. |
|---|---|
|Подробности |Эта операция активируется:<ul><li>при изменении сети;</li><li>если система восстанавливается из подключенного режима ожидания или гибернации;</li><li>если в течение длительного времени не выполнялась синхронизация;</li><li>администратор отправил команду повторной синхронизации.</li></ul>Эта операция приводит к немедленной утрате точности синхронизации времени, так как NTP-клиент очищает свои фильтры. |
|Механизм регулирования  |Максимальная частота — каждые 5 минут.<br><br>Возможно, что нерабочая сетевая карта (или плохой скрипт) может повлечь повторную активацию этой операции и привести к переполнению журналов. Следовательно, это событие необходимо регулировать.<br><br>Обратите внимание, что для достижения точной синхронизации времени требуется гораздо больше 5 минут, а регулирование не приводит к потере сведений об изначальном событии, которое повлияло на снижение точности времени.  |
