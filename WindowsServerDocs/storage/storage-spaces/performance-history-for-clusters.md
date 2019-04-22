---
title: Журнал производительности для кластеров
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
Keywords: Локальные дисковые пространства
ms.localizationpriority: medium
ms.openlocfilehash: 68596cbdcf8593cd3017c8ae5d0836891c78229c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59818775"
---
# <a name="performance-history-for-clusters"></a>Журнал производительности для кластеров

> Область применения. Сборка из программы предварительной оценки Windows Server

Этот подраздел из [журнал производительности дисковых](performance-history.md) описывает журнал производительности, собранных для кластеров.

Существует ряд не, создаются на уровне кластера. Вместо этого серия server, такие как `clusternode.cpu.usage`, объединяются для всех серверов в кластере. Серия тома, такие как `volume.iops.total`, объединяются для всех томов в кластере. И диске рядов, например `physicaldisk.size.total`, объединяются для всех дисков в кластере.

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте [Get-Cluster](https://docs.microsoft.com/powershell/module/failoverclusters/get-cluster) командлета:

```PowerShell
Get-Cluster | Get-ClusterPerf
```

## <a name="see-also"></a>См. также

- [Журнал производительности для дисковых пространств](performance-history.md)
