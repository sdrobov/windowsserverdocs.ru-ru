---
title: Сбор диагностических данных с дисковыми пространствами
description: Основные сведения о хранилище пробелы прямой средства сбора данных, с помощью конкретные примеры того, как запустить и использовать их.
keywords: Дисковые пространства, сбор данных, устранение неполадок, каналы событий, Get-SDDCDiagnosticInfo
ms.assetid: ''
ms.prod: windows-server-threshold
ms.author: adagashe
ms.technology: storage-spaces
ms.topic: article
author: adagashe
ms.date: 10/24/2018
ms.localizationpriority: ''
ms.openlocfilehash: eaa7d92fe6f77697614cacf1405a25e5a42e14b7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59880275"
---
# <a name="collect-diagnostic-data-with-storage-spaces-direct"></a>Сбор диагностических данных с дисковыми пространствами

> Относится к: Windows Server 2019, Windows Server 2016

Существуют различные инструменты диагностики, которые могут использоваться для сбора данных, необходимые для устранения неполадок дисковых пространств и отказоустойчивого кластера. В этой статье основное внимание уделено **Get-SDDCDiagnosticInfo** -это средство одна операция сенсорного ввода, которое будет собирать все важные сведения, которые помогут вам диагностировать кластера.

<!-- The health summary report is a great start to understanding the status of your system to start diagnosing an issue. -->

Учитывая, что журналы и другие сведения, **Get SDDCDiagnosticInfo** являются плотным, сведения об устранении неполадок, представленные ниже, будет полезно для устранения неполадок Дополнительные вопросы, переданных на обработку и, возможно требуются данные для отправки в корпорацию Майкрософт для рассмотрения.

<!--
## Collecting live dumps

Windows will trigger the collection of a ``` LiveDump ``` when there are known resources that are hanging in kernel calls. ``` RHS ``` will trigger ```LiveDump``` collection if both the resource type and cluster ``` DumpPolicy ``` are set to 1. For physical disk it is set out of the box
-->

## <a name="installing-get-sddcdiagnosticinfo"></a>Installing Get-SDDCDiagnosticInfo

**Get SDDCDiagnosticInfo** командлет PowerShell (так называемые) **Get-PCStorageDiagnosticInfo**, ранее известная как **StorageHealth теста**) позволяют собирать журналы и выполнять проверки работоспособности для отказоустойчивой кластеризации (кластера, ресурсов, сети, узлы), дисковые пространства () Физические диски, вложения, виртуальные диски), кластера, Общие тома, общих файловых ресурсов SMB и дедупликации. 

Существует два способа установки скрипт, каждый из которых является описаны ниже.

### <a name="powershell-gallery"></a>Коллекции PowerShell

[Коллекции PowerShell](https://www.powershellgallery.com/packages/PrivateCloud.DiagnosticInfo) является моментальным снимком репозитория GitHub. Обратите внимание на то, что для установки элементов из коллекции PowerShell требуется последняя версия модуля PowerShellGet, который доступен в Windows 10, в Windows Management Framework (WMF) 5.0 или в установщик MSI-файл (для PowerShell 3 и 4).

Можно установить модуль, выполнив следующую команду в PowerShell с правами администратора:

``` PowerShell
Install-PackageProvider NuGet -Force
Install-Module PrivateCloud.DiagnosticInfo -Force
Import-Module PrivateCloud.DiagnosticInfo -Force
```

Чтобы обновить модуль, выполните следующую команду в PowerShell:

``` PowerShell
Update-Module PrivateCloud.DiagnosticInfo
```

### <a name="github"></a>GitHub

[Репозиторий GitHub](https://github.com/PowerShell/PrivateCloud.DiagnosticInfo/) — это самая последняя версия модуля, так как мы здесь постоянно итерации. Чтобы установить модуль из GitHub, загрузите последнюю версию модуля из [архив](https://github.com/PowerShell/PrivateCloud.DiagnosticInfo/archive/master.zip) и каталог PrivateCloud.DiagnosticInfo на правильный путь модули PowerShell, на который указывает средство для извлечения ```$env:PSModulePath```

``` PowerShell
# Allowing Tls12 and Tls11 -- e.g. github now requires Tls12
# If this is not set, the Invoke-WebRequest fails with "The request was aborted: Could not create SSL/TLS secure channel."
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$module = 'PrivateCloud.DiagnosticInfo'
Invoke-WebRequest -Uri https://github.com/PowerShell/$module/archive/master.zip -OutFile $env:TEMP\master.zip
Expand-Archive -Path $env:TEMP\master.zip -DestinationPath $env:TEMP -Force
if (Test-Path $env:SystemRoot\System32\WindowsPowerShell\v1.0\Modules\$module) {
    rm -Recurse $env:SystemRoot\System32\WindowsPowerShell\v1.0\Modules\$module -ErrorAction Stop
    Remove-Module $module -ErrorAction SilentlyContinue
} else {
    Import-Module $module -ErrorAction SilentlyContinue
} 
if (-not ($m = Get-Module $module -ErrorAction SilentlyContinue)) {
    $md = "$env:ProgramFiles\WindowsPowerShell\Modules"
} else {
    $md = (gi $m.ModuleBase -ErrorAction SilentlyContinue).PsParentPath
    Remove-Module $module -ErrorAction SilentlyContinue
    rm -Recurse $m.ModuleBase -ErrorAction Stop
}
cp -Recurse $env:TEMP\$module-master\$module $md -Force -ErrorAction Stop
rm -Recurse $env:TEMP\$module-master,$env:TEMP\master.zip
Import-Module $module -Force

``` 

Если вам нужно получить этот модуль в кластере в автономном режиме, загрузите ZIP-файл, переместите его целевым узлом сервера и установить модуль.

## <a name="gathering-logs"></a>Идет сбор журналов

После включения каналы событий и завершить процесс установки, можно использовать командлет Get-SDDCDiagnosticInfo PowerShell в модуле для получения:

- Отчеты о работоспособности хранилища, а также сведения о неработоспособных компонентов
- Отчеты о емкости пула, тома и дедуплицированного тома
- Журналы событий всех узлов кластера и отчета об ошибках сводки

Предположим, что кластер хранилища содержит имя *«CLUS01».*

Выполнять в отношении удаленного хранилища кластера:

``` PowerShell
Get-SDDCDiagnosticInfo -ClusterName CLUS01
```

Чтобы выполнить локально на узле кластерного хранилища:

``` PowerShell
Get-SDDCDiagnosticInfo
```

Чтобы сохранить результаты в указанную папку:

``` PowerShell
Get-SDDCDiagnosticInfo -WriteToPath D:\Folder 
```

Ниже приведен пример того, как это выглядит в реальном кластере:

``` PowerShell
New-Item -Name SDDCDiagTemp -Path d:\ -ItemType Directory -Force
Get-SddcDiagnosticInfo -ClusterName S2D-Cluster -WriteToPath d:\SDDCDiagTemp
```

Как вы видите, сценарий также будут выполнять проверку текущего состояния кластера

![Снимок экрана powershell коллекции данных](media/data-collection/CollectData.png)

Как вы видите, все данные записываются в папку SDDCDiagTemp

![Снимок экрана обозревателя файла данных](media/data-collection/CollectDataFolder.png)

После завершения сценария будет она создаст ZIP в каталоге пользователей

![ZIP-файлу данных снимок экрана powershell](media/data-collection/CollectDataResult.png)

Создайте отчет в текстовый файл

```PowerShell
#find the latest diagnostic zip in UserProfile
    $DiagZip=(get-childitem $env:USERPROFILE | where Name -like HealthTest*.zip)
    $LatestDiagPath=($DiagZip | sort lastwritetime | select -First 1).FullName
#expand to temp directory
    New-Item -Name SDDCDiagTemp -Path d:\ -ItemType Directory -Force
    Expand-Archive -Path $LatestDiagPath -DestinationPath D:\SDDCDiagTemp -Force
#generate report and save to text file
    $report=Show-SddcDiagnosticReport -Path D:\SDDCDiagTemp
    $report | out-file d:\SDDCReport.txt
    
```

Для справки ниже приведен ссылку [образец отчета](https://github.com/Microsoft/WSLab/blob/dev/Scenarios/S2D%20Tools/Get-SDDCDiagnosticInfo/SDDCReport.txt) и [пример zip](https://github.com/Microsoft/WSLab/blob/dev/Scenarios/S2D%20Tools/Get-SDDCDiagnosticInfo/HealthTest-S2D-Cluster-20180522-1546.ZIP).

Чтобы увидеть это в Windows Admin Center (и более поздних версий в версии 1812), перейдите к *диагностики* вкладки. Как видно на следующем снимке экрана, вы можете 

- Установка средства диагностики
- Обновить их (если они устарели), 
- Планирование ежедневного запуска диагностики (они имеют минимальной степени влияет на систему, как правило, принимают < 5 минут в фоновом режиме и не более 500 МБ в кластере)
- Представление собранные диагностические сведения ранее в том случае, если вам нужно предоставить его для поддержки или проанализировать информацию самостоятельно.

![Снимок экрана диагностики WAC](media/data-collection/Wac.png)

## <a name="get-sddcdiagnosticinfo-output"></a>Выходные данные Get-SDDCDiagnosticInfo

Ниже приведены файлы, включенные в ZIP-выходные данные Get-SDDCDiagnosticInfo.

### <a name="health-summary-report"></a>Сводный отчет о работоспособности

Сводный отчет о работоспособности будет сохранен как:
- 0_CloudHealthSummary.log

Этот файл создается после синтаксического анализа все данные собираются и целью является предоставление краткую сводку системы. Этот пакет содержит:

- Сведения о системе
- Общие сведения о работоспособности хранилища (число узлов до ресурсы сети, Общие тома кластера через Интернет, неработоспособных компонентов, и т.д.)
- Сведения о неработоспособных компонентов (ресурсы кластера, которые отключены, неудачных или Ожидание в сети)
- Сведения о встроенного по и драйверов
- Пул, физический диск и сведения о томе
- Производительность хранилища (собираются данные счетчиков производительности)

В этом отчете постоянно обновляются для включения больше полезной информации. Последние сведения см. в разделе [файл сведений GitHub](https://github.com/PowerShell/PrivateCloud.DiagnosticInfo/edit/master/README.md).

### <a name="logs-and-xml-files"></a>XML-файлы и журналы

Скрипт выполняется различных журналов, сбор скрипты и сохраняет результат в виде XML-файлов. Мы собираем журналы кластера и работоспособности, сведения о системе (MSInfo32), нефильтрованные журналы событий (отказоустойчивой кластеризации, dis диагностики, hyper-v, дисковых пространств и многое другое) и хранения диагностической информации (операционные журналы). Последние сведения о собираемой информации, см. в разделе [файл сведений GitHub (что мы собираем)](https://github.com/PowerShell/PrivateCloud.DiagnosticInfo/blob/master/README.md#what-does-the-cmdlet-output-include).

<!--
## Enabling event channels

When Windows Server is installed, many event channels are enabled by default. But sometimes when diagnosing an issue, we want to be able to enable some of these event channels since it will help in triaging and diagnosing system issues.

You could enable additional event channels on each server node in your cluster as needed; however, this approach presents two problems:

1. You need to remember to enable the same event channels on every new server node that you add to your cluster.
2. When diagnosing, it can be tedious to enable specific event channels, reproduce the error, and repeat this process until you root cause.

To avoid these issues, you can enable event channels on cluster startup. The list of enabled event channels on your cluster can be configured using the public property **EnabledEventLogs**. By default, the following event channels are enabled:

```powershell
PS C:\Windows\system32> (get-cluster).EnabledEventLogs
```

Here's an example of the output:
```
Microsoft-Windows-Hyper-V-VmSwitch-Diagnostic,4,0xFFFFFFFD
Microsoft-Windows-SMBDirect/Debug,4
Microsoft-Windows-SMBServer/Analytic
Microsoft-Windows-Kernel-LiveDump/Analytic
```

The **EnabledEventLogs** property is a multistring, where each string is in the form: **channel-name, log-level, keyword-mask**. The **keyword-mask** can be a hexadecimal (prefix 0x), octal (prefix 0), or decimal number (no prefix) number that each event contains (so you can filter by it). For instance, to add a new event channel to the list and to configure both **log-level** and **keyword-mask** you can run:

```powershell
(get-cluster).EnabledEventLogs += "Microsoft-Windows-WinINet/Analytic,2,321"
```

If you want to set the **log-level** but keep the **keyword-mask** at its default value, you can use either of the following commands:

```powershell
(get-cluster).EnabledEventLogs += "Microsoft-Windows-WinINet/Analytic,2"
(get-cluster).EnabledEventLogs += "Microsoft-Windows-WinINet/Analytic,2,"
```

If you want to keep the **log-level** at its default value, but set the **keyword-mask** you can run the following command:

```powershell
(get-cluster).EnabledEventLogs += "Microsoft-Windows-WinINet/Analytic,,0xf1"
```

If you want to keep both the **log-level** and the **keyword-mask** at their default values, you can run any of the following commands:

```powershell
(get-cluster).EnabledEventLogs += "Microsoft-Windows-WinINet/Analytic"
(get-cluster).EnabledEventLogs += "Microsoft-Windows-WinINet/Analytic,"
(get-cluster).EnabledEventLogs += "Microsoft-Windows-WinINet/Analytic,,"
```

These event channels will be enabled on every cluster node when the cluster service starts or whenever the **EnabledEventLogs** property is changed.
-->

## <a name="how-to-consume-the-xml-files-from-get-pcstoragediagnosticinfo"></a>Как использовать XML-файлы из Get-PCStorageDiagnosticInfo
Вы можете использовать данные из XML-файлов, в данных, собираемых **Get PCStorageDiagnosticInfo** командлета. Эти файлы имеют сведения о виртуальных дисков, физические диски, базовый кластер сведения и другие PowerShell связанные выходные данные. 

Чтобы просмотреть результаты этих выходных данных, откройте окно PowerShell и выполните следующие действия. 

```PowerShell
ipmo storage
$d = import-clixml <filename> 
$d
```

## <a name="what-to-expect-next"></a>Что будет дальше?
Много усовершенствования и новые командлеты для анализа работоспособности системы SDDC.
Отправить отзыв о вы хотите см. в разделе, подав заявку проблемы [здесь](https://github.com/PowerShell/PrivateCloud.DiagnosticInfo/issues). Кроме того, вы можете отправить полезные изменения в сценарий, отправляя [запрос на Вытягивание](https://github.com/PowerShell/PrivateCloud.DiagnosticInfo/pulls).
