---
title: Журнал производительности для кластеров
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: 7a5eec986d6e7d633f1917c599ab6fcd244c7008
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856207"
---
# <a name="performance-history-for-clusters"></a>Журнал производительности для кластеров

> Область применения: Windows Server 2019

Этот подраздел [журнала производительности для Локальные дисковые пространства](performance-history.md) описывает журнал производительности, собранный для кластеров.

Нет рядов, исходящих на уровне кластера. Вместо этого ряды серверов, например `clusternode.cpu.usage`, объединяются для всех серверов в кластере. Ряды томов, например `volume.iops.total`, объединяются для всех томов в кластере. И серии дисков, например `physicaldisk.size.total`, объединяются для всех дисков в кластере.

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте командлет [Get-Cluster](https://docs.microsoft.com/powershell/module/failoverclusters/get-cluster) :

```PowerShell
Get-Cluster | Get-ClusterPerf
```

## <a name="see-also"></a>См. также:

- [Журнал производительности для Локальные дисковые пространства](performance-history.md)
