---
title: Журнал производительности для кластеров
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: e013295364ae2951ffe8a963fb61a85d7863f5b6
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86962056"
---
# <a name="performance-history-for-clusters"></a>Журнал производительности для кластеров

> Область применения: Windows Server 2019

Этот подраздел [журнала производительности для Локальные дисковые пространства](performance-history.md) описывает журнал производительности, собранный для кластеров.

Нет рядов, исходящих на уровне кластера. Вместо этого ряды серверов, такие как `clusternode.cpu.usage` , объединяются для всех серверов в кластере. Ряды томов, такие как `volume.iops.total` , объединяются для всех томов в кластере. И ряды дисков, такие как `physicaldisk.size.total` , объединяются для всех дисков в кластере.

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте командлет [Get-Cluster](/powershell/module/failoverclusters/get-cluster) :

```PowerShell
Get-Cluster | Get-ClusterPerf
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Журнал производительности для Локальных дисковых пространств](performance-history.md)
