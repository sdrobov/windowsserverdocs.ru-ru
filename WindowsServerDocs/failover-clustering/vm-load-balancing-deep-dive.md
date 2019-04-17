---
ms.assetid: 5b5bab7a-727b-47ce-8efa-1d37a9639cba
title: "Балансировка нагрузки виртуальной машины подробное"
ms.prod: windows-server-threshold
ms.technology: storage-failover-clustering
ms.topic: article
author: bhattacharyaz
manager: eldenc
ms.author: subhatt
ms.date: 09/19/2016
ms.openlocfilehash: 6ee092a2e51e2181a2203bc263377c4a8ec60246
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="virtual-machine-load-balancing-deep-dive"></a>Балансировка нагрузки виртуальной машины подробное

> Применяется к: Windows Server (канал точками годовой), Windows Server 2016

Windows Server 2016 предоставляет [функции балансировки нагрузки виртуальной машины](vm-load-balancing-overview.md) для оптимизации использования узлов в отказоустойчивом кластере. В этом документе описывается, как для настройки и управления <abbr title="виртуальной машины">Виртуальная машина</abbr> балансировки нагрузки. 

## <a id="heuristics-for-balancing"></a>Эвристические методы для балансировки нагрузки
<abbr title="Виртуальная машина">Виртуальная машина</abbr> балансировки нагрузки виртуальной машины оценка узла Загрузка на основе следующих эвристические методы:
1. Текущий **нехватки памяти**: память — это наиболее распространенные ограничения ресурсов на узле Hyper-V
2. <abbr title="Центральный процессор">ЦП</abbr> **использования** узла среднего окно 5-минутный: устраняет узла в кластере, становится перегруженное

## <a id="controlling-aggressiveness-of-balancing"></a>Управление интенсивности балансировки
Интенсивность балансировки основании эвристики памятью и ЦПУ можно настроить с помощью по общее свойство кластера «AutoBalancerLevel». Для управления значением интенсивности, выполните следующие действия в PowerShell:

```PowerShell
(Get-Cluster).AutoBalancerLevel = <value>
```

| AutoBalancerLevel | Интенсивность | Поведение |
|-------------------|----------------|----------|
| 1 (по умолчанию) | Низкий | Перемещать, если узел является загружен более чем на 80% |
| 2 | Средний | Перемещать, если узел является более 70% загрузки |
| 3 | Высокий | Перемещать, если узел является более 60% загрузки | 

![Рисунок, демонстрирующий PowerShell настройки интенсивности балансировки](media/vm-load-balancing/detailed-VM-load-balancing-1.jpg)

## <a name="controlling-abbr-titlevirtual-machinevmabbr-load-balancing"></a>Управление <abbr title="виртуальной машины">Виртуальная машина</abbr> балансировки нагрузки
<abbr title="Виртуальная машина">Виртуальная машина</abbr> балансировки нагрузки включена по умолчанию, и при возникновении балансировки нагрузки можно настроить, общее свойство кластера «AutoBalancerMode». Для управления Равнодоступность узла остатков кластера:

### <a name="using-failover-cluster-manager"></a>С помощью диспетчера отказоустойчивости кластеров:
1. Щелкните правой кнопкой мыши имя кластера и выберите параметр «Свойства»  
    ![Рисунок Выбор свойств для кластера с помощью диспетчера отказоустойчивости кластеров](media/vm-load-balancing/detailed-VM-load-balancing-2.jpg)

2.  Выберите на панели «Балансировки»  
    ![Изображение при выборе параметра балансировки через диспетчер отказоустойчивости кластеров](media/vm-load-balancing/detailed-VM-load-balancing-3.jpg)

### <a name="using-powershell"></a>С помощью PowerShell:
Выполните следующую команду:
```powershell
(Get-Cluster).AutoBalancerMode = <value>
```

|AutoBalancerMode |Поведение| 
|:----------------:|:----------:|
|0| Отключено| 
|1| Балансировка нагрузки на узле объединении| 
|2 (по умолчанию)| Нагрузку на присоединение к узлу и каждые 30 минут |

## <a name="abbr-titlevirtual-machinevmabbr-load-balancing-vs-system-center-virtual-machine-manager-dynamic-optimization"></a><abbr title="Виртуальная машина">Виртуальная машина</abbr> Балансировка нагрузки и System Center Virtual Machine Manager динамической оптимизации
Компонент справедливость узел предоставляет встроенные возможности, которые ориентированы на развертывания без System Center Virtual Machine Manager (<abbr title="System Center Virtual Machine Manager">SCVMM</abbr>). <abbr title="System Center Virtual Machine Manager">SCVMM</abbr> динамической оптимизации — это рекомендуемый механизм для балансировки нагрузки виртуальной машины в кластере для <abbr title="System Center Virtual Machine Manager">SCVMM</abbr> развертываний. <abbr title="System Center Virtual Machine Manager">SCVMM</abbr> автоматически отключает Windows Server <abbr title="виртуальной машины">Виртуальная машина</abbr> при включении динамической оптимизации балансировки нагрузки.

## <a name="see-also"></a>См. также:
* [Обзор балансировки нагрузки виртуальной машины](vm-load-balancing-overview.md)
* [Отказоустойчивый кластер](failover-clustering-overview.md)
* [Обзор Hyper-V](../virtualization/hyper-v/Hyper-V-on-Windows-Server.md)
