---
title: Создание сценариев с помощью дисковых пространств журнал производительности
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 05/15/2018
Keywords: Локальные дисковые пространства
ms.localizationpriority: medium
ms.openlocfilehash: cc8ebcaaf7cc39cfadb0ebcec71ed573b436b466
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59816325"
---
# <a name="scripting-with-powershell-and-storage-spaces-direct-performance-history"></a>Создание сценариев с помощью PowerShell и дисковые пространства журнала производительности

> Область применения. Сборки Windows Server Insider Preview 17692 и более поздние версии

В Windows Server 2019 [Storage Spaces Direct](storage-spaces-direct-overview.md) записей и обширной хранилищ [журнал производительности](performance-history.md) для виртуальных машин, серверов, диски, тома, сетевые адаптеры и многое другое. Журнал производительности легко делать запросы и процесса в PowerShell, поэтому вы можете быстро перейти из *необработанные данные* для *актуальных ответов* на следующие вопросы:

1. Возникали ли какие-либо пики ЦП на прошлой неделе?
2. Все физические диски из машин наблюдаются Чрезмерных задержек?
3. Какие виртуальные машины потребляют больше всего операций ввода-ВЫВОДА хранилища прямо сейчас?
4. Перегружена ли мои пропускной способности сети?
5. Если этот том будет хватает свободного места?
6. В прошлом месяце какие виртуальные машины использовать больше всего памяти?

`Get-ClusterPerf` Командлет предназначен для сценариев. Он принимает входные данные из командлетов, например `Get-VM` или `Get-PhysicalDisk` конвейер для обработки связи и его выходные данные можно перенаправить в командлеты служебной программы вроде `Sort-Object`, `Where-Object`, и `Measure-Object` быстро составить мощные запросы.

**В этом разделе даются и объясняется 6 примеры сценариев, ответьте на вопросы выше-6.** Они представляют шаблонов, которые можно применить к найти пики, найти средние значения, отображения линии тренда, запустите выбросов, обнаружения и многого другого для разнообразных данных и временных интервалов. Они представляют собой бесплатные начальный код можно скопировать, расширять и использовать повторно.

   > [!NOTE]
   > Для краткости в примерах скриптов опустить таких вещей, как обработка ошибок, можно ожидать высокого качества кода PowerShell. Они предназначены главным образом для вдохновения и образовательных учреждений вместо производственного использования.

## <a name="sample-1-cpu-i-see-you"></a>Пример 1. ЦП, я вижу вы!

В этом примере используется `ClusterNode.Cpu.Usage` рядами данных из `LastWeek` период времени, чтобы показать максимум («верхнего предела»), минимальное и среднее использование ЦП для каждого сервера в кластере. Он также выполняет анализ простой квартиль, чтобы показать, сколько часов ЦП использования был более чем 25%, 50%, а 75% за последние 8 дней.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

В нашем примере мы видим, что *Server-02* бы необъяснимых пик на прошлой неделе:

![Снимок экрана PowerShell](media/performance-history/Show-CpuMinMaxAvg.png)

### <a name="how-it-works"></a>Принцип работы

В результате `Get-ClusterPerf` каналы отлично во встроенную `Measure-Object` командлета, мы просто укажите `Value` свойство. С его `-Maximum`, `-Minimum`, и `-Average` флаги, `Measure-Object` дает нам первых трех столбцах почти для бесплатно. Для проведения анализа квартиль, мы можете передать в командлет `Where-Object` и подсчитать, сколько значений было `-Gt` (больше) 25, 50 или 75. Последний шаг — повышает с `Format-Hours` и `Format-Percent` вспомогательные функции – определенно необязательно.

### <a name="script"></a>Сценарий

Вот сценарий:

```
Function Format-Hours {
    Param (
        $RawValue
    )
    # Weekly timeframe has frequency 15 minutes = 4 points per hour
    [Math]::Round($RawValue/4)
}

Function Format-Percent {
    Param (
        $RawValue
    )
    [String][Math]::Round($RawValue) + " " + "%"
}

$Output = Get-ClusterNode | ForEach-Object {
    $Data = $_ | Get-ClusterPerf -ClusterNodeSeriesName "ClusterNode.Cpu.Usage" -TimeFrame "LastWeek"

    $Measure = $Data | Measure-Object -Property Value -Minimum -Maximum -Average
    $Min = $Measure.Minimum
    $Max = $Measure.Maximum
    $Avg = $Measure.Average

    [PsCustomObject]@{
        "ClusterNode"    = $_.Name
        "MinCpuObserved" = Format-Percent $Min
        "MaxCpuObserved" = Format-Percent $Max
        "AvgCpuObserved" = Format-Percent $Avg
        "HrsOver25%"     = Format-Hours ($Data | Where-Object Value -Gt 25).Length
        "HrsOver50%"     = Format-Hours ($Data | Where-Object Value -Gt 50).Length
        "HrsOver75%"     = Format-Hours ($Data | Where-Object Value -Gt 75).Length
    }
}

$Output | Sort-Object ClusterNode | Format-Table
```

## <a name="sample-2-fire-fire-latency-outlier"></a>Пример 2. Пожара, пожар, задержка выбросов

В этом примере используется `PhysicalDisk.Latency.Average` рядами данных из `LastHour` период времени, чтобы искать статистические выбросы, определенные как диски с почасовой превышает среднее время задержки + 3σ (трех стандартных отклонений) выше среднего заполнения.

   > [!IMPORTANT]
   > Для краткости этот сценарий не реализует меры предосторожности против низкая вариативность, не обрабатывает часть данных отсутствует, не различает по модели или встроенного по и т. д. Хороший judgement следует проявлять и не следует полагаться на этот скрипт отдельно, чтобы определить, следует ли заменить жесткий диск. Здесь оно выводится только в образовательных целях.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

На следующем снимке экрана мы увидим, что существует не выбросы:

![Снимок экрана PowerShell](media/performance-history/Show-LatencyOutlierHDD.png)

### <a name="how-it-works"></a>Принцип работы

Во-первых, мы исключаем простоя или почти простоя дисков, проверив, `PhysicalDisk.Iops.Total` постоянно `-Gt 1`. Для каждого активного жесткого диска, мы передаем его `LastHour` период времени, состоящая из 360 измерения в 10-секундным интервалом, на `Measure-Object -Average` для получения его среднее за последний час. Это настраивает наших заполнения.

Мы реализуем [широко известная формула](http://www.mathsisfun.com/data/standard-deviation.html) найти среднее значение `μ` и стандартное отклонение `σ` заполнения. Для каждого активного жесткого диска мы сравнить его среднее время задержки, чтобы среднее значение заполнения, а также разделить с стандартное отклонение. Мы храним необработанные значения, поэтому мы можем `Sort-Object` наши результаты, но использование `Format-Latency` и `Format-StandardDeviation` вспомогательные функции для повышает, что мы покажем – определенно необязательно.

Если любой диск является более чем + 3σ, мы `Write-Host` красным; в противном случае — зеленым цветом.

### <a name="script"></a>Сценарий

Вот сценарий:

```
Function Format-Latency {
    Param (
        $RawValue
    )
    $i = 0 ; $Labels = ("s", "ms", "μs", "ns") # Petabits, just in case!
    Do { $RawValue *= 1000 ; $i++ } While ( $RawValue -Lt 1 )
    # Return
    [String][Math]::Round($RawValue, 2) + " " + $Labels[$i]
}

Function Format-StandardDeviation {
    Param (
        $RawValue
    )
    If ($RawValue -Gt 0) {
        $Sign = "+"
    }
    Else {
        $Sign = "-"
    }
    # Return
    $Sign + [String][Math]::Round([Math]::Abs($RawValue), 2) + "σ"
}

$HDD = Get-StorageSubSystem Cluster* | Get-PhysicalDisk | Where-Object MediaType -Eq HDD

$Output = $HDD | ForEach-Object {

    $Iops = $_ | Get-ClusterPerf -PhysicalDiskSeriesName "PhysicalDisk.Iops.Total" -TimeFrame "LastHour"
    $AvgIops = ($Iops | Measure-Object -Property Value -Average).Average

    If ($AvgIops -Gt 1) { # Exclude idle or nearly idle drives

        $Latency = $_ | Get-ClusterPerf -PhysicalDiskSeriesName "PhysicalDisk.Latency.Average" -TimeFrame "LastHour"
        $AvgLatency = ($Latency | Measure-Object -Property Value -Average).Average

        [PsCustomObject]@{
            "FriendlyName"  = $_.FriendlyName
            "SerialNumber"  = $_.SerialNumber
            "MediaType"     = $_.MediaType
            "AvgLatencyPopulation" = $null # Set below
            "AvgLatencyThisHDD"    = Format-Latency $AvgLatency
            "RawAvgLatencyThisHDD" = $AvgLatency
            "Deviation"            = $null # Set below
            "RawDeviation"         = $null # Set below
        }
    }
}

If ($Output.Length -Ge 3) { # Minimum population requirement

    # Find mean μ and standard deviation σ
    $μ = ($Output | Measure-Object -Property RawAvgLatencyThisHDD -Average).Average
    $d = $Output | ForEach-Object { ($_.RawAvgLatencyThisHDD - $μ) * ($_.RawAvgLatencyThisHDD - $μ) }
    $σ = [Math]::Sqrt(($d | Measure-Object -Sum).Sum / $Output.Length)

    $FoundOutlier = $False

    $Output | ForEach-Object {
        $Deviation = ($_.RawAvgLatencyThisHDD - $μ) / $σ
        $_.AvgLatencyPopulation = Format-Latency $μ
        $_.Deviation = Format-StandardDeviation $Deviation
        $_.RawDeviation = $Deviation
        # If distribution is Normal, expect >99% within 3σ
        If ($Deviation -Gt 3) {
            $FoundOutlier = $True
        }
    }

    If ($FoundOutlier) {
        Write-Host -BackgroundColor Black -ForegroundColor Red "Oh no! There's an HDD significantly slower than the others."
    }
    Else {
        Write-Host -BackgroundColor Black -ForegroundColor Green "Good news! No outlier found."
    }

    $Output | Sort-Object RawDeviation -Descending | Format-Table FriendlyName, SerialNumber, MediaType, AvgLatencyPopulation, AvgLatencyThisHDD, Deviation

}
Else {
    Write-Warning "There aren't enough active drives to look for outliers right now."
}
```

## <a name="sample-3-noisy-neighbor-thats-write"></a>Пример 3. Шумного соседа? Это записи!

Журнал производительности можно ответить на вопросы о *прямо сейчас*, слишком. Новые измерения, доступные в режиме реального времени, каждые 10 секунд. В этом примере используется `VHD.Iops.Total` рядами данных из `MostRecent` период времени для определения максимальной нагрузкой (казалось «неспокойным») виртуальных машин, потребляющие больше всего объем операций ввода-ВЫВОДА, каждый узел в кластере и Показать разрыв чтения и записи их действие.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

На следующем снимке экрана мы увидим первые 10 виртуальных машин действием хранилища:

![Снимок экрана PowerShell](media/performance-history/Show-TopIopsVMs.png)

### <a name="how-it-works"></a>Принцип работы

В отличие от `Get-PhysicalDisk`, `Get-VM` командлет не кластерного — он возвращает только виртуальные машины на локальном сервере. Для выполнения запроса из каждого сервера в параллельном режиме, мы Подведем краткие наш вызов в `Invoke-Command (Get-ClusterNode).Name { ... }`. Для каждой виртуальной Машины, мы получаем `VHD.Iops.Total`, `VHD.Iops.Read`, и `VHD.Iops.Write` измерения. Не указывая `-TimeFrame` параметра, мы получаем `MostRecent` единой точки данных для каждого.

   > [!TIP]
   > Этих рядов отражают суммы для все его файлы VHD/VHDX действия этой виртуальной Машины. Ниже приведен пример, где журнал производительности автоматически вычисляется для нас. Чтобы получить разбиение на VHD/VHDX, можно направить отдельного `Get-VHD` в `Get-ClusterPerf` вместо виртуальной Машины.

Результаты из каждого сервера, объединяются как `$Output`, который мы можем `Sort-Object` и затем `Select-Object -First 10`. Обратите внимание, что `Invoke-Command` оформляет результаты с `PsComputerName` свойство, указывающее, откуда они поступили, который можно напечатать знать, где виртуальная машина запущена.

### <a name="script"></a>Сценарий

Вот сценарий:

```
$Output = Invoke-Command (Get-ClusterNode).Name {
    Function Format-Iops {
        Param (
            $RawValue
        )
        $i = 0 ; $Labels = (" ", "K", "M", "B", "T") # Thousands, millions, billions, trillions...
        Do { if($RawValue -Gt 1000){$RawValue /= 1000 ; $i++ } } While ( $RawValue -Gt 1000 )
        # Return
        [String][Math]::Round($RawValue) + " " + $Labels[$i]
    }

    Get-VM | ForEach-Object {
        $IopsTotal = $_ | Get-ClusterPerf -VMSeriesName "VHD.Iops.Total"
        $IopsRead  = $_ | Get-ClusterPerf -VMSeriesName "VHD.Iops.Read"
        $IopsWrite = $_ | Get-ClusterPerf -VMSeriesName "VHD.Iops.Write"
        [PsCustomObject]@{
            "VM" = $_.Name
            "IopsTotal" = Format-Iops $IopsTotal.Value
            "IopsRead"  = Format-Iops $IopsRead.Value
            "IopsWrite" = Format-Iops $IopsWrite.Value
            "RawIopsTotal" = $IopsTotal.Value # For sorting...
        }
    }
}

$Output | Sort-Object RawIopsTotal -Descending | Select-Object -First 10 | Format-Table PsComputerName, VM, IopsTotal, IopsRead, IopsWrite
```

## <a name="sample-4-as-they-say-25-gig-is-the-new-10-gig"></a>Пример 4. Как говорится, «25 ГБ — новый модулями 10»

В этом примере используется `NetAdapter.Bandwidth.Total` рядами данных из `LastDay` период времени, чтобы обращать внимание на знаки насыщенности сети определяется как > 90% от теоретической максимальной пропускной способности. Для каждого сетевого адаптера в кластере он сравнивает наибольшим использованием наблюдаемых пропускной способности в последний день скорость заявленным ссылку.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

В нашем примере мы видим, что один *Pro Fabrikam NX-4 2* наблюдался скачок в последний день:

![Снимок экрана PowerShell](media/performance-history/Show-NetworkSaturation.png)

### <a name="how-it-works"></a>Принцип работы

Мы повторяем наших `Invoke-Command` прием выше для `Get-NetAdapter` на каждом сервере и канала в `Get-ClusterPerf`. Кроме того, мы получаем два соответствующих свойства: его `LinkSpeed` строку, например «10 Гбит/с» и его необработанные `Speed` числа, такого как 10000000000. Мы используем `Measure-Object` получить среднее значение и пиковой за прошлый день (напоминание: каждый замер в `LastDay` временных рамок представляет интервал от 5 минут) и умножьте на 8 битов в байте для получения сравнения яблок требуют.

   > [!NOTE]
   > Некоторые поставщики, например Chelsio, включают действия памяти удаленного доступа (RDMA) в их *сетевой адаптер* счетчики производительности, поэтому он включен в `NetAdapter.Bandwidth.Total` рядов. Другие, такие как Mellanox, может отличаться. Если поставщик не просто добавьте `NetAdapter.Bandwidth.RDMA.Total` рядов в вашей версии этого сценария.

### <a name="script"></a>Сценарий

Вот сценарий:

```
$Output = Invoke-Command (Get-ClusterNode).Name {

    Function Format-BitsPerSec {
        Param (
            $RawValue
        )
        $i = 0 ; $Labels = ("bps", "kbps", "Mbps", "Gbps", "Tbps", "Pbps") # Petabits, just in case!
        Do { $RawValue /= 1000 ; $i++ } While ( $RawValue -Gt 1000 )
        # Return
        [String][Math]::Round($RawValue) + " " + $Labels[$i]
    }

    Get-NetAdapter | ForEach-Object {

        $Inbound = $_ | Get-ClusterPerf -NetAdapterSeriesName "NetAdapter.Bandwidth.Inbound" -TimeFrame "LastDay"
        $Outbound = $_ | Get-ClusterPerf -NetAdapterSeriesName "NetAdapter.Bandwidth.Outbound" -TimeFrame "LastDay"

        If ($Inbound -Or $Outbound) {

            $InterfaceDescription = $_.InterfaceDescription
            $LinkSpeed = $_.LinkSpeed
    
            $MeasureInbound = $Inbound | Measure-Object -Property Value -Maximum
            $MaxInbound = $MeasureInbound.Maximum * 8 # Multiply to bits/sec
    
            $MeasureOutbound = $Outbound | Measure-Object -Property Value -Maximum
            $MaxOutbound = $MeasureOutbound.Maximum * 8 # Multiply to bits/sec
    
            $Saturated = $False
    
            # Speed property is Int, e.g. 10000000000
            If (($MaxInbound -Gt (0.90 * $_.Speed)) -Or ($MaxOutbound -Gt (0.90 * $_.Speed))) {
                $Saturated = $True
                Write-Warning "In the last day, adapter '$InterfaceDescription' on server '$Env:ComputerName' exceeded 90% of its '$LinkSpeed' theoretical maximum bandwidth. In general, network saturation leads to higher latency and diminished reliability. Not good!"
            }
    
            [PsCustomObject]@{
                "NetAdapter"  = $InterfaceDescription
                "LinkSpeed"   = $LinkSpeed
                "MaxInbound"  = Format-BitsPerSec $MaxInbound
                "MaxOutbound" = Format-BitsPerSec $MaxOutbound
                "Saturated"   = $Saturated
            }
        }
    }
}

$Output | Sort-Object PsComputerName, InterfaceDescription | Format-Table PsComputerName, NetAdapter, LinkSpeed, MaxInbound, MaxOutbound, Saturated
```

## <a name="sample-5-make-storage-trendy-again"></a>Пример 5. Снова сделать современным хранилища!

Чтобы просмотреть тренды макрос, журнал производительности хранятся на 1 год. В этом примере используется `Volume.Size.Available` рядами данных из `LastYear` период времени, чтобы определить скорость, с которой идет заполнение хранилища и оценки, когда она будет заполнена.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

В нашем примере мы видим *резервного копирования* тома добавляет около 15 ГБ в день:

![Снимок экрана PowerShell](media/performance-history/Show-StorageTrend.png)

При такой скорости она достигнет вместимости другой 42 дня.

### <a name="how-it-works"></a>Принцип работы

`LastYear` Период времени содержит одну точку данных в день. Несмотря на то, что требуется только строго две точки в соответствии с линию тренда, на практике лучше требуется больше, например 14 дней. Мы используем `Select-Object -Last 14` настроить массив *(x, y)* точек, для *x* в диапазоне [1, 14]. С помощью этих точек, мы реализуем простой [алгоритма линейной метод наименьших квадратов](http://mathworld.wolfram.com/LeastSquaresFitting.html) найти `$A` и `$B` , параметризовать строку лучше всего подходит *y = ax + b*. Добро пожаловать в школе повсеместно еще раз.

Деления тома `SizeRemaining` свойства тренда (наклон `$A`) позволяет грубой оценки число дней, по текущей ставке увеличение размера хранилища, пока том заполнен. `Format-Bytes`, `Format-Trend`, И `Format-Days` вспомогательные функции повышает выходные данные.

   > [!IMPORTANT]
   > Данная оценка является линейной и только на самых последних измерениях, 14 ежедневной основе. Существуют более сложные и точные методы. Хороший judgement следует проявлять и не следует полагаться на этот сценарий, отдельно, чтобы определить, следует ли инвестировать в расширение вашего хранилища. Здесь оно выводится только в образовательных целях.

### <a name="script"></a>Сценарий

Вот сценарий:

```

Function Format-Bytes {
    Param (
        $RawValue
    )
    $i = 0 ; $Labels = ("B", "KB", "MB", "GB", "TB", "PB", "EB", "ZB", "YB")
    Do { $RawValue /= 1024 ; $i++ } While ( $RawValue -Gt 1024 )
    # Return
    [String][Math]::Round($RawValue) + " " + $Labels[$i]
}

Function Format-Trend {
    Param (
        $RawValue
    )
    If ($RawValue -Eq 0) {
        "0"
    }
    Else {
        If ($RawValue -Gt 0) {
            $Sign = "+"
        }
        Else {
            $Sign = "-"
        }
        # Return
        $Sign + $(Format-Bytes [Math]::Abs($RawValue)) + "/day"
    }
}

Function Format-Days {
    Param (
        $RawValue
    )
    [Math]::Round($RawValue)
}

$CSV = Get-Volume | Where-Object FileSystem -Like "*CSV*"

$Output = $CSV | ForEach-Object {

    $N = 14 # Require 14 days of history

    $Data = $_ | Get-ClusterPerf -VolumeSeriesName "Volume.Size.Available" -TimeFrame "LastYear" | Sort-Object Time | Select-Object -Last $N

    If ($Data.Length -Ge $N) {

        # Last N days as (x, y) points
        $PointsXY = @()
        1..$N | ForEach-Object {
            $PointsXY += [PsCustomObject]@{ "X" = $_ ; "Y" = $Data[$_-1].Value }
        }

        # Linear (y = ax + b) least squares algorithm
        $MeanX = ($PointsXY | Measure-Object -Property X -Average).Average
        $MeanY = ($PointsXY | Measure-Object -Property Y -Average).Average
        $XX = $PointsXY | ForEach-Object { $_.X * $_.X }
        $XY = $PointsXY | ForEach-Object { $_.X * $_.Y }
        $SSXX = ($XX | Measure-Object -Sum).Sum - $N * $MeanX * $MeanX
        $SSXY = ($XY | Measure-Object -Sum).Sum - $N * $MeanX * $MeanY
        $A = ($SSXY / $SSXX)
        $B = ($MeanY - $A * $MeanX)
        $RawTrend = -$A # Flip to get daily increase in Used (vs decrease in Remaining)
        $Trend = Format-Trend $RawTrend

        If ($RawTrend -Gt 0) {
            $DaysToFull = Format-Days ($_.SizeRemaining / $RawTrend)
        }
        Else {
            $DaysToFull = "-"
        }
    }
    Else {
        $Trend = "InsufficientHistory"
        $DaysToFull = "-"
    }

    [PsCustomObject]@{
        "Volume"     = $_.FileSystemLabel
        "Size"       = Format-Bytes ($_.Size)
        "Used"       = Format-Bytes ($_.Size - $_.SizeRemaining)
        "Trend"      = $Trend
        "DaysToFull" = $DaysToFull
    }
}

$Output | Format-Table
```

## <a name="sample-6-memory-hog-you-can-run-but-you-cant-hide"></a>Пример 6. Расходе памяти, можно запустить, но не спрятаться

Так как журнал производительности собираются и хранятся централизованно, для всего кластера, вы никогда не должны стыковки данных от разных компьютеров, независимо от того, как много раз виртуальные машины перемещаются, между узлами. В этом примере используется `VM.Memory.Assigned` рядами данных из `LastMonth` период времени, чтобы идентифицировать виртуальные машины, потребляющие больше всего памяти за последние 35 дней.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

В нашем примере мы видим первые 10 виртуальных машин по использованию памяти последний месяц:

![Снимок экрана PowerShell](media/performance-history/Show-TopMemoryVMs.png)

### <a name="how-it-works"></a>Принцип работы

Мы повторяем наших `Invoke-Command` прием, представленные выше, до `Get-VM` на каждом сервере. Мы используем `Measure-Object -Average` для получения ежемесячного среднее значение для каждой виртуальной Машины, затем `Sort-Object` следуют `Select-Object -First 10` для получения списка лидеров в нашей. (Или, возможно, это наши *наиболее требовалась* списка?)

### <a name="script"></a>Сценарий

Вот сценарий:

```
$Output = Invoke-Command (Get-ClusterNode).Name {
    Function Format-Bytes {
        Param (
            $RawValue
        )
        $i = 0 ; $Labels = ("B", "KB", "MB", "GB", "TB", "PB", "EB", "ZB", "YB")
        Do { if( $RawValue -Gt 1024 ){ $RawValue /= 1024 ; $i++ } } While ( $RawValue -Gt 1024 )
        # Return
        [String][Math]::Round($RawValue) + " " + $Labels[$i]
    }
    
    Get-VM | ForEach-Object {
        $Data = $_ | Get-ClusterPerf -VMSeriesName "VM.Memory.Assigned" -TimeFrame "LastMonth"
        If ($Data) {
            $AvgMemoryUsage = ($Data | Measure-Object -Property Value -Average).Average
            [PsCustomObject]@{
                "VM" = $_.Name
                "AvgMemoryUsage" = Format-Bytes $AvgMemoryUsage.Value
                "RawAvgMemoryUsage" = $AvgMemoryUsage.Value # For sorting...
            }
        }
    }
}

$Output | Sort-Object RawAvgMemoryUsage -Descending | Select-Object -First 10 | Format-Table PsComputerName, VM, AvgMemoryUsage
```

Вот и все! Будем надеяться, что в этих примерах заинтересуют поможет приступить к работе. С дисковыми пространствами журнал производительности и мощные сценарии с поддержкой `Get-ClusterPerf` командлета, вы можете задать — вопросы и получить! — комплексного вопросы, как управлять и наблюдать за инфраструктурой Windows Server 2019.

## <a name="see-also"></a>См. также

- [Приступая к работе с Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell)
- [Общие сведения о дисковых хранилища](storage-spaces-direct-overview.md)
- [Журнал производительности](performance-history.md)
