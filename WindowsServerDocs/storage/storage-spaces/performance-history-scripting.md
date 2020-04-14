---
title: Создание сценариев с помощью журнала производительности Локальные дисковые пространства
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 05/15/2018
ms.localizationpriority: medium
ms.openlocfilehash: 4c25ed4112035fa729ccf17792a846263ec68dfc
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856177"
---
# <a name="scripting-with-powershell-and-storage-spaces-direct-performance-history"></a>Создание сценариев с помощью PowerShell и Локальные дисковые пространства журнала производительности

> Область применения: Windows Server 2019

В Windows Server 2019 [Локальные дисковые пространства](storage-spaces-direct-overview.md) записывает и хранит подробный [Журнал производительности](performance-history.md) для виртуальных машин, серверов, дисков, томов, сетевых адаптеров и многого другого. Журнал производительности легко запрашивать и обрабатывать в PowerShell, что позволяет быстро переходить от *необработанных данных* к *фактическим ответам* на такие вопросы:

1. Были ли на прошлой неделе пики загрузки ЦП?
2. Используется ли на физическом диске ненормальная задержка?
3. Какие виртуальные машины сейчас потребляют больше всего операций ввода-вывода в хранилище?
4. Перегружена ли пропускная способность сети?
5. Когда на этом томе будет исчерпано свободное место?
6. В прошлом месяце, какие виртуальные машины использовали наибольшую память?

Командлет `Get-ClusterPerf` создан для создания сценариев. Он принимает входные данные из командлетов, например `Get-VM` или `Get-PhysicalDisk` конвейера для обработки ассоциаций, и вы можете передать его выходные данные в командлеты служебных программ, такие как `Sort-Object`, `Where-Object`и `Measure-Object`, чтобы быстро создавать эффективные запросы.

**В этом разделе приводится описание 6 примеров сценариев, которые отвечают на шесть вопросов, описанных выше.** Они представляют собой шаблоны, которые можно применять для поиска пиков, поиска средних значений, отображения линий тенденций, выполнения обнаружения выбросов и многого другого, в различных данных и временных интервалах. Они предоставляются в виде бесплатного начального кода для копирования, расширения и повторного использования.

   > [!NOTE]
   > Для краткости в примерах сценариев пропускаются такие вещи, как обработка ошибок, которые могут ожидать высококачественный код PowerShell. Они предназначены главным образом для создания идей и образования, а не для использования в рабочей среде.

## <a name="sample-1-cpu-i-see-you"></a>Пример 1. ЦП, я вижу!

В этом примере используется серия `ClusterNode.Cpu.Usage` из `LastWeek` временных интервалов для отображения максимального значения ("высокая маркировка воды"), минимальной и средней загрузки ЦП для каждого сервера в кластере. Он также выполняет простой анализ квартиль, чтобы продемонстрировать, сколько часов загруженности ЦП превышает 25%, 50% и 75% за последние 8 дней.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

На приведенном ниже снимке экрана мы видим, что на прошлой неделе *сервер-02* имел необъяснимый пик:

![Снимок экрана PowerShell](media/performance-history/Show-CpuMinMaxAvg.png)

### <a name="how-it-works"></a>Принцип работы

Выходные данные из `Get-ClusterPerf`ных каналов хорошо находятся во встроенном `Measure-Object`ном командлете, мы просто указываем свойство `Value`. С помощью `-Maximum`, `-Minimum`и `-Average`ных флагов `Measure-Object` предоставляет нам первые три столбца почти бесплатно. Чтобы выполнить анализ квартиль, можно передать `Where-Object` и подсчитать, сколько значений было `-Gt` (больше) 25, 50 или 75. Последний шаг — это беаутифи с вспомогательными функциями `Format-Hours` и `Format-Percent` — определенно необязательно.

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

## <a name="sample-2-fire-fire-latency-outlier"></a>Пример 2. пожар, пожар, задержка выбросов

В этом образце для поиска статистических выбросов, определенных как диски с почасовой задержкой, превышающей +3 σ (три стандартных отклонения) выше среднего, используется серия `PhysicalDisk.Latency.Average` из `LastHour` временных интервалов.

   > [!IMPORTANT]
   > Для краткости этот скрипт не реализует меры защиты от низкого вариативности, не обрабатывает частичные отсутствующие данные, не различает модель или встроенное по и т. д. Рекомендуется использовать только этот сценарий, чтобы определить, следует ли заменить жесткий диск. Он представлен здесь только для образовательных целей.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

На следующем снимке экрана мы видим отсутствие выбросов:

![Снимок экрана PowerShell](media/performance-history/Show-LatencyOutlierHDD.png)

### <a name="how-it-works"></a>Принцип работы

Во-первых, мы исключаем бездействующие или почти неактивные диски, проверяя, `-Gt 1`ли `PhysicalDisk.Iops.Total` согласованно. Для каждого активного жесткого диска мы параллельно используем период `LastHour`, состоящий из 360 измерений с интервалом в 10 секунд, чтобы `Measure-Object -Average` получить среднюю задержку за последний час. Это настраивает наше заполнение.

Мы реализуем [широко известную формулу](http://www.mathsisfun.com/data/standard-deviation.html) , чтобы найти среднее `μ` и стандартное отклонение `σ` Генеральной совокупности. Для каждого активного жесткого диска мы сравним среднюю задержку до среднего значения совокупности и разделите ее на стандартное отклонение. Мы храним необработанные значения, так что мы можем `Sort-Object` наши результаты, но с помощью `Format-Latency` и `Format-StandardDeviation` вспомогательных функций, чтобы беаутифи, что мы будем показывать — определенно необязательно.

Если какой-либо диск больше, чем +3 σ, мы `Write-Host` красным; в противном случае — зеленый.

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

## <a name="sample-3-noisy-neighbor-thats-write"></a>Пример 3. бесшумный сосед? Это запись!

Журнал производительности может также ответить на *right now*вопросы. Новые измерения доступны в режиме реального времени каждые 10 секунд. В этом примере используется серия `VHD.Iops.Total` из `MostRecent` временных интервалов для выяснения наиболее вероятной максимальной вероятности (например, "неспокойным") виртуальных машин, использующих большинство операций ввода-вывода в хранилище, на каждом узле в кластере, а также показана декомпозиция операций чтения и записи их действий.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

На следующем снимке экрана показаны 10 основных виртуальных машин по действиям хранилища:

![Снимок экрана PowerShell](media/performance-history/Show-TopIopsVMs.png)

### <a name="how-it-works"></a>Принцип работы

В отличие от `Get-PhysicalDisk`командлет `Get-VM` не поддерживает кластеризацию — он возвращает только виртуальные машины на локальном сервере. Чтобы выполнить запрос с каждого сервера параллельно, мы обернут наш вызов в `Invoke-Command (Get-ClusterNode).Name { ... }`. Для каждой виртуальной машины мы получаем измерения `VHD.Iops.Total`, `VHD.Iops.Read`и `VHD.Iops.Write`. Не указывая параметр `-TimeFrame`, мы получаем `MostRecent` одну точку данных для каждого из них.

   > [!TIP]
   > Эти ряды соответствуют сумме действий этой виртуальной машины со всеми файлами VHD и VHDX. Это пример, в котором для нас автоматически выполняется статистическая обработка журнала производительности. Чтобы получить декомпозицию на виртуальный жесткий диск или VHDX, можно передать отдельные `Get-VHD` в `Get-ClusterPerf`, а не на виртуальную машину.

Результаты со всех серверов поступают в виде `$Output`, которые можно `Sort-Object`, а затем `Select-Object -First 10`. Обратите внимание, что `Invoke-Command` Оформление результатов с помощью свойства `PsComputerName`, показывающего, откуда они поступили, что можно распечатать, чтобы понять, где работает виртуальная машина.

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

## <a name="sample-4-as-they-say-25-gig-is-the-new-10-gig"></a>Пример 4. как говорится, «25-ГБ — это новый 10-ГБ»

В этом примере используется серия `NetAdapter.Bandwidth.Total` из `LastDay` временных интервалов для поиска знаков насыщенности сети, определенных как > 90% теоретической максимальной пропускной способности. Для каждого сетевого адаптера в кластере он сравнивает наиболее интенсивное использование пропускной способности за последний день до указанной скорости связи.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

На следующем снимке экрана показано, что в течение последнего дня одно из следующих выгрузок: *Fabrikam NX-4 Pro #2* .

![Снимок экрана PowerShell](media/performance-history/Show-NetworkSaturation.png)

### <a name="how-it-works"></a>Принцип работы

Мы повторяем `Invoke-Command`ный прием с `Get-NetAdapter` на каждом сервере и передать `Get-ClusterPerf`. Кстати, мы получаем два соответствующих свойства: его `LinkSpeed`ную строку, например "10 Гбит/с", и ее необработанное `Speed` целое число, например 10000000000. Мы используем `Measure-Object` для получения среднего и пикового значения за последний день (напоминание: каждое измерение в `LastDay` времени представляет 5 минут) и умножается на 8 бит на байт, чтобы получить сравнение яблоки и зарядаок.

   > [!NOTE]
   > Некоторые поставщики, например Chelsio, включают действие "удаленный доступ к памяти" (RDMA) в счетчиках производительности *сетевого адаптера* , поэтому они включены в серию `NetAdapter.Bandwidth.Total`. Другие, как и Mellanox, могут не иметь. Если поставщик не имеет, просто добавьте серию `NetAdapter.Bandwidth.RDMA.Total` в вашу версию этого сценария.

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

## <a name="sample-5-make-storage-trendy-again"></a>Пример 5. Сделайте хранилище тренди еще раз!

Чтобы взглянуть на тенденции макросов, журнал производительности сохраняется в течение 1 года. В этом примере используется серия `Volume.Size.Available` из `LastYear` временных интервалов, чтобы определить частоту заполнения хранилища и оценить ее, когда она будет заполнена.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

На следующем снимке экрана показан объем *данных* , добавляемый примерно 15 ГБ в день:

![Снимок экрана PowerShell](media/performance-history/Show-StorageTrend.png)

По этой ставке его емкость будет достигнута в течение еще 42 дней.

### <a name="how-it-works"></a>Принцип работы

`LastYear` временных интервалов содержит по одной точке данных в день. Хотя для каждой линии тренда достаточно двух точек, на практике лучше потребовать больше, например 14 дней. Мы используем `Select-Object -Last 14` для настройки массива точек *(x, y)* , для *x* в диапазоне [1, 14]. С этими точками мы реализуем простой [алгоритм линейной аппроксимации по крайней мере](http://mathworld.wolfram.com/LeastSquaresFitting.html) для поиска `$A` и `$B`, которые параметризуются строку наилучшего соответствия *y = ax + b*. Добро пожаловать в верхнюю школу снова.

Деление свойства `SizeRemaining`ого тома по тенденциям (наклон `$A`) позволяет нам грубой оценить, сколько дней с текущей скоростью роста хранилища, до заполнения тома. Вспомогательные функции `Format-Bytes`, `Format-Trend`и `Format-Days`, беаутифи выходные данные.

   > [!IMPORTANT]
   > Эта оценка линейная и основана только на последних 14 ежедневных измерениях. Существуют более сложные и точные методики. Примите все усилия и не полагайтесь на этот сценарий, чтобы определить, следует ли вкладывать в хранилище расширение. Он представлен здесь только для образовательных целей.

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

## <a name="sample-6-memory-hog-you-can-run-but-you-cant-hide"></a>Пример 6. память забивает, но вы не можете скрыть

Так как журнал производительности собирается и хранится централизованно для всего кластера, не нужно объединять данные с разных компьютеров, независимо от того, сколько раз виртуальные машины перемещаются между узлами. В этом примере для указания виртуальных машин, использующих наибольшее количество памяти за последние 35 дней, используется серия `VM.Memory.Assigned` из `LastMonth` временных интервалов.

### <a name="screenshot"></a>Screenshot (Снимок экрана)

На следующем снимке экрана показаны 10 основных виртуальных машин по использованию памяти за прошлый месяц:

![Снимок экрана PowerShell](media/performance-history/Show-TopMemoryVMs.png)

### <a name="how-it-works"></a>Принцип работы

Мы повторяем наш прием `Invoke-Command`, представленный выше, для `Get-VM` на каждом сервере. Мы используем `Measure-Object -Average` для получения ежемесячного среднего значения для каждой виртуальной машины, а затем `Sort-Object`, `Select-Object -First 10` для получения нашей список лидеров. (Или, возможно, это *самый самый желаемый* список?)

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

Вот и все! Надеюсь, эти примеры вдохновить вас и помогут вам приступить к работе. С помощью Локальные дисковые пространства журнала производительности и мощного командлета `Get-ClusterPerf`, поддерживающего написание сценариев, вы получите возможность спрашивать и отвечать! — сложные вопросы по управлению и мониторингу инфраструктуры Windows Server 2019.

## <a name="see-also"></a>См. также:

- [Начало работы с Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell)
- [Обзор Локальные дисковые пространства](storage-spaces-direct-overview.md)
- [Журнал производительности](performance-history.md)
