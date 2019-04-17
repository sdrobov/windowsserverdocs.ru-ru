---
ms.assetid: f15c02d7-1cbd-4eba-a571-0ea34ab93ef4
title: "Выполнение дедупликации данных"
ms.technology: storage-deduplication
ms.prod: windows-server-threshold
ms.topic: article
author: wmgries
manager: klaasl
ms.author: wgries
ms.date: 09/15/2016
ms.openlocfilehash: e2a84799a7478e192ee50723d5c6cb7a3f4efbf9
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="running-data-deduplication"></a>Выполнение дедупликации данных

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

## <a id="running-dedup-jobs-manually"></a>Запуск заданий дедупликации данных вручную

Каждое запланированное задание дедупликации данных можно запустить вручную следующими командлетами PowerShell:
* [`Start-DedupJob`](https://technet.microsoft.com/library/hh848442.aspx): запускает новое задание дедупликации данных.
* [`Stop-DedupJob`](https://technet.microsoft.com/library/hh848439.aspx): останавливает уже выполняющееся задание дедупликации данных (или удаляет его из очереди).
* [`Get-DedupJob`](https://technet.microsoft.com/library/hh848452.aspx): отображает все активные и ожидающие в очереди задания дедупликации данных.

При запуске задания вручную доступны все [параметры, доступные при планировании задания дедупликации данных](advanced-settings.md#modifying-job-schedules-available-settings), за исключением параметров планирования. Например, чтобы запустить вручную задание [оптимизации](understand.md#job-info-optimization) с высоким приоритетом и максимальным использованием ЦП и памяти, выполните следующую команду PowerShell с правами администратора:

```PowerShell
Start-DedupJob -Type Optimization -Volume <Your-Volume-Here> -Memory 100 -Cores 100 -Priority High
```

## <a id="monitoring-dedup"></a>Наблюдение за дедупликацией данных

### <a id="monitoring-dedup-job-successes"></a>Успешное выполнение задания

Так как дедупликация данных использует модель постобработки, важно, чтобы [задания дедупликации данных](understand.md#job-info) выполнялись успешно. Простой способ проверить состояние последнего задания— использовать командлет PowerShell [`Get-DedupStatus`](https://technet.microsoft.com/library/hh848437.aspx). Периодически проверяйте следующие поля:

* Для [задания оптимизации](understand.md#job-info-optimization) проверьте `LastOptimizationResult` (0 = Успех), `LastOptimizationResultMessage`, и `LastOptimizationTime` (должны быть указаны последние).
* Для [задания сбора мусора](understand.md#job-info-gc) проверьте `LastGarbageCollectionResult` (0 = Успех), `LastGarbageCollectionResultMessage`, и `LastGarbageCollectionTime` (должны быть указаны последние).
* Для [задания очистки целостности](understand.md#job-info-scrubbing) проверьте `LastScrubbingResult` (0 = Успех), `LastScrubbingResultMessage`, и `LastScrubbingTime` (должны быть указаны последние).

> [!Note]  
> Дополнительные сведения об успешном выполнении и невыполнении заданий можно найти в средстве просмотра событий Windows в разделе `\Applications and Services Logs\Windows\Deduplication\Operational`.

### <a id="monitoring-dedup-optimization-rates"></a>Скорости оптимизации

Одним из индикаторов сбоя при выполнении [задания оптимизации](understand.md#job-info-optimization) является снижение скорости оптимизации. Оно может означать, что задания оптимизации не могут своевременно обрабатывать все изменения или обновления. Вы можете проверить скорость оптимизации командлетом PowerShell [`Get-DedupStatus`](https://technet.microsoft.com/library/hh848437.aspx).

> [!Important]  
> `Get-DedupStatus` содержит два поля, связанных со скоростью оптимизации: `OptimizedFilesSavingsRate` и `SavingsRate`. Для отслеживания важны оба этих поля, но каждое из них имеет уникальное значение.
- `OptimizedFilesSavingsRate` применяется только к файлам, которые доступны для оптимизации (`space used by optimized files after optimization / logical size of optimized files`).
- `SavingsRate` применяется ко всему тому (`space used by optimized files after optimization / total logical size of the optimization`).

## <a id="disabling-dedup"></a>Отключение дедупликации данных
Чтобы отключить дедупликацию данных, запустите [задание отмены оптимизации](understand.md#job-info-unoptimization). Чтобы отменить оптимизацию тома, выполните следующую команду:

```PowerShell
Start-DedupJob -Type Unoptimization -Volume <Desired-Volume>
```

> [!Important]  
> Если том не имеет достаточно места для хранения неоптимизированных данных, задание отмены оптимизации завершится сбоем.

## <a id="faq"></a>Вопросы и ответы
**Существует ли какой-либо доступный пакет управления System Center Operations Manager для отслеживания дедупликации данных?**  
Да. Дедупликацию данных можно отслеживать при помощи пакета управления System Center для File Server. Дополнительные сведения см. в [руководстве по пакету управления System Center для File Server2012R2](http://download.microsoft.com/download/6/F/7/6F7A33B9-9383-48ED-9252-23C2C8AD1BDA/MPGuide_FileServer2012R2.doc).
