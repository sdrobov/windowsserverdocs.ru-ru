---
ms.assetid: 5b5bab7a-727b-47ce-8efa-1d37a9639cba
title: 'Балансировка нагрузки виртуальной машины: глубокое погружение'
ms.prod: windows-server-threshold
ms.technology: storage-failover-clustering
ms.topic: article
author: bhattacharyaz
manager: eldenc
ms.author: subhatt
ms.date: 09/19/2016
ms.openlocfilehash: f90802a8e77ade0b9f282730e7cb61c73a246018
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59853425"
---
# <a name="virtual-machine-load-balancing-deep-dive"></a>Балансировка нагрузки виртуальной машины: глубокое погружение

> Относится к: Windows Server (полугодовой канал), Windows Server 2016

Windows Server 2016 обеспечивает [функцию балансировки нагрузки виртуальной машины](vm-load-balancing-overview.md) для оптимизации использования узлов в отказоустойчивом кластере. В этом документе описываются способы настройки и управления <abbr title="виртуальной машины">Виртуальная машина</abbr> Балансировка нагрузки. 

## <a id="heuristics-for-balancing"></a>Эвристический подход для балансировки
<abbr title="Виртуальной машины">Виртуальная машина</abbr> Балансировка нагрузки виртуальной машины оценивает узла нагрузкой, основываясь на следующих эвристических методов:
1. Текущий **нехватки памяти**: Память — это наиболее общие ограничения ресурсов на узле Hyper-V
2. <abbr title="Центральный процессор">ЦП</abbr> **использование** среднее значение за 5-минутное окно узла: Уменьшает узла в кластере, как стать перегруженное

## <a id="controlling-aggressiveness-of-balancing"></a>Управление интенсивность балансировки
Интенсивность балансировки на основе эвристики памяти и ЦП можно настроить на использование по общее свойство кластера «AutoBalancerLevel». Для управления Интенсивность в PowerShell выполните следующую команду:

```PowerShell
(Get-Cluster).AutoBalancerLevel = <value>
```

| AutoBalancerLevel | Интенсивность | Поведение |
|-------------------|----------------|----------|
| 1 (по умолчанию) | Низкий | Когда узел находится загружен более чем на 80% |
| 2 | Средний | Когда узел находится загружен более чем на 70% |
| 3 | Высокий | Среднее число узлов и перемещать, когда узел находится более чем на 5% выше среднего | 

![График ключевого PowerShell настройки интенсивность балансировки](media/vm-load-balancing/detailed-VM-load-balancing-1.jpg)

## <a name="controlling-abbr-titlevirtual-machinevmabbr-load-balancing"></a>Управление <abbr title="виртуальной машины">Виртуальная машина</abbr> Балансировка нагрузки
<abbr title="Виртуальной машины">Виртуальная машина</abbr> балансировки нагрузки включена по умолчанию и когда происходит Балансировка нагрузки можно настроить с общее свойство кластера «AutoBalancerMode». Для управления, когда распределение ресурсов узла сальдо кластера:

### <a name="using-failover-cluster-manager"></a>С помощью диспетчера отказоустойчивости кластеров:
1. Щелкните правой кнопкой мыши на имя кластера и выберите параметр «Свойства»  
    ![Рисунок выбора свойств для кластера с помощью диспетчера отказоустойчивости кластеров](media/vm-load-balancing/detailed-VM-load-balancing-2.jpg)

2.  Выберите на панели «Балансировщик»  
    ![Рисунок выбора параметра балансировки через диспетчер отказоустойчивости кластеров](media/vm-load-balancing/detailed-VM-load-balancing-3.jpg)

### <a name="using-powershell"></a>С помощью PowerShell.
Используйте следующую команду:
```powershell
(Get-Cluster).AutoBalancerMode = <value>
```

|AutoBalancerMode |Поведение| 
|:----------------:|:----------:|
|0| Отключено| 
|1| Балансировать нагрузку на узел соединения| 
|2 (по умолчанию)| Балансировать нагрузку на узел соединения и каждые 30 минут |

## <a name="abbr-titlevirtual-machinevmabbr-load-balancing-vs-system-center-virtual-machine-manager-dynamic-optimization"></a><abbr title="Виртуальной машины">Виртуальная машина</abbr> vs балансировки нагрузки. System Center Virtual Machine Manager динамической оптимизации
Функция распределение ресурсов узла, предоставляет готовую возможности, которые ориентирован развертываний без System Center Virtual Machine Manager (<abbr title="System Center Virtual Machine Manager">SCVMM</abbr>). <abbr title="System Center Virtual Machine Manager">SCVMM</abbr> динамической оптимизации является рекомендуемым механизмом для балансировки нагрузки виртуальной машины в кластере для <abbr title="System Center Virtual Machine Manager">SCVMM</abbr> развертываний. <abbr title="System Center Virtual Machine Manager">SCVMM</abbr> автоматически отключает Windows Server <abbr title="виртуальной машины">Виртуальная машина</abbr> балансировки нагрузки, при включении динамической оптимизации.

## <a name="see-also"></a>См. также
* [Обзор балансировки нагрузки виртуальной машины](vm-load-balancing-overview.md)
* [Отказоустойчивая кластеризация](failover-clustering-overview.md)
* [Обзор Hyper-V](../virtualization/hyper-v/Hyper-V-on-Windows-Server.md)
