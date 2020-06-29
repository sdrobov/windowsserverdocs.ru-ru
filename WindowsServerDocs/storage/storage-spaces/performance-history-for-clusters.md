---
title: Журнал производительности для кластеров
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: 8ee2e85723cc2449e8cb9c42ccb7d6b761482e3a
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474871"
---
# <a name="performance-history-for-clusters"></a>Журнал производительности для кластеров

> Область применения: Windows Server 2019

Этот подраздел [журнала производительности для Локальные дисковые пространства](performance-history.md) описывает журнал производительности, собранный для кластеров.

Нет рядов, исходящих на уровне кластера. Вместо этого ряды серверов, такие как `clusternode.cpu.usage` , объединяются для всех серверов в кластере. Ряды томов, такие как `volume.iops.total` , объединяются для всех томов в кластере. И ряды дисков, такие как `physicaldisk.size.total` , объединяются для всех дисков в кластере.

## <a name="usage-in-powershell"></a>Использование в PowerShell

Используйте командлет [Get-Cluster](https://docs.microsoft.com/powershell/module/failoverclusters/get-cluster) :

```PowerShell
Get-Cluster | Get-ClusterPerf
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Журнал производительности для Локальных дисковых пространств](performance-history.md)
