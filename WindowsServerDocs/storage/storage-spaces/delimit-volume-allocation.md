---
title: Разделение размещения томов в Локальные дисковые пространства
ms.author: cosmosdarwin
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 03/29/2018
ms.openlocfilehash: faf9547833764e9075e86515d1f486a5a3f61ff8
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70872076"
---
# <a name="delimit-the-allocation-of-volumes-in-storage-spaces-direct"></a>Разделение размещения томов в Локальные дисковые пространства
> Относится к: Windows Server 2019

В Windows Server 2019 появился параметр, позволяющий вручную ограничить выделение томов в Локальные дисковые пространства. Это может значительно повысить отказоустойчивость при определенных условиях, но накладывает некоторые дополнительные рекомендации по управлению и сложность. В этом разделе объясняется, как это работает, и приводятся примеры в PowerShell.

   > [!IMPORTANT]
   > Эта функция впервые реализована в Windows Server 2019. Она недоступна в Windows Server 2016. 

## <a name="prerequisites"></a>Предварительные требования

### <a name="green-checkmark-iconmediadelimit-volume-allocationsupportedpng-consider-using-this-option-if"></a>![Зеленый значок галочки.](media/delimit-volume-allocation/supported.png) Рекомендуется использовать этот параметр, если:

- Кластер содержит шесть или более серверов; перетаскивани
- Кластер использует только [трехстороннее зеркальное отражение](storage-spaces-fault-tolerance.md#mirroring)

### <a name="red-x-iconmediadelimit-volume-allocationunsupportedpng-do-not-use-this-option-if"></a>![Красный значок X.](media/delimit-volume-allocation/unsupported.png) Не используйте этот параметр, если:

- Кластер содержит менее шести серверов; ни
- В кластере [используется устойчивость четности или](storage-spaces-fault-tolerance.md#parity) повышение [четности с ускорением отражения](storage-spaces-fault-tolerance.md#mirror-accelerated-parity)

## <a name="understand"></a>Общие сведения

### <a name="review-regular-allocation"></a>Проверка: обычное выделение

При использовании регулярного зеркального отображения том делится на несколько небольших "слоев", которые копируются три раза и равномерно распределяются по каждому диску на каждом сервере в кластере. Дополнительные сведения см. в [этом блоге глубокого](https://blogs.technet.microsoft.com/filecab/2016/11/21/deep-dive-pool-in-spaces-direct/)ознакомления.

![Схема, на которой показан объем данных, разделенный на три стопки слоев и равномерно распределенный по всем серверам.](media/delimit-volume-allocation/regular-allocation.png)

Такое выделение по умолчанию увеличивает скорость параллельных операций чтения и записи, повышает производительность и является привлекательной для простоты: каждый сервер постоянно занят, каждый диск является одинаковым, и все тома остаются в сети или переходят в автономный режим. Все тома гарантированно остаются до двух одновременных сбоев, как показано в [этих примерах](storage-spaces-fault-tolerance.md#examples) .

Однако при таком выделении тома не могут продолжать сосуществовать три одновременных сбоя. Если три сервера одновременно завершаются сбоем или если диски на трех серверах завершаются сбоем, тома становятся недоступными, так как по крайней мере некоторые слои (с очень высокой вероятностью) выделяются на все три диска или серверы, на которых произошел сбой.

В следующем примере серверы 1, 3 и 5 завершаются сбоем одновременно. Несмотря на то, что многие слои имеют неработоспособные копии, некоторые из них не:

![На схеме показаны три из шести серверов, выделенные красным цветом, а общий том — красный.](media/delimit-volume-allocation/regular-does-not-survive.png)

Том переходит в автономный режим и становится недоступен до тех пор, пока серверы не будут восстановлены.

### <a name="new-delimited-allocation"></a>Создать: выделение с разделителями

При выделении с разделителями указывается подмножество используемых серверов (минимум три для трехуровневой зеркальной копии). Том делится на слои, которые копируются три раза, как и раньше, но вместо того, чтобы распределять их по каждому серверу, **слои выделяются только на подмножество указанных серверов**.

![Схема, на которой показан том, разбитый на три стопки слоев и распределенный только на три из шести серверов.](media/delimit-volume-allocation/delimited-allocation.png)

#### <a name="advantages"></a>Преимущества

При таком выделении том, скорее всего, будет продолжать три одновременных сбоя: на самом деле его вероятность возрастает от 0% (с обычным выделением) до 95% (с выделением с разделителями) в данном случае! Интуитивно, это обусловлено тем, что не зависит от серверов 4, 5 или 6, поэтому их сбои не затрагиваются.

В примере выше серверы 1, 3 и 5 завершаются сбоем одновременно. Так как выделение с разделением гарантирует, что на сервере 2 содержится копия каждой слоя, каждая из них имеет работоспособную копию, а том остается в сети и доступен.

![На схеме показаны три из шести серверов, выделенные красным цветом, но общий том горит зеленым цветом.](media/delimit-volume-allocation/delimited-does-survive.png)

Вероятность выживания зависит от количества серверов и других факторов — дополнительные сведения см. в разделе [анализ](#analysis) .

#### <a name="disadvantages"></a>Недостатки

Выделение с разделителями накладывает некоторые дополнительные соображения и сложность управления:

1. Администратор несет ответственность за выделение каждого тома, чтобы сбалансировать использование хранилища на серверах и правилами высокую вероятность выживания, как описано [в разделе рекомендации](#best-practices) .

2. При выделении с разделителями необходимо зарезервировать эквивалент **одного диска емкости на один сервер (без максимального значения)** . Это больше, чем [опубликованная рекомендация](plan-volumes.md#choosing-the-size-of-volumes) по обычному выделению, которая снижается на четырех дисках емкости.

3. Если сервер завершается с ошибкой и нуждается в замене, как описано в разделе [Удаление сервера и его дисков](remove-servers.md#remove-a-server-and-its-drives), Администратор несет ответственность за обновление разграничения на уязвимых томах путем добавления нового сервера и удаления невыполненного сбоя, как показано ниже.

## <a name="usage-in-powershell"></a>Использование в PowerShell

`New-Volume` Командлет можно использовать для создания томов в Локальные дисковые пространства.

Например, чтобы создать обычный трехстороннее зеркальный том:

```PowerShell
New-Volume -FriendlyName "MyRegularVolume" -Size 100GB
```

### <a name="create-a-volume-and-delimit-its-allocation"></a>Создание тома и разграничение его выделения

Чтобы создать трехстороннее зеркальный том и ограничить его выделение, сделайте следующее:

1. Сначала назначьте серверы в кластере переменной `$Servers`:

    ```PowerShell
    $Servers = Get-StorageFaultDomain -Type StorageScaleUnit | Sort FriendlyName
    ```

   > [!TIP]
   > В Локальные дисковые пространства термин "единица масштабирования хранилища" относится ко всему необработанному хранилищу, подключенному к одному серверу, включая прямые подключенные диски и прямые подключенные внешние корпуса с дисками. В этом контексте это то же самое, что и Server.

2. Укажите, какие серверы следует использовать с новым `-StorageFaultDomainsToUse` параметром и путем индексирования в `$Servers`. Например, чтобы выделить выделение для первого, второго и третьего серверов (индексы 0, 1 и 2):

    ```PowerShell
    New-Volume -FriendlyName "MyVolume" -Size 100GB -StorageFaultDomainsToUse $Servers[0,1,2]
    ```

### <a name="see-a-delimited-allocation"></a>Просмотр выделения с разделителями

Чтобы увидеть, как *миволуме* выделяется, используйте `Get-VirtualDiskFootprintBySSU.ps1` сценарий в [приложении](#appendix):

```PowerShell
PS C:\> .\Get-VirtualDiskFootprintBySSU.ps1

VirtualDiskFriendlyName TotalFootprint Server1 Server2 Server3 Server4 Server5 Server6
----------------------- -------------- ------- ------- ------- ------- ------- -------
MyVolume                300 GB         100 GB  100 GB  100 GB  0       0       0      
```

Обратите внимание, что только Server1, Server2 и Server3 содержат слои *миволуме*.

### <a name="change-a-delimited-allocation"></a>Изменение выделения с разделителями

Используйте командлеты `Add-StorageFaultDomain` New `Remove-StorageFaultDomain` и для изменения того, как выделение отделяется.

Например, чтобы переместить *миволуме* на один сервер:

1. Укажите, что четвертый сервер **может** хранить слои *миволуме*:

    ```PowerShell
    Get-VirtualDisk MyVolume | Add-StorageFaultDomain -StorageFaultDomains $Servers[3]
    ```

2. Укажите, что первый сервер **не может** хранить слои *миволуме*:

    ```PowerShell
    Get-VirtualDisk MyVolume | Remove-StorageFaultDomain -StorageFaultDomains $Servers[0]
    ```

3. Перераспределите пул носителей, чтобы изменения вступили в силу:

    ```PowerShell
    Get-StoragePool S2D* | Optimize-StoragePool
    ```

![На схеме, показывающей слои, переносится EN-масса с серверов 1, 2 и 3 на серверы 2, 3 и 4.](media/delimit-volume-allocation/move.gif)

Ход выполнения перераспределения можно отслеживать с помощью `Get-StorageJob`.

По завершении убедитесь, что *миволуме* переместился, выполнив `Get-VirtualDiskFootprintBySSU.ps1` еще раз.

```PowerShell
PS C:\> .\Get-VirtualDiskFootprintBySSU.ps1

VirtualDiskFriendlyName TotalFootprint Server1 Server2 Server3 Server4 Server5 Server6
----------------------- -------------- ------- ------- ------- ------- ------- -------
MyVolume                300 GB         0       100 GB  100 GB  100 GB  0       0      
```

Обратите внимание, что Server1 не содержит слоев *миволуме* больше — вместо этого Server04.

## <a name="best-practices"></a>Рекомендации

Ниже приведены рекомендации по использованию выделения томов с разделителями.

### <a name="choose-three-servers"></a>Выберите три сервера

Разделять каждый трехстороннее зеркальный том на три сервера, а не больше.

### <a name="balance-storage"></a>Балансировка хранилища

Балансировка объема хранилища, выделенного каждому серверу, с учетом размера тома.

### <a name="every-delimited-allocation-unique"></a>Каждое выделение с разделением Unique

Чтобы повысить отказоустойчивость, сделайте выделение для каждого тома уникальным, т. е. он не использует *все* серверы совместно с другим томом (перекрытие допустимо). С N серверами есть уникальные сочетания "N выберите 3" — Вот что означает для некоторых распространенных размеров кластера:

| Число серверов (N) | Число уникальных выделений с разделителями (N выберите 3) |
|-----------------------|-----------------------------------------------------|
| 6                     | 20                                                  |
| 8                     | 56                                                  |
| 12                    | 220                                                 |
| 16                    | 560                                                 |

   > [!TIP]
   > Рассмотрим эту полезную проверку [комбинаторикс и выберите Notation (нотация](https://betterexplained.com/articles/easy-permutations-and-combinations/)).

Ниже приведен пример, в котором максимально повышается отказоустойчивость — каждый том имеет уникальное выделение с разделителями:

![уникальный — выделение](media/delimit-volume-allocation/unique-allocation.png)

И наоборот, в следующем примере первые три тома используют одинаковое выделение с разделителями (для серверов 1, 2 и 3), а последние три тома используют одинаковое выделение с разделителями (для серверов 4, 5 и 6). Это не обеспечивает максимальную отказоустойчивость: в случае сбоя трех серверов несколько томов могут перейти в автономный режим и стать недоступными одновременно.

![неуникальное выделение](media/delimit-volume-allocation/non-unique-allocation.png)

## <a name="analysis"></a>Отчет

Этот раздел является производным от математической вероятности того, что том остается в сети и доступен (или эквивалентно ожидаемой доли общего хранилища, которая остается в сети и доступна) в качестве функции числа сбоев и размера кластера.

   > [!NOTE]
   > Этот раздел является необязательным для чтения. Если вы острыйе математику, читайте здесь! Но если нет, не беспокойтесь: [Использование в PowerShell](#usage-in-powershell) и [рекомендации — все, что](#best-practices) вам нужно, чтобы успешно реализовать выделение с разделением.

### <a name="up-to-two-failures-is-always-okay"></a>До двух сбоев всегда нормально

Каждый трехстороннее зеркальный том может продолжаться до двух сбоев одновременно, как показано в [этих примерах](storage-spaces-fault-tolerance.md#examples) , независимо от их выделения. В случае сбоя двух дисков или двух серверов, или одного из них, каждый трехстороннее зеркальный том остается в сети и доступен, даже при обычном выделении.

### <a name="more-than-half-the-cluster-failing-is-never-okay"></a>Больше половины сбоя кластера никогда не происходит

И наоборот, в крайнем случае при сбое более половины серверов или дисков в кластере [кворум теряется](understand-quorum.md) , и каждый трехстороннее зеркальный том переходит в режим «вне сети» и становится недоступным, независимо от его выделения.

### <a name="what-about-in-between"></a>Что насчет?

Если три или более ошибок происходят одновременно, но по крайней мере половина половины серверов и дисков продолжают работать, тома с выделением с разделителями могут оставаться в сети и доступны в зависимости от серверов, на которых возникают сбои. Давайте запустим числа, чтобы определить точную вероятность.

Для простоты предположим, что тома являются независимо друг от друга и равномерно распределены (IID) в соответствии с рекомендациями, описанными выше, и что достаточно уникальных сочетаний, доступных для каждого выделения тома. Вероятность того, что любой заданный том остается, является также ожидаемой долей общего хранилища, которая находится в неправильном виде. 

При наличии **N** серверов, на которых у **F** возникают сбои, том, выделенный для **3** из них, переходит в режим «вне сети», если все **3** являются частью **F** со сбоями. Есть **(N выбрать f)** способы выполнения **F** -сбоев, которые **(F Choose 3)** приводят к тому, что том переходит в автономный режим и становится недоступным. Вероятность может быть выражена следующим образом:

![P_offline = Fc3/НКФ](media/delimit-volume-allocation/probability-volume-offline.png)

Во всех остальных случаях том остается в сети и доступен.

![P_online = 1 – (Fc3/НКФ)](media/delimit-volume-allocation/probability-volume-online.png)

В следующих таблицах приводится оценка вероятности для некоторых распространенных размеров кластера и до 5 сбоев, что позволяет обнаружить, что выделение с разделителями повышает отказоустойчивость по сравнению с обычным выделением в каждом из случаев.

### <a name="with-6-servers"></a>С 6 серверами

| Выделение                           | Вероятность бесперебойной работы 1 сбоя | Вероятность бесперебойной работы 2 сбоев | Вероятность бесперебойной работы 3 сбоев | Вероятность бесперебойной работы 4 сбоев | Вероятность бесперебойной работы 5 сбоев |
|--------------------------------------|------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|
| Обычный, распределенный по всем 6 серверам | 100%                               | 100%                                | 0,0                                  | 0,0                                  | 0,0                                  |
| Разделять только на 3 сервера          | 100%                               | 100%                                | 95,0%                               | 0,0                                  | 0,0                                  |

   > [!NOTE]
   > После выхода более 3 ошибок из 6 общих серверов кластер теряет кворум.

### <a name="with-8-servers"></a>С 8 серверами

| Выделение                           | Вероятность бесперебойной работы 1 сбоя | Вероятность бесперебойной работы 2 сбоев | Вероятность бесперебойной работы 3 сбоев | Вероятность бесперебойной работы 4 сбоев | Вероятность бесперебойной работы 5 сбоев |
|--------------------------------------|------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|
| Обычный, распределенный по всем 8 серверам | 100%                               | 100%                                | 0,0                                  | 0,0                                  | 0,0                                  |
| Разделять только на 3 сервера          | 100%                               | 100%                                | 98,2%                               | 94,3%                               | 0,0                                  |

   > [!NOTE]
   > После выхода более 4 ошибок из 8 серверов кластер теряет кворум.

### <a name="with-12-servers"></a>С 12 серверами

| Выделение                            | Вероятность бесперебойной работы 1 сбоя | Вероятность бесперебойной работы 2 сбоев | Вероятность бесперебойной работы 3 сбоев | Вероятность бесперебойной работы 4 сбоев | Вероятность бесперебойной работы 5 сбоев |
|---------------------------------------|------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|
| Обычный, распределенный по всем 12 серверам | 100%                               | 100%                                | 0,0                                  | 0,0                                  | 0,0                                  |
| Разделять только на 3 сервера           | 100%                               | 100%                                | 99,5%                               | 99,2%                               | 98,7%                               |

### <a name="with-16-servers"></a>С 16 серверами

| Выделение                            | Вероятность бесперебойной работы 1 сбоя | Вероятность бесперебойной работы 2 сбоев | Вероятность бесперебойной работы 3 сбоев | Вероятность бесперебойной работы 4 сбоев | Вероятность бесперебойной работы 5 сбоев |
|---------------------------------------|------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|
| Обычная, распределение по всем 16 серверам | 100%                               | 100%                                | 0,0                                  | 0,0                                  | 0,0                                  |
| Разделять только на 3 сервера           | 100%                               | 100%                                | 99,8%                               | 99,8%                               | 99,8%                               |

## <a name="frequently-asked-questions"></a>Часто задаваемые вопросы

### <a name="can-i-delimit-some-volumes-but-not-others"></a>Можно ли разделять некоторые тома, но не другие?

Да. Для каждого тома можно выбрать, следует ли разделять выделение.

### <a name="does-delimited-allocation-change-how-drive-replacement-works"></a>Ограничивается ли распределение с разделением изменением работы замены дисков?

Нет, это то же самое, что и при обычном выделении.

## <a name="see-also"></a>См. также

- [Обзор Локальные дисковые пространства](storage-spaces-direct-overview.md)
- [Отказоустойчивость в Локальные дисковые пространства](storage-spaces-fault-tolerance.md)

## <a name="appendix"></a>Приложение

Этот сценарий поможет вам увидеть, как распределяются тома.

Чтобы использовать его, как описано выше, скопируйте, вставьте и сохраните `Get-VirtualDiskFootprintBySSU.ps1`как.

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
