---
title: Dfsutil
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef5093a4-0d24-4b21-9d04-59933ad98e2c
robots: noindex,nofollow
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1a06806b109bbd324213f935892bbbab415362df
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377976"
---
# <a name="dfsutil"></a>Dfsutil

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Команда Dfsutil управляет пространствами имен DFS, серверами и клиентами. команды Dfsutil используют исходную терминологию распределенная файловая система с обновленными терминологиями пространств имен DFS, предоставленными в качестве объяснения для большинства команд.

Примеры использования этой команды см. в разделе. 

## <a name="syntax"></a>Синтаксис

```
command </parameter> </param2>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|[Dfsutil root](dfsutil-root.md)|Отображает, создает, удаляет, импортирует и экспортирует корни пространства имен.|
|[Dfsutil Link](dfsutil-link.md)|Отображает, создает, удаляет или перемещает папки \(ссылки\).|
|[Dfsutil Target](dfsutil-target.md)|Отображает, создает, удаляет целевой объект папки или сервер пространства имен.|
|[Dfsutil, свойство](dfsutil-property.md)|Отображает или изменяет целевой объект папки или сервер пространства имен.|
|[Dfsutil Client](dfsutil-client.md)|Отображает или изменяет сведения о клиенте или разделы реестра.|
|[Dfsutil Server](dfsutil-server.md)|Отображает или изменяет конфигурацию пространства имен.|
|[Dfsutil DIAG](dfsutil-diag.md)|Выполните диагностику или просмотрите дфсдирс\/дфспас.|
|[Dfsutil domain](dfsutil-domain.md)|Отображает все пространства имен на основе доменного\-в домене.|
|[Dfsutil Cache](dfsutil-cache.md)|Отображает или очищает кэш клиента.|
|[Dfsutil олдкли](dfsutil-oldcli.md)|Используйте команду Dfsutil \/олдкли, чтобы использовать исходный синтаксис команды Dfsutil.|

## <a name="remarks-optional-section"></a>Примечания <optional section>
Если указать объект \(например, сервер пространства имен\) в конце команды, в большинстве команд будут отображаться сведения об объекте без дополнительных параметров или команд. Например, при использовании команды Dfsutil root можно добавить к команде корень пространства имен, чтобы просмотреть сведения об корне.

## <a name="BKMK_Examples"></a>Примеров
&lt;здесь вы поместите подробное описание вашего примера.&gt;

```
This /is /the /example /of /calling /command /with /parameters
```

&lt;здесь вы помещаете подробное описание другого примера.&gt;

```
This /is /a:different /example
```

## <a name="additional-references"></a>Дополнительные ссылки

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)


