---
title: Написание скриптов с помощью локальных дисковых пространств журнал производительности
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 05/15/2018
Keywords: Storage Spaces Direct
ms.localizationpriority: medium
ms.openlocfilehash: cc8ebcaaf7cc39cfadb0ebcec71ed573b436b466
ms.sourcegitcommit: 78ecb64cac789751abf9fd3f55b4a1fcbbe4dad2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2018
ms.locfileid: "8843112"
---
# Написание скриптов с помощью PowerShell и локальных дисковых пространств журнал производительности

> Область применения: 17692 и более поздних версиях сборки предварительной оценки Windows Server

В Windows Server 2019 [Локальных дисковых пространств](storage-spaces-direct-overview.md) записывает; сохраняет расширенный [Журнал производительности](performance-history.md) виртуальных машин, серверы, диски, тома, сетевых адаптеров и больше Производительность журнала простого запроса и процесс в PowerShell, чтобы быстро перейти из *необработанных данных* для *фактического ответы* на вопросы, например:

1. Происходили каких-либо пиков ЦП на прошлой неделе?
2. Любой физический диск замечены чрезмерных задержку?
3. Какие виртуальные машины потребляют ресурсы наиболее хранилища операций ввода-ВЫВОДА прямо сейчас?
4. Мои пропускную способность сети перегружена?
5. Когда этот том будет выполняться из свободного места?
6. В прошлом месяце какие виртуальные машины используется больше всего памяти?

`Get-ClusterPerf` Командлет создан для сценариев. Он принимает ввод от командлеты как `Get-VM` или `Get-PhysicalDisk` конвейером для обработки связь, а также можно передать командлет выводимыми в командлеты служебную программу как `Sort-Object`, `Where-Object`, и `Measure-Object` для быстрого составления мощные средства запросов.

**В этом разделе представлены, а также 6 примеров сценариев, которые ответьте на вопросы выше-6.** Они представляют шаблонов, которые можно применить к найти пиков, найти средние значения, построения линии тенденций, запустить выбросов обнаружения и т.д., для различных данных и сроки оплаты. Они представляют собой бесплатные начальный код для копирования, расширения и повторного использования.

   > [!NOTE]
   > Для краткости примеры сценариев опустить таких действий, как обработка ошибок, можно было ожидать кода PowerShell высокого качества. Они предназначены главным образом для вдохновения и для образовательных учреждений вместо рабочей среде.

## Пример 1: ЦП, видны вы!

В этом примере используется `ClusterNode.Cpu.Usage` серии из `LastWeek` период времени для отображения максимум (» высоким водяной знак»), минимальное и среднее значение загрузки ЦП для каждого сервера в кластере. Он также выполняет простой достигает анализ, чтобы показать, сколько часов ЦП использования был более чем 25%, 50% и 75% в течение последних 8 дней.

### Screenshot (Снимок экрана)

На следующем снимке экрана мы видим, *Server-02* было необъяснимых отклонений скачки, возникающие на прошлой неделе:

![Снимок экрана: PowerShell](media/performance-history/Show-CpuMinMaxAvg.png)

### Принцип работы

Выходные данные из `Get-ClusterPerf` каналы хорошо в встроенный `Measure-Object` командлет, мы просто укажите `Value` свойства. С его `-Maximum`, `-Minimum`, и `-Average` флагов `Measure-Object` от него мы получаем первых трех столбцов практически для бесплатной. Для анализа достигает, мы можно передавать `Where-Object` и подсчета количества значения были `-Gt` (больше) 25, 50 или 75. Последним шагом является повышает с `Format-Hours` и `Format-Percent` вспомогательные функции — определенно необязательно.

### Сценарий

Здесь приведен скрипт.

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

## Пример 2: Огня, огня, задержка выбросов

В этом примере используется `PhysicalDisk.Latency.Average` серии из `LastHour` период времени для статистического выбросов определен как диски с ежечасного превышение Средняя задержка + 3σ (три стандартных отклонения) выше среднего заполнение.

   > [!IMPORTANT]
   > Для краткости этот сценарий не реализован защиту от низкой отклонение, не обрабатывает частичный отсутствуют данные, не делает различия модели или встроенного по, и т. д. Пожалуйста соблюдать хорошо judgement и не следует полагаться на этот сценарий способом определения, следует ли заменить к жесткому диску. Он предоставляется здесь только для образовательных целей.

### Screenshot (Снимок экрана)

На следующем снимке экрана мы видим, что нет не выбросов:

![Снимок экрана: PowerShell](media/performance-history/Show-LatencyOutlierHDD.png)

### Принцип работы

Во-первых, мы простоя или почти простоя диски исключать, проверив, `PhysicalDisk.Iops.Total` постоянно `-Gt 1`. Для каждого активного жесткого диска, мы передаем его `LastHour` период времени, состоящий из 360 показателей в каждые 10 секунд, в `Measure-Object -Average` для получения его средняя задержка за последний час. Это действие настраивает участникам.

Мы реализуем необходимо найти среднее значение [Формула широко известные](http://www.mathsisfun.com/data/standard-deviation.html) `μ` и стандартное отклонение `σ` заполнения. Для каждого активного жесткого диска мы сравнить его средняя задержка для заполнения среднее и деления на стандартное отклонение. Мы сохранить необработанные значения, чтобы мы могли `Sort-Object` результаты, но использование `Format-Latency` и `Format-StandardDeviation` вспомогательные функции для повышает, что мы покажем — определенно необязательно.

Если все диски, более + 3σ, мы `Write-Host` красным; Если нет, зеленым цветом.

### Сценарий

Здесь приведен скрипт.

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

## Пример 3: Потреблением? Это записи!

Журнал производительности можно слишком ответить на вопросы о *прямо сейчас*. Новые измерения доступны в режиме реального времени, каждые 10 секунд. В этом примере используется `VHD.Iops.Total` серии из `MostRecent` для определения максимальной загрузки, (некоторые может произнести «неспокойным») к решению проблем виртуальных машин, используются наиболее хранилища операций ввода-ВЫВОДА, между всеми узлами в кластере и Показать разбивка чтение и запись их действия.

### Screenshot (Снимок экрана)

На следующем снимке экрана мы см. в разделе первые 10 виртуальных машин, действия:

![Снимок экрана: PowerShell](media/performance-history/Show-TopIopsVMs.png)

### Принцип работы

В отличие от `Get-PhysicalDisk`, `Get-VM` не кластерное командлет — он возвращает только виртуальные машины на локальном сервере. Чтобы запросить из каждого сервера параллельно, мы создаем оболочку наш вызов в `Invoke-Command (Get-ClusterNode).Name { ... }`. Для каждой виртуальной Машины, мы получаем `VHD.Iops.Total`, `VHD.Iops.Read`, и `VHD.Iops.Write` измерения. Не указывая `-TimeFrame` параметр, мы получаем `MostRecent` единая точка данных для каждого элемента.

   > [!TIP]
   > Эти серии отражают сумма действия этой Виртуальной машины для всех VHD или vhdx-файлов. Это пример, где производительность журнала автоматически объединяются для нас. Чтобы получить разбивка каждого VHD или VHDX, может передать человека `Get-VHD` в `Get-ClusterPerf` вместо виртуальной Машины.

Результаты из каждого сервера компоненты начинают работать вместе как `$Output`, который мы можем `Sort-Object` и затем `Select-Object -First 10`. Обратите внимание, что `Invoke-Command` отображающее результаты с `PsComputerName` свойство, показывающее, где они получены от, который можно напечатать знать, где запущена виртуальная машина.

### Сценарий

Здесь приведен скрипт.

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

## Пример 4: Как говорится, «25 ГБ — новый 10 ГБ»

В этом примере используется `NetAdapter.Bandwidth.Total` серии из `LastDay` определенный период времени для поиска признаки насыщенность сети, как > 90% теоретическую максимальной пропускной способности. Для каждого сетевого адаптера в кластере он сравнивает высокий наблюдаемое пропускной способности за последний день скорость указанных выше ссылку.

### Screenshot (Снимок экрана)

На следующем снимке экрана мы видим, что один *Pro 2 Fabrikam NX-4* наблюдался за последний день:

![Снимок экрана: PowerShell](media/performance-history/Show-NetworkSaturation.png)

### Принцип работы

Повторим наших `Invoke-Command` спецэффектов выше для `Get-NetAdapter` на каждом сервере и канала в `Get-ClusterPerf`. Попутно мы взять два соответствующие свойства: его `LinkSpeed` строки наподобие «10 Гбит /», а его необработанные `Speed` целое число, например 10000000000. Мы используем `Measure-Object` обеспечения среднее и пиковое последний день (напоминание: каждый показателей в `LastDay` к решению проблем представляет 5 минут) и умножить на 8 бит на каждый байт для получения яблоки яблоки сравнения.

   > [!NOTE]
   > Некоторые поставщики, например Chelsio, включить удаленное-памяти (RDMA) действия по использованию в счетчиками производительности *Сетевой адаптер* , таким образом также добавляется в `NetAdapter.Bandwidth.Total` серии. Другие, такие как Mellanox, могут не. Если поставщику не просто добавьте `NetAdapter.Bandwidth.RDMA.Total` серии в вашей версии этого сценария.

### Сценарий

Здесь приведен скрипт.

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

## Пример 5: Хранилища современным снова сделайте!

Чтобы взглянуть на тенденции макросов, производительность журнала сохраняется для до 1 год. В этом примере используется `Volume.Size.Available` серии из `LastYear` определить скорость, с которой переполнения хранилища и оценка, когда он будет полный к решению проблем.

### Screenshot (Снимок экрана)

На следующем снимке экрана мы видим, что *резервное копирование* тома — Добавление около 15 ГБ в день:

![Снимок экрана: PowerShell](media/performance-history/Show-StorageTrend.png)

В этом случае срок его емкости в другой 42 дня.

### Принцип работы

`LastYear` К решению проблем имеет одну точку данных в день. Несмотря на то, что требуется только строго двумя точками в соответствии с линия тенденции, на практике лучше требуются сведения, такие как 14 дней. Мы используем `Select-Object -Last 14` Настройка массив точки *(x, y)* , для *x* в диапазоне [1, 14]. Эти точки, мы реализуем простой [Алгоритм линейной квадратов](http://mathworld.wolfram.com/LeastSquaresFitting.html) для поиска `$A` и `$B` , параметризации строке оптимальным вариантом *y = ax + b*. Добро пожаловать в школе их снова.

Разделение тома `SizeRemaining` свойства, тенденции (наклон `$A`) позволяет нам грубой оценки сколько дней текущего со скоростью самого роста хранилища, пока на диске. `Format-Bytes`, `Format-Trend`, И `Format-Days` вспомогательные функции повышает выходных данных.

   > [!IMPORTANT]
   > Эта оценка линейной и только на основе последних 14 ежедневных измерений. Существует более сложных и точные методик. Пожалуйста соблюдать хорошо judgement и не следует полагаться на этот сценарий способом определения, следует ли приобретают разворачивания хранилища. Он предоставляется здесь только для образовательных целей.

### Сценарий

Здесь приведен скрипт.

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

## Пример 6: Расходе памяти можно запустить, но нельзя скрывать

Так как производительность журнала собранных и хранимых централизованно всего кластера, вы никогда не требуется объединить данные с разных компьютеров, независимо от того, как много раз перемещении виртуальных машин между узлами. В этом примере используется `VM.Memory.Assigned` серии из `LastMonth` период времени, чтобы идентифицировать виртуальные машины, использующие наибольший объем памяти за последние 35 дней.

### Screenshot (Снимок экрана)

На следующем снимке экрана мы см. виртуальные машины первые 10 по использованию памяти в прошлом месяце.

![Снимок экрана: PowerShell](media/performance-history/Show-TopMemoryVMs.png)

### Принцип работы

Повторим наших `Invoke-Command` сработало, вызвали ранее, до `Get-VM` на каждом сервере. Мы используем `Measure-Object -Average` для получения ежемесячных среднее значение для каждой виртуальной Машины, затем `Sort-Object` следуют `Select-Object -First 10` получить наш списка лидеров. (Или, возможно, это наш *Самый хотели* list?)

### Сценарий

Здесь приведен скрипт.

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

Вот и все! Надеемся в этих примерах учеников поможет вам приступить к работе. С помощью локальных дисковых пространств журнал производительности и мощным, сценариев поддержкой `Get-ClusterPerf` командлета возможность задавать — и отвечать! — вопросы комплексное управление отслеживая инфраструктуры Windows Server 2019.

## См. также

- [Начало работы с помощью Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell)
- [Обзор локальных дисковых пространств](storage-spaces-direct-overview.md)
- [Журнал производительности](performance-history.md)
