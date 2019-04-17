---
title: Журнал производительности для кластеров
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
Keywords: Storage Spaces Direct
ms.localizationpriority: medium
ms.openlocfilehash: 68596cbdcf8593cd3017c8ae5d0836891c78229c
ms.sourcegitcommit: 1533d994a6ddea54ac189ceb316b7d3c074307db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "1894323"
---
# <a name="performance-history-for-clusters"></a>Журнал производительности для кластеров

> Применимо к: Просмотр внутренних Windows Server

Подменю истории [производительности для хранения пробелы прямое](performance-history.md) описывается журнал производительности, собранные для кластеров.

Существует ряд, не, создаются на уровне кластера. Вместо этого сервера серии, таких как `clusternode.cpu.usage`, сводный для всех серверов в кластере. Серия тома, таких как `volume.iops.total`, сводный для всех томов в кластере. И диска ряда, таких как `physicaldisk.size.total`, сводный на всех дисках в кластере.

## <a name="usage-in-powershell"></a>Об использовании в PowerShell

Командлет [Get-кластера](https://docs.microsoft.com/powershell/module/failoverclusters/get-cluster) :

```PowerShell
Get-Cluster | Get-ClusterPerf
```

## <a name="see-also"></a>См. также

- [Журнал производительности для прямого пробелы хранилища](performance-history.md)
