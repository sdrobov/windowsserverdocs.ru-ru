---
title: Центр администрирования Windows SDK практический пример — Fujitsu
description: Центр администрирования Windows SDK практический пример — Fujitsu
ms.technology: extend
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 05/23/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 6d916920b187dd3c637644a0f40ae9f9cca72b66
ms.sourcegitcommit: e0479b0114eac7f232e8b1e45eeede96ccd72b26
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2018
ms.locfileid: "2052378"
---
# <a name="fujitsu-serverview-health-and-raid-extensions"></a>Расширения Fujitsu ServerView работоспособности и RAID

## <a name="bringing-end-to-end-visibility-from-operating-system-to-hardware-into-windows-admin-center"></a>Перенос видимости начала до конца от операционной системы для оборудования, в центр администрирования Windows

Fujitsu — начальные сведения о японского и компании технологию обмена данными и производителю [PRIMERGY](http://www.fujitsu.com/fts/products/computing/servers/primergy/) и [PRIMEQUEST](http://www.fujitsu.com/fts/products/computing/servers/mission-critical/) серверных продуктов. [Пакет управления Fujitsu ServerView](http://www.fujitsu.com/fts/products/computing/servers/primergy/management/) предоставляет набор средств для сервера управления жизненным циклом, включая агент на сервере, который предоставляет интерфейс CIM и PowerShell для управления оборудования.

Fujitsu зафиксировала возможность легко интегрировать с помощью центра администрирования Windows, как оно указано CIM и PowerShell интерфейсы, которые могут общаться с агенты на сервере. Группа разработчиков в Fujitsu мог легко реализации CIM вызовов, которые они были знакомы с агенту и визуализации информации в пределах доступных компонентов пользовательского интерфейса с помощью центра администрирования Windows.

![Расширение Fujitsu - представления дерева работоспособности](../../media/extend-case-study-fujitsu/health-tree.png)

После группа стала знакомы с пакетом SDK центра администрирования Windows, добавление пользовательского интерфейса для предоставления сведений дополнительного оборудования зачастую был просто еще на несколько строк кода HTML, и они смогли быстро развернуть единый инструмент для отображения сводное представление аппаратный компонент работоспособности, подробные представления для системы журналы событий, драйвер монитора разделения представления для процессора, памяти, вентиляторы, источников питания, температуры и напряжения и даже дополнительные средства для управления RAID. Использование элементов управления пользовательского интерфейса в пакете SDK, такие как дерево, элементы управления области сетки и сведений о включено группы для быстрого построения пользовательского интерфейса и также достижения visual и взаимодействия разработки, очень похоже на остальных центра администрирования Windows.

![Расширение Fujitsu - представления дерева RAID](../../media/extend-case-study-fujitsu/raid-tree.png)

![Просмотр расширения Fujitsu - томов RAID](../../media/extend-case-study-fujitsu/raid-volumes.png)

Сотрудничество между Fujitsu и группой центра администрирования Windows четко показывает значение интеграции в центр администрирования Windows, включение клиенты будут иметь начала до конца понимание ролей серверов и служб, для операционной системы и управление оборудования .