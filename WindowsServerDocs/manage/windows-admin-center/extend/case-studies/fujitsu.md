---
title: Практический пример пакета SDK для Windows Admin Center - Fujitsu
description: Практический пример пакета SDK для Windows Admin Center - Fujitsu
ms.technology: extend
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 05/23/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 6d916920b187dd3c637644a0f40ae9f9cca72b66
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814995"
---
# <a name="fujitsu-serverview-health-and-raid-extensions"></a>Расширения Fujitsu ServerView работоспособности и RAID

## <a name="bringing-end-to-end-visibility-from-operating-system-to-hardware-into-windows-admin-center"></a>Перенос видимость end-to-end из операционной системы к оборудованию, в Windows Admin Center

Fujitsu является ведущим японский информационным и коммуникационным технологии компанией и производитель [PRIMERGY](http://www.fujitsu.com/fts/products/computing/servers/primergy/) и [PRIMEQUEST](http://www.fujitsu.com/fts/products/computing/servers/mission-critical/) серверных продуктов. [Suite управления Fujitsu ServerView](http://www.fujitsu.com/fts/products/computing/servers/primergy/management/) предоставляет исчерпывающий набор средств для сервера управления жизненным циклом, включая агент на сервере, который предоставляет интерфейс CIM и PowerShell для управления оборудованием.

Fujitsu поняли, что легко интегрировать с Windows Admin Center, как интерфейсы CIM и PowerShell, которые могут обмениваться данными с агентами на стороне сервера. Команда разработчиков в Fujitsu мог легко реализовать вызовов CIM, которые они были знакомы с агенту и визуализируйте информацию в Windows Admin Center с помощью доступных компонентов пользовательского интерфейса.

![Расширение "Fujitsu" — представление в виде дерева работоспособности](../../media/extend-case-study-fujitsu/health-tree.png)

Когда группа стала знакомы с помощью пакета SDK Windows Admin Center, добавление пользовательского интерфейса для предоставления дополнительного оборудования информации часто было просто еще на несколько строк кода HTML, и они смогли быстро развернуть с помощью единственного средства для отображения сводного представления о компонент оборудования работоспособность и подробные представления для драйвера монитора, журналов событий системы разделения представления для процессора, памяти, вентиляторы, источников питания, температуры и напряжения и даже дополнительный инструмент для управления RAID. С помощью элементов управления пользовательского интерфейса, доступные в пакете SDK, например дерево, элементы управления панели сетки и подробно включена команда для быстрого создания пользовательского интерфейса, а также повысит визуальный элемент и взаимодействие разработки, очень похожа на остальной части Windows Admin Center.

![Расширение "Fujitsu" — представление в виде дерева RAID](../../media/extend-case-study-fujitsu/raid-tree.png)

![Просмотр томов RAID Fujitsu расширение —](../../media/extend-case-study-fujitsu/raid-volumes.png)

Связь между Fujitsu и группой Windows Admin Center четко показывает значение интеграции в Windows Admin Center, что дает клиентам возможность иметь представление о end-to-end ролей сервера и службы, в операционную систему и для управления оборудованием .