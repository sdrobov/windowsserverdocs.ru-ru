---
title: Пример использования пакета SDK для центра администрирования Windows — Fujitsu
description: Пример использования пакета SDK для центра администрирования Windows — Fujitsu
ms.technology: extend
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 05/23/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 9acfa873e4ce7d3e91a23abff726836f0e11ce59
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71357217"
---
# <a name="fujitsu-serverview-health-and-raid-extensions"></a>Fujitsu Сервервиев Health and RAID Extensions

## <a name="bringing-end-to-end-visibility-from-operating-system-to-hardware-into-windows-admin-center"></a>Обеспечение сквозной видимости, от операционной системы до оборудования, в центре администрирования Windows

Компания Fujitsu является ведущим учреждением для японских и коммуникационных технологий, а изготовителем серверных продуктов [примерги](http://www.fujitsu.com/fts/products/computing/servers/primergy/) и [примекуест](http://www.fujitsu.com/fts/products/computing/servers/mission-critical/) . [Пакет управления "Fujitsu сервервиев Management Suite](http://www.fujitsu.com/fts/products/computing/servers/primergy/management/) " предоставляет полный набор инструментов для управления жизненным циклом сервера, включая агент на стороне сервера, предоставляющий CIM и интерфейс PowerShell для управления оборудованием.

Компания Fujitsu обнаружила возможность легко интегрироваться с центром администрирования Windows, так как она предоставляет интерфейсы CIM и PowerShell, которые могут взаимодействовать с агентами на стороне сервера. Команда разработчиков компания Fujitsu могла легко реализовать вызовы CIM, знакомые с агентом, и визуализировать информацию в центре администрирования Windows с помощью доступных компонентов пользовательского интерфейса.

![Расширение Fujitsu — представление дерева работоспособности](../../media/extend-case-study-fujitsu/health-tree.png)

После того, как группа стала знакома с пакетом SDK для Windows Admin Center, Добавление пользовательского интерфейса для предоставления дополнительных сведений об оборудовании часто является просто еще несколькими строками кода HTML, и они быстро разворачиваются от одного средства до отображения сводного представления компонента оборудования. работоспособность, подробные представления журналов системных событий, монитор драйверов, отдельные представления для процессора, памяти, вентиляторов, источников питания, температур и напряжений, а также дополнительное средство для управления RAID. Использование элементов управления пользовательского интерфейса, доступных в пакете SDK, таких как элементы управления «дерево», «сетка» и «подробности», позволило команде быстро создавать пользовательский интерфейс, а также создавать визуальные и взаимодействующие структуры очень похожи на остальную часть центра администрирования Windows.

![Расширение Fujitsu — представление дерева RAID](../../media/extend-case-study-fujitsu/raid-tree.png)

![Расширение Fujitsu — представление томов RAID](../../media/extend-case-study-fujitsu/raid-volumes.png)

Партнерство между Fujitsu и группой Windows Admin Center ясно показывает ценность интеграции в центре администрирования Windows, позволяя клиентам получить полное представление о ролях и службах сервера, операционной системе и управлении оборудованием. .