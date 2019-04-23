---
title: Разделение выделение томов в дисковых пространств
ms.author: cosmosdarwin
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 03/29/2018
ms.openlocfilehash: c93cbf4ba418f6702cf8747508605952d993508d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889055"
---
# <a name="delimit-the-allocation-of-volumes-in-storage-spaces-direct"></a>Разделение выделение томов в дисковых пространств
> Область применения. Windows Server Insider Preview сборки 17093 и более поздние версии

Windows Server Insider Preview представлены возможность вручную разделить выделение томов в дисковых пространств. Это в, может значительно повысить устойчивость к сбоям при определенных условиях, но накладывает некоторые рекомендации по управлению добавлена и сложности. В этом разделе объясняется, как он работает и предоставляет примеры в PowerShell.

   > [!IMPORTANT]
   > Этот компонент впервые появился в Windows Server Insider Preview сборки 17093 и более поздние версии. Она недоступна в Windows Server 2016. Мы приглашаем ИТ-специалисты смогут присоединиться к [программа предварительной оценки Windows Server](https://aka.ms/serverinsider) Чтобы отправить нам отзыв, на что мы можем сделать, чтобы сделать сервер Windows лучше подходит для вашей организации.

## <a name="prerequisites"></a>предварительные требования

### <a name="green-checkmark-iconmediadelimit-volume-allocationsupportedpng-consider-using-this-option-if"></a>![Значок с зеленой галочкой.](media/delimit-volume-allocation/supported.png) Рассмотрите возможность использования этого параметра, если:

- Кластер содержит шесть или более серверов; и
- Ваш кластер использует только [трехстороннее зеркало](storage-spaces-fault-tolerance.md#mirroring) устойчивости

### <a name="red-x-iconmediadelimit-volume-allocationunsupportedpng-do-not-use-this-option-if"></a>![Значок красного значка X.](media/delimit-volume-allocation/unsupported.png) Не используйте этот параметр, если:

- Кластер содержит не более шести серверов; или
- Ваш кластер использует [четности](storage-spaces-fault-tolerance.md#parity) или [ускорением зеркальной четности](storage-spaces-fault-tolerance.md#mirror-accelerated-parity) устойчивости

## <a name="understand"></a>Общие сведения

### <a name="review-regular-allocation"></a>Для просмотра: регулярные выделения

С регулярных трехстороннего зеркалирования, том состоит из многих небольших «слоев», которые копируются в три раза и равномерно распределяться между всеми каждый диск в каждом из серверов в кластере. Дополнительные сведения см. в статье [этот блог глубокое погружение в обработку](https://blogs.technet.microsoft.com/filecab/2016/11/21/deep-dive-pool-in-spaces-direct/).

![Схема, показывающая тома разделяются на три стеки слоев и равномерно распределяться между всеми каждого сервера.](media/delimit-volume-allocation/regular-allocation.png)

Это выделение по умолчанию обеспечивает максимальную параллельного считывает и записывает, что приводит к повышения производительности и удобным в его простоте: каждый сервер занят одинаково, каждый диск заполнен одинаково и всем томам оставаться в оперативном режиме или вместе переходят в автономный режим. Каждый том будет гарантированно выдержать до двух одновременных сбоев, как [эти примеры](storage-spaces-fault-tolerance.md#examples) иллюстрации.

Тем не менее с помощью это выделение тома не могут выжить трех одновременных сбоев. Если три сервера сбоем за один раз, или если диски в трех серверов не сразу, тома становятся недоступными, так как по крайней мере некоторые слоев (с очень высокой степенью вероятности) выделенные точное трех дисков или серверов, которые не удалось.

В приведенном ниже примере серверы 1, 3 и 5 ошибкой в то же время. Несмотря на то, что многие слоев у оставшимся копий, другие — нет:

![Схема, показывающая три из шести серверов, выделены красным, а также объем — красный.](media/delimit-volume-allocation/regular-does-not-survive.png)

Том переходит в автономный режим и становится недоступным, пока не будут восстановлены серверы.

### <a name="new-delimited-allocation"></a>Новинка: с разделителями выделения

С помощью с разделителями выделения указать подмножество серверов для использования (минимальное три для трехстороннего зеркала). Том состоит из слоев, которые копируются в три раза, как и прежде, но вместо выделения на каждом сервере, **слоев выделяются только к подмножеству серверов вами**.

![Схема, показывающая тома разделены на три стеки слоев и передается только три из шести серверов.](media/delimit-volume-allocation/delimited-allocation.png)

#### <a name="advantages"></a>Преимущества

С помощью это выделение тома, вероятнее всего выжить трех одновременных сбоев: на самом деле, вероятность ее появления практические советы увеличивается от 0% (счет регулярного выделения памяти) 95% (с разделителями выделения) в этом случае! Интуитивно это обусловлено тем, не зависящий от серверов, 4, 5 или 6, поэтому не подвержены их сбоев.

В примере выше серверы, 1, 3 и 5 ошибкой в то же время. Так, как с разделителями выделения гарантировало, что этот сервер 2 содержит копию каждого перекрытия, каждый перекрытия выжившую копии, а том остается в сети и доступны:

![Схема, показывающая три из шести серверов, выделены красным, но объем имеет зеленый цвет.](media/delimit-volume-allocation/delimited-does-survive.png)

Практические советы вероятность зависит от числа серверов и других факторов — см. в разделе [Analysis](#analysis) подробные сведения.

#### <a name="disadvantages"></a>Недостатки

С разделителями выделения накладывает некоторые рекомендации по управлению добавлена и сложности:

1. Администратор отвечает за выделение выделение каждого тома, чтобы сбалансировать использование хранилища на серверы и высокая вероятность практические советы, для того, как описано в разделе [рекомендации](#best-practices) раздел.

2. С помощью с разделителями выделения зарезервировать эквивалент **емкость одного жесткого диска на сервере (без ограничений)**. Это больше, чем [опубликованных рекомендация](plan-volumes.md#choosing-the-size-of-volumes) для регулярного выделения, какие двухъядерной четыре достигнуто максимальное число дисков общее.

3. Если сервер завершается ошибкой и необходимо заменить, как описано в разделе [удалить сервер и его диски](remove-servers.md#remove-a-server-and-its-drives), администратор отвечает за обновление разграничение затронутых томах путем добавления нового сервера и удаления пример не выполненного one: ниже.

## <a name="usage-in-powershell"></a>Использование в PowerShell

Можно использовать `New-Volume` командлет для создания тома в дисковых пространств.

Например, чтобы создать том регулярных трехстороннее зеркало:

```PowerShell
New-Volume -FriendlyName "MyRegularVolume" -Size 100GB
```

### <a name="create-a-volume-and-delimit-its-allocation"></a>Создайте том и разделения его выделения

Для создания тома трехстороннее зеркало и разделения его распределения:

1. Сначала присвоить переменной серверов в кластере `$Servers`:

    ```PowerShell
    $Servers = Get-StorageFaultDomain -Type StorageScaleUnit | Sort FriendlyName
    ```

   > [!TIP]
   > В Storage Spaces Direct термин «Единицы масштабирования хранилища» относится к необработанного хранилища, подключенных к одному серверу, включая непосредственно подключенных дисков и прямого подключения внешних корпуса с дисками. В этом контексте это так же, как «сервер».

2. Указать, какие серверы для использования с новым `-StorageFaultDomainsToUse` параметр и индексирование в `$Servers`. Например, для разделения распределения первой, второй и третий серверов (индексы 0, 1 и 2):

    ```PowerShell
    New-Volume -FriendlyName "MyVolume" -Size 100GB -StorageFaultDomainsToUse $Servers[0,1,2]
    ```

### <a name="see-a-delimited-allocation"></a>См. в разделе с разделителями выделения

Чтобы увидеть как *MyVolume* является выделенной таким образом, использовать `Get-VirtualDiskFootprintBySSU.ps1` скрипта в [приложение](#appendix):

```PowerShell
PS C:\> .\Get-VirtualDiskFootprintBySSU.ps1

VirtualDiskFriendlyName TotalFootprint Server1 Server2 Server3 Server4 Server5 Server6
----------------------- -------------- ------- ------- ------- ------- ------- -------
MyVolume                300 GB         100 GB  100 GB  100 GB  0       0       0      
```

Обратите внимание, что только Server1, Server2 и Server3 содержит слоев из *MyVolume*.

### <a name="change-a-delimited-allocation"></a>Изменить выделение с разделителями

Используйте новый `Add-StorageFaultDomain` и `Remove-StorageFaultDomain` для изменения, как выделение в качестве разделителя используется.

Например, чтобы переместить *MyVolume* на одном сервере:

1. Указать, что четвертый server **можно** хранения слоев из *MyVolume*:

    ```PowerShell
    Get-VirtualDisk MyVolume | Add-StorageFaultDomain -StorageFaultDomains $Servers[3]
    ```

2. Указать, что первый сервер **невозможно** хранения слоев из *MyVolume*:

    ```PowerShell
    Get-VirtualDisk MyVolume | Remove-StorageFaultDomain -StorageFaultDomains $Servers[0]
    ```

3. Перераспределить пула носителей, чтобы изменения вступили в силу:

    ```PowerShell
    Get-StoragePool S2D* | Optimize-StoragePool
    ```

![Схема слоев миграцию скопом из серверов, 1, 2 и 3 на серверы, 2, 3 и 4.](media/delimit-volume-allocation/move.gif)

Можно отслеживать ход выполнения перераспределения с `Get-StorageJob`.

После его завершения, убедитесь, что *MyVolume* были перемещены, выполнив `Get-VirtualDiskFootprintBySSU.ps1` еще раз.

```PowerShell
PS C:\> .\Get-VirtualDiskFootprintBySSU.ps1

VirtualDiskFriendlyName TotalFootprint Server1 Server2 Server3 Server4 Server5 Server6
----------------------- -------------- ------- ------- ------- ------- ------- -------
MyVolume                300 GB         0       100 GB  100 GB  100 GB  0       0      
```

Обратите внимание, что не содержит Server1 слоев из *MyVolume* больше – а также вместо этого, выполняет Server04.

## <a name="best-practices"></a>Рекомендации

Ниже приведены рекомендации по с помощью с разделителями выделения томов.

### <a name="choose-three-servers"></a>Выберите три сервера

Разделение каждого тома трехстороннее зеркало три сервера, не более.

### <a name="balance-storage"></a>Баланс хранилища

Баланс, какой объем хранилища выделяется для каждого сервера, учитывая размер тома.

### <a name="every-delimited-allocation-unique"></a>Каждое уникальное с разделителями выделение

Для достижения максимальной отказоустойчивости, сделать выделения каждого тома уникальным, то есть она не использует *все* своих серверов с другой том (некоторые его функции пересекаются допустимо). С серверами N, имеется «N выберите 3» уникальных сочетаний — Вот что значит для некоторых распространенных размеров кластера:

| Количество серверов (N) | Количество уникальных с разделителями выделения (N выберите три варианта.) |
|-----------------------|-----------------------------------------------------|
| 6                     | 20                                                  |
| 8                     | 56                                                  |
| 12                    | 220                                                 |
| 16                    | 560                                                 |

   > [!TIP]
   > Рассмотрим этот полезные Обзор [combinatorics и выберите нотации](https://betterexplained.com/articles/easy-permutations-and-combinations/).

Ниже приведен пример, в котором повышает устойчивость к сбоям — каждый том будет иметь уникальный с разделителями распределения:

![Уникальный выделения](media/delimit-volume-allocation/unique-allocation.png)

И наоборот в следующем примере первые три тома, использовать то же самое распределение с разделителями (для серверов, 1, 2 и 3) и последние три тома, использовать то же самое распределение с разделителями (для серверов, 4, 5 и 6). Это не максимально повысить устойчивость к сбоям: при сбое трех серверов несколько томов может перейти в автономный режим и становятся недоступными, за один раз.

![Уникальный Нераспределенная](media/delimit-volume-allocation/non-unique-allocation.png)

## <a name="analysis"></a>Анализ

В этом разделе, является производным математические вероятность, что том остается в сети и доступны (или, что эквивалентно, ожидаемый долю общее хранилище, которое остается в сети и доступны) как функция количество сбоев и размера кластера.

   > [!NOTE]
   > Этот раздел является необязательным чтения. Если вы стремятся к см. в статье расчеты, читайте статью дальше. Но если это не так, не волнуйтесь: [Использование в PowerShell](#usage-in-powershell) и [рекомендации](#best-practices) необходимо успешно выполнить выделение с разделителями.

### <a name="up-to-two-failures-is-always-okay"></a>До двух сбоев допустимо всегда

Каждый том трехстороннее зеркало может выдержать до двух сбоев, в то же время, как [эти примеры](storage-spaces-fault-tolerance.md#examples) проиллюстрировать, независимо от ее выделения. Если сбой двух дисков, сбой двух серверов или один из каждого, каждый том трехстороннее зеркало остается сети и доступны, даже с помощью регулярного выделения.

### <a name="more-than-half-the-cluster-failing-is-never-okay"></a>Никогда не допустимо более половины сбоя кластера

И наоборот, в крайнем случае, что более половины серверов или дисков в кластере не сразу [кворум теряется](understand-quorum.md) и каждый том трехстороннее зеркало переходит в автономный режим и становится недоступным, независимо от ее выделения.

### <a name="what-about-in-between"></a>Как насчет между ними?

Если три или более сбоев за один раз, но по крайней мере половину серверов и диски не будут по-прежнему, томов с разделителями выделения может оставаться в сети и доступны в зависимости от того, какие серверы, у которых произошли сбои. Давайте запустим чисел, чтобы определить точное вероятность.

Для простоты предполагается тома находятся независимо друг от друга и одинаково распределенных (IID) в соответствии с рекомендациями выше и что достаточного количества уникальных сочетаний доступны для выделения каждого тома должны быть уникальными. Вероятность того, что сохранять работоспособность после любого конкретного тома также является ожидаемый доля общего хранилища, нечувствительным к линейности ожидания. 

Учитывая **N** серверов, из которых **F** сбоями, выделенных для тома **3** из них становится автономной if-and только if все **3** данныеиграютроль **F** со сбоями. Существуют **(N выберите F)** способов **F** сбои происходят, из которых **(F выберите 3)** привести том переходит в автономный режим и становится недоступным. Вероятность можно выразить следующим образом.

![P_offline = Fc3 / NcF](media/delimit-volume-allocation/probability-volume-offline.png)

Во всех остальных случаях том остается в сети и доступны:

![P_online = 1 – (Fc3 / NcF)](media/delimit-volume-allocation/probability-volume-online.png)

Следующие таблицы оценить вероятность для некоторых распространенных размеров кластера и до 5 сбоев, раскрытия, с разделителями выделения увеличивается по сравнению с регулярного выделения во всех случаях считается устойчивость к сбоям.

### <a name="with-6-servers"></a>С помощью шести серверов

| Выделение                           | Вероятность риск сбоя 1 | Вероятность риск сбоев 2 | Вероятность риск сбоев 3 | Вероятность риск сбоев 4 | Вероятность риск сбоев 5 |
|--------------------------------------|------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|
| Regular, распределены по всем серверам 6 | 100%                               | 100%                                | 0%                                  | 0%                                  | 0%                                  |
| С разделителями 3 только для серверов          | 100%                               | 100%                                | 95.0%                               | 0%                                  | 0%                                  |

   > [!NOTE]
   > После более чем трех сбоев из шести серверов общее потери кворума.

### <a name="with-8-servers"></a>С 8 серверов

| Выделение                           | Вероятность риск сбоя 1 | Вероятность риск сбоев 2 | Вероятность риск сбоев 3 | Вероятность риск сбоев 4 | Вероятность риск сбоев 5 |
|--------------------------------------|------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|
| Regular, распределены по всем серверам 8 | 100%                               | 100%                                | 0%                                  | 0%                                  | 0%                                  |
| С разделителями 3 только для серверов          | 100%                               | 100%                                | 98.2%                               | 94.3%                               | 0%                                  |

   > [!NOTE]
   > После сбоев более 4 из 8 серверов потери кворума.

### <a name="with-12-servers"></a>С 12 серверов

| Выделение                            | Вероятность риск сбоя 1 | Вероятность риск сбоев 2 | Вероятность риск сбоев 3 | Вероятность риск сбоев 4 | Вероятность риск сбоев 5 |
|---------------------------------------|------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|
| Regular, распределены по всем серверам 12 | 100%                               | 100%                                | 0%                                  | 0%                                  | 0%                                  |
| С разделителями 3 только для серверов           | 100%                               | 100%                                | 99.5%                               | 99.2%                               | 98.7%                               |

### <a name="with-16-servers"></a>С 16 серверов

| Выделение                            | Вероятность риск сбоя 1 | Вероятность риск сбоев 2 | Вероятность риск сбоев 3 | Вероятность риск сбоев 4 | Вероятность риск сбоев 5 |
|---------------------------------------|------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|
| Regular, распределены по всем серверам 16 | 100%                               | 100%                                | 0%                                  | 0%                                  | 0%                                  |
| С разделителями 3 только для серверов           | 100%                               | 100%                                | 99.8%                               | 99.8%                               | 99.8%                               |

## <a name="frequently-asked-questions"></a>Вопросы и ответы

### <a name="can-i-delimit-some-volumes-but-not-others"></a>Я легко разграничивать нескольких томов, но не другие?

Да. Вы можете тома по ли разделения выделения.

### <a name="does-delimited-allocation-change-how-drive-replacement-works"></a>С разделителями распределения изменяется как работает замены диска?

Нет, он совпадает со значением регулярного выделения.

## <a name="see-also"></a>См. также

- [Общие сведения о дисковых хранилища](storage-spaces-direct-overview.md)
- [Устойчивость к сбоям в Storage Spaces Direct](storage-spaces-fault-tolerance.md)

## <a name="appendix"></a>Приложение

Этот скрипт поможет вам см. в разделе выделением томов.

Чтобы использовать его, как описано выше, вставьте и сохраните как `Get-VirtualDiskFootprintBySSU.ps1`.

```PowerShell
Function ConvertTo-PrettyCapacity {
    Param (
        [Parameter(
            Mandatory = $True,
            ValueFromPipeline = $True
            )
        ]
    [Int64]$Bytes,
    [Int64]$RoundTo = 0
    )
    If ($Bytes -Gt 0) {
        $Base = 1024
        $Labels = ("bytes", "KB", "MB", "GB", "TB", "PB", "EB", "ZB", "YB")
        $Order = [Math]::Floor( [Math]::Log($Bytes, $Base) )
        $Rounded = [Math]::Round($Bytes/( [Math]::Pow($Base, $Order) ), $RoundTo)
        [String]($Rounded) + " " + $Labels[$Order]
    }
    Else {
        "0"
    }
    Return
}

Function Get-VirtualDiskFootprintByStorageFaultDomain {

    ################################################
    ### Step 1: Gather Configuration Information ###
    ################################################

    Write-Progress -Activity "Get-VirtualDiskFootprintByStorageFaultDomain" -CurrentOperation "Gathering configuration information..." -Status "Step 1/4" -PercentComplete 00

    $ErrorCannotGetCluster = "Cannot proceed because 'Get-Cluster' failed."
    $ErrorNotS2DEnabled = "Cannot proceed because the cluster is not running Storage Spaces Direct."
    $ErrorCannotGetClusterNode = "Cannot proceed because 'Get-ClusterNode' failed."
    $ErrorClusterNodeDown = "Cannot proceed because one or more cluster nodes is not Up."
    $ErrorCannotGetStoragePool = "Cannot proceed because 'Get-StoragePool' failed."
    $ErrorPhysicalDiskFaultDomainAwareness = "Cannot proceed because the storage pool is set to 'PhysicalDisk' fault domain awareness. This cmdlet only supports 'StorageScaleUnit', 'StorageChassis', or 'StorageRack' fault domain awareness."

    Try  {
        $GetCluster = Get-Cluster -ErrorAction Stop
    }
    Catch {
        throw $ErrorCannotGetCluster
    }

    If ($GetCluster.S2DEnabled -Ne 1) {
        throw $ErrorNotS2DEnabled
    }

    Try  {
        $GetClusterNode = Get-ClusterNode -ErrorAction Stop
    }
    Catch {
        throw $ErrorCannotGetClusterNode
    }

    If ($GetClusterNode | Where State -Ne Up) {
        throw $ErrorClusterNodeDown
    }

    Try {
        $GetStoragePool = Get-StoragePool -IsPrimordial $False -ErrorAction Stop
    }
    Catch {
        throw $ErrorCannotGetStoragePool
    }

    If ($GetStoragePool.FaultDomainAwarenessDefault -Eq "PhysicalDisk") {
        throw $ErrorPhysicalDiskFaultDomainAwareness
    }

    ###########################################################
    ### Step 2: Create SfdList[] and PhysicalDiskToSfdMap{} ###
    ###########################################################

    Write-Progress -Activity "Get-VirtualDiskFootprintByStorageFaultDomain" -CurrentOperation "Analyzing physical disk information..." -Status "Step 2/4" -PercentComplete 25

    $SfdList = Get-StorageFaultDomain -Type ($GetStoragePool.FaultDomainAwarenessDefault) | Sort FriendlyName # StorageScaleUnit, StorageChassis, or StorageRack

    $PhysicalDiskToSfdMap = @{} # Map of PhysicalDisk.UniqueId -> StorageFaultDomain.FriendlyName
    $SfdList | ForEach {
        $StorageFaultDomain = $_
        $_ | Get-StorageFaultDomain -Type PhysicalDisk | ForEach {
            $PhysicalDiskToSfdMap[$_.UniqueId] = $StorageFaultDomain.FriendlyName
        }
    }

    ##################################################################################################
    ### Step 3: Create VirtualDisk.FriendlyName -> { StorageFaultDomain.FriendlyName -> Size } Map ###
    ##################################################################################################

    Write-Progress -Activity "Get-VirtualDiskFootprintByStorageFaultDomain" -CurrentOperation "Analyzing virtual disk information..." -Status "Step 3/4" -PercentComplete 50

    $GetVirtualDisk = Get-VirtualDisk | Sort FriendlyName

    $VirtualDiskMap = @{}

    $GetVirtualDisk | ForEach {
        # Map of PhysicalDisk.UniqueId -> Size for THIS virtual disk
        $PhysicalDiskToSizeMap = @{}
        $_ | Get-PhysicalExtent | ForEach {
            $PhysicalDiskToSizeMap[$_.PhysicalDiskUniqueId] += $_.Size
        }
        # Map of StorageFaultDomain.FriendlyName -> Size for THIS virtual disk
        $SfdToSizeMap = @{}
        $PhysicalDiskToSizeMap.keys | ForEach {
            $SfdToSizeMap[$PhysicalDiskToSfdMap[$_]] += $PhysicalDiskToSizeMap[$_]
        }
        # Store
        $VirtualDiskMap[$_.FriendlyName] = $SfdToSizeMap
    }

    #########################
    ### Step 4: Write-Out ###
    #########################

    Write-Progress -Activity "Get-VirtualDiskFootprintByStorageFaultDomain" -CurrentOperation "Formatting output..." -Status "Step 4/4" -PercentComplete 75

    $Output = $GetVirtualDisk | ForEach {
        $Row = [PsCustomObject]@{}

        $VirtualDiskFriendlyName = $_.FriendlyName
        $Row | Add-Member -MemberType NoteProperty "VirtualDiskFriendlyName" $VirtualDiskFriendlyName

        $TotalFootprint = $_.FootprintOnPool | ConvertTo-PrettyCapacity
        $Row | Add-Member -MemberType NoteProperty "TotalFootprint" $TotalFootprint

        $SfdList | ForEach {
            $Size = $VirtualDiskMap[$VirtualDiskFriendlyName][$_.FriendlyName] | ConvertTo-PrettyCapacity
            $Row | Add-Member -MemberType NoteProperty $_.FriendlyName $Size
        }

        $Row
    }

    # Calculate width, in characters, required to Format-Table
    $RequiredWindowWidth = ("TotalFootprint").length + 1 + ("VirtualDiskFriendlyName").length + 1
    $SfdList | ForEach {
        $RequiredWindowWidth += $_.FriendlyName.Length + 1
    }

    $ActualWindowWidth = (Get-Host).UI.RawUI.WindowSize.Width

    If (!($ActualWindowWidth)) {
        # Cannot get window width, probably ISE, Format-List
        Write-Warning "Could not determine window width. For the best experience, use a Powershell window instead of ISE"
        $Output | Format-Table
    }
    ElseIf ($ActualWindowWidth -Lt $RequiredWindowWidth) {
        # Narrower window, Format-List
        Write-Warning "For the best experience, try making your PowerShell window at least $RequiredWindowWidth characters wide. Current width is $ActualWindowWidth characters."
        $Output | Format-List
    }
    Else {
        # Wider window, Format-Table
        $Output | Format-Table
    }
}

Get-VirtualDiskFootprintByStorageFaultDomain
```
