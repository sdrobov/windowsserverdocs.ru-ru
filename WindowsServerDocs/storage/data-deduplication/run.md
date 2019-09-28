---
ms.assetid: f15c02d7-1cbd-4eba-a571-0ea34ab93ef4
title: Выполнение дедупликации данных
ms.technology: storage-deduplication
ms.prod: windows-server
ms.topic: article
author: wmgries
manager: klaasl
ms.author: wgries
ms.date: 09/15/2016
ms.openlocfilehash: 86aff55b4c548ccf4fcbb04cc477dd63a889bebd
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403203"
---
# <a name="running-data-deduplication"></a>Выполнение дедупликации данных

> Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

## <a id="running-dedup-jobs-manually"></a>Запуск заданий дедупликации данных вручную

Каждое запланированное задание дедупликации данных можно запустить вручную следующими командлетами PowerShell:
* [`Start-DedupJob`](https://technet.microsoft.com/library/hh848442.aspx): Запуск нового задания дедупликации данных
* [`Stop-DedupJob`](https://technet.microsoft.com/library/hh848439.aspx): Останавливает уже выполняющееся задание дедупликации данных (или удаляет его из очереди)
* [`Get-DedupJob`](https://technet.microsoft.com/library/hh848452.aspx): Показывает все активные и поставленные в очередь задания дедупликации данных

При запуске задания вручную доступны все [параметры, доступные при планировании задания дедупликации данных](advanced-settings.md#modifying-job-schedules-available-settings), за исключением параметров планирования. Например, чтобы запустить вручную задание [оптимизации](understand.md#job-info-optimization) с высоким приоритетом и максимальным использованием ЦП и памяти, выполните следующую команду PowerShell с правами администратора:

```PowerShell
Start-DedupJob -Type Optimization -Volume <Your-Volume-Here> -Memory 100 -Cores 100 -Priority High
```

## <a id="monitoring-dedup"></a>Наблюдение за дедупликацией данных

### <a id="monitoring-dedup-job-successes"></a>Задание выполнено успешно

Так как дедупликация данных использует модель постобработки, важно, чтобы [задания дедупликации данных](understand.md#job-info) выполнялись успешно. Простой способ проверить состояние последнего задания — использовать командлет PowerShell [`Get-DedupStatus`](https://technet.microsoft.com/library/hh848437.aspx). Периодически проверяйте следующие поля:

* Для [задания оптимизации](understand.md#job-info-optimization) проверьте `LastOptimizationResult` (0 = Успех), `LastOptimizationResultMessage`, и `LastOptimizationTime` (должны быть указаны последние).
* Для [задания сбора мусора](understand.md#job-info-gc) проверьте `LastGarbageCollectionResult` (0 = Успех), `LastGarbageCollectionResultMessage`, и `LastGarbageCollectionTime` (должны быть указаны последние).
* Для [задания очистки целостности](understand.md#job-info-scrubbing) проверьте `LastScrubbingResult` (0 = Успех), `LastScrubbingResultMessage`, и `LastScrubbingTime` (должны быть указаны последние).

> [!Note]  
> Дополнительные сведения об успешном выполнении и невыполнении заданий можно найти в средстве просмотра событий Windows в разделе `\Applications and Services Logs\Windows\Deduplication\Operational`.

### <a id="monitoring-dedup-optimization-rates"></a>Уровни оптимизации

Одним из индикаторов сбоя при выполнении [задания оптимизации](understand.md#job-info-optimization) является снижение скорости оптимизации. Оно может означать, что задания оптимизации не могут своевременно обрабатывать все изменения или обновления. Вы можете проверить скорость оптимизации командлетом PowerShell [`Get-DedupStatus`](https://technet.microsoft.com/library/hh848437.aspx).

> [!Important]
> `Get-DedupStatus` имеет два поля, относящиеся к скорости оптимизации: `OptimizedFilesSavingsRate` и `SavingsRate`. Для отслеживания важны оба этих поля, но каждое из них имеет уникальное значение.
> - `OptimizedFilesSavingsRate` применяется только к файлам, которые находятся в политике для оптимизации (`space used by optimized files after optimization / logical size of optimized files`).
> - `SavingsRate` применяется ко всему тому (`space used by optimized files after optimization / total logical size of the optimization`).

## <a id="disabling-dedup"></a>Отключение дедупликации данных
Чтобы отключить дедупликацию данных, запустите [задание отмены оптимизации](understand.md#job-info-unoptimization). Чтобы отменить оптимизацию тома, выполните следующую команду:

```PowerShell
Start-DedupJob -Type Unoptimization -Volume <Desired-Volume>
```

> [!Important]  
> Если том не имеет достаточно места для хранения неоптимизированных данных, задание отмены оптимизации завершится сбоем.

## <a id="faq"></a>Часто задаваемые вопросы
**Доступен ли System Center Operations Manager пакет управления для мониторинга дедупликации данных?**  
Да. Дедупликацию данных можно отслеживать при помощи пакета управления System Center для File Server. Дополнительные сведения см. в [руководстве по пакету управления System Center для File Server 2012 R2](https://download.microsoft.com/download/6/F/7/6F7A33B9-9383-48ED-9252-23C2C8AD1BDA/MPGuide_FileServer2012R2.doc).
