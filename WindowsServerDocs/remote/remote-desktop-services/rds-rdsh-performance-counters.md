---
title: Диагностика проблем со скоростью реагирования приложений на узлах сеансов удаленных рабочих столов с помощью счетчиков производительности
description: Ваше приложение медленно работает в сеансе удаленного рабочего стола? Узнайте о счетчиках производительности, с помощью которых можно выполнять диагностику проблем с производительностью приложения на узле сеанса удаленного рабочего стола.
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.author: elizapo
ms.date: 07/11/2019
ms.topic: article
author: lizap
manager: dougkim
ms.localizationpriority: medium
ms.openlocfilehash: 7e08e4aa0cd1298502c59a1a8275293910345d6a
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966196"
---
# <a name="use-performance-counters-to-diagnose-app-performance-problems-on-remote-desktop-session-hosts"></a>Диагностика проблем с производительностью приложений на узлах сеансов удаленных рабочих столов с помощью счетчиков производительности

> Применяется к: Windows Server 2019, Windows 10

Плохая производительность приложений (когда приложения работают медленно или не отвечают) — одна из самых сложных проблем в плане диагностики. В большинстве случаев диагностику начинают со сбора данных о ЦП, памяти, дисковых операциях ввода/вывода и других метриках, после чего пытаются выяснить причину проблемы с помощью таких средств, как Windows Performance Analyzer. К сожалению, в большинстве случаев эти данные не помогают определить основную причину, так как данные счетчиков потребления ресурсов часто существенно колеблются. Из-за этого трудно сопоставить прочитанные данные с обнаруженной проблемой. Чтобы помочь вам быстрее устранять проблемы с производительностью приложений, мы добавили несколько новых счетчиков производительности (доступных [для загрузки](#download-windows-server-insider-software) через [Программу предварительной оценки Windows](https://insider.windows.com)), которые измеряют потоки ввода данных пользователем.

> [!NOTE]
> Счетчик задержки ввода данных пользователем совместим только с такими ОС:
> - Windows Server 2019 или более поздней версии;
> - Windows 10 версии 1809 или более поздней.

Счетчик задержки ввода данных пользователем может помочь быстро определить основную причину медленной производительности в рамках сеанса удаленного рабочего стола. Этот счетчик измеряет, какой период времени ввод данных пользователем (например, с помощью мыши или клавиатуры) остается в очереди перед тем, как процесс его подхватит. Он работает в локальных и удаленных сеансах.

На следующем рисунке показано примерное представление потока ввода данных пользователем, поступающего от клиента к приложению.

![Удаленный рабочий стол. Ввод данных пользователем поступает от пользовательского клиента удаленного рабочего стола к приложению](./media/rds-user-input.png)

Счетчик задержки ввода данных пользователем измеряет максимальную разницу (в пределах интервала времени) между тем, когда ввод помещается в очередь и когда приложение получает его в [традиционном цикле обработки сообщений](/windows/win32/winmsg/about-messages-and-message-queues#message-loop), как показано на следующей блок-схеме.

![Удаленный рабочий стол. Поток счетчика производительности — счетчик задержки ввода данных пользователем](./media/rds-user-input-delay.png)

Следует отметить, что этот счетчик сообщает максимальную задержку ввода данных пользователем в пределах настраиваемого интервала. Это самое продолжительное время, за которое ввод поступает в приложение, что может повлиять на скорость выполнения важных видимых действий, таких как ввод.

Например, в приведенной ниже таблице задержка ввода данных пользователем в пределах этого интервала будет составлять 1000 мс. Счетчик сообщает наибольшую задержку ввода данных пользователем в пределах интервала, потому что пользователь рассматривает медленную реакцию как самое медленное время ввода (максимальное), а не как среднюю скорость всех вводов данных.

| Номер |   0   |   1   |    2     |
| ------ | ----- | ----- | -------- |
| Задержка  | 16 мс | 20 мс | 1000 мс |

## <a name="enable-and-use-the-new-performance-counters"></a>Включение новых счетчиков производительности и их использование

Чтобы использовать эти новые счетчики производительности, необходимо сначала включить раздел реестра, выполнив следующую команду:

```
reg add "HKLM\System\CurrentControlSet\Control\Terminal Server" /v "EnableLagCounter" /t REG_DWORD /d 0x1 /f
```

> [!NOTE]
> Если вы используете Windows 10, версия 1809 или более поздняя, либо Windows Server, версия 2019 или более поздняя, вам не требуется включать раздел реестра.

После этого нужно перезапустить сервер. Затем откройте системный монитор и щелкните значок плюс (+), как показано на следующем снимке экрана.

![Удаленный рабочий стол. Снимок экрана, где показано, как добавить счетчик производительности "Задержка ввода данных пользователем"](./media/rds-add-user-input-counter-screen.png)

После этого появится диалоговое окно "Добавить счетчики", где можно выбрать пункт **User Input Delay per Process** (Задержка ввода данных пользователем на процесс) или **User Input Delay per Session** (Задержка ввода данных пользователем на сеанс).

![Удаленный рабочий стол. Снимок экрана, где показано, как добавить счетчик "Задержка ввода данных пользователем на сеанс"](./media/rds-user-delay-per-session.png)

![Удаленный рабочий стол. Снимок экрана, где показано, как добавить счетчик "Задержка ввода данных пользователем на процесс"](./media/rds-user-delay-per-process.png)

После того как вы выберете вариант **User Input Delay per Process** (Задержка ввода данных пользователем на процесс), в одноименном разделе отобразятся **экземпляры выбранного объекта** (другими словами, процессы) в формате ```SessionID:ProcessID <Process Image>```.

Например, если Калькулятор выполняется в [сеансе с идентификатором 1](/previous-versions/iis/6.0-sdk/ms524326(v=vs.90)), вы увидите ```1:4232 <Calculator.exe>```.

> [!NOTE]
> Учитываются не все процессы. Вы не увидите процессы, запущенные как системные.

Счетчик начинает отправку отчетов о задержке ввода данных пользователем сразу после того, как вы его добавите. Обратите внимание, что максимальный масштаб по умолчанию — 100 (мс).

![Удаленный рабочий стол. Пример действия, сообщенного счетчиком задержки ввода данных пользователя на процесс в системном мониторе](./media/rds-sample-user-input-delay-perfmon.png)

Теперь давайте рассмотрим счетчик **задержки ввода данных пользователем на сеанс**. Для каждого идентификатора сеанса есть экземпляры, и их счетчики показывают задержку ввода данных пользователем для любого процесса в указанном сеансе. Кроме того, есть еще два экземпляра — "Макс." (максимальная задержка ввода данных пользователем во всех сеансах) и "Средний" (средняя задержка во всех сеансах).

В этой таблице представлен визуальный пример этих экземпляров. (Те же сведения можно получить в системном мониторе, переключившись на тип графа "Отчет".)

| Тип счетчика | Имя экземпляра | Сообщенная задержка (мс) |
| --------------- | ------------- | ------------------- |
| Задержка ввода данных пользователем на процесс | 1:4232 <Calculator.exe> |    200 |
| Задержка ввода данных пользователем на процесс | 2:1000 <Calculator.exe> |     16 |
| Задержка ввода данных пользователем на процесс | 1:2000 <Calculator.exe> |     32 |
| Задержка ввода данных пользователем на сеанс | 1 |    200 |
| Задержка ввода данных пользователем на сеанс | 2 |     16 |
| Задержка ввода данных пользователем на сеанс | Среднее |     108 |
| Задержка ввода данных пользователем на сеанс | Макс. |     200 |

## <a name="counters-used-in-an-overloaded-system"></a>Счетчики, используемые в перегруженной системе

Теперь давайте рассмотрим, что же отобразится в отчете, если производительность приложения снижена. На следующей диаграмме приведены показатели пользователей, удаленно работающих в Microsoft Word. В этом случае производительность сервера узла сеансов удаленных рабочих столов (RDSH) ухудшается по мере того, как входит большее количество пользователей.

![Удаленный рабочий стол. Пример диаграммы производительности для сервера RDSH, на котором запущена программа Microsoft Word](./media/rds-user-input-perf-graph.png)

Вот что представляют линии на диаграмме:

- Розовая линия показывает количество сеансов, в которые выполнен вход на сервере.
- Красная линия показывает потребление ЦП.
- Зеленая линия — это максимальная задержка ввода данных пользователем во всех сеансах.
- Синяя линия (отображается как черная на этой диаграмме) представляет среднюю задержку ввода данных пользователем во всех сеансах.

Можно заметить, что присутствует взаимосвязь между пиками потребления ЦП и задержкой ввода данных пользователем: задержка ввода данных пользователем повышается по мере увеличения потребления ЦП. Кроме того, по мере добавления в систему большего количества пользователей потребление ЦП приближается к 100 %, что приводит к более частым пикам задержки ввода данных пользователем. Хотя этот счетчик очень полезен в случаях, когда серверу не хватает ресурсов, его также можно использовать для отслеживания задержки ввода данных пользователем, связанной с определенным приложением.

## <a name="configuration-options"></a>Параметры конфигурации

При использовании этого счетчика производительности следует помнить, что он сообщает задержку ввода данных пользователем через определенный интервал — 1000 мс по умолчанию. Если задать для свойства интервала выборки счетчика производительности (как показано на следующем снимке экрана) другое значение, полученное значение будет неправильным.

![Удаленный рабочий стол. Свойства для системного монитора](./media/rds-user-input-perfmon-properties.png)

Чтобы устранить эту проблему, можно задать для следующего раздела реестра нужный интервал (в миллисекундах). Например, если мы изменим значение параметра Sample every x seconds (Выполнять выборку каждые x секунд) на 5 с, то для этого раздела нужно задать значение 5000 мс.

```
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server]

"LagCounterInterval"=dword:00005000
```

> [!NOTE]
> Если вы используете Windows 10, версия 1809 или более поздняя, либо Windows Server, версия 2019 или более поздняя, не нужно задавать параметр LagCounterInterval, чтобы исправить счетчик производительности.

Мы также добавили несколько разделов, которые могут оказаться полезными, под тем же разделом реестра.

**LagCounterImageNameFirst** — задайте для этого раздела значение `DWORD 1` (значение по умолчанию (0) или раздел не существует). В результате имена счетчиков изменятся на "Имя образа <SessionID:ProcessId>". Например, "explorer <1:7964>". Это полезно, если нужно выполнить сортировку по имени образа.

**LagCounterShowUnknown** — задайте для этого раздела значение `DWORD 1` (значение по умолчанию (0) или раздел не существует). В результате будут показаны все процессы, запущенные как службы или система. Для некоторых процессов в качестве названия сеанса будет отображаться "?".

Вот что будет, если вы включите оба раздела:

![Удаленный рабочий стол. Системный монитор с обоими включенными разделами](./media/rds-user-input-delay-with-two-counters.png)

## <a name="using-the-new-counters-with-non-microsoft-tools"></a>Использование новых счетчиков со сторонними инструментами

Инструменты мониторинга могут использовать этот счетчик, как описано в руководстве [Использование счетчиков производительности](/windows/win32/perfctrs/using-performance-counters).

## <a name="download-windows-server-insider-software"></a>Скачивание программного обеспечения Windows Server для предварительной оценки

Зарегистрированные участники программы могут перейти непосредственно на [страницу загрузки ПО Windows Server для предварительной оценки](https://microsoft.com/en-us/software-download/windowsinsiderpreviewserver), чтобы получить последние файлы для загрузки программного обеспечения.  Чтобы узнать, как зарегистрироваться в качестве участника программы предварительной оценки, перейдите к разделу [Начало работы](https://insider.windows.com/en-us/for-business-getting-started-server/).

## <a name="share-your-feedback"></a>Поделитесь своим мнением

Вы можете отправить отзыв об этом компоненте через Центр отзывов. Выберите **Приложения > Все другие приложения** и добавьте"Счетчики производительности RDS — системный монитор" в заголовок публикации.

Чтобы оставить идеи касательно общих компонентов, перейдите на [страницу об RDS на сайте UserVoice](https://aka.ms/uservoice-rds).
