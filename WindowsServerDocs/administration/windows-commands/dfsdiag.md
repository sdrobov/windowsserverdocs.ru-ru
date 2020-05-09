---
title: дфсдиаг
description: Справочный раздел по команде дфсдиаг, который предоставляет диагностические сведения для пространств имен DFS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c0891e67-0187-4f18-923d-5623e6127f90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7e9e0de18b48a4233b950ad6aa8f1e450a99da62
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992829"
---
# <a name="dfsdiag"></a>дфсдиаг

Предоставляет диагностические сведения для пространств имен DFS.

## <a name="syntax"></a>Синтаксис

```
dfsdiag /testdcs [/domain:<domain name>]
dfsdiag /testsites </machine:<server name>| /DFSPath:<namespace root or DFS folder> [/recurse]> [/full]
dfsdiag /testdfsconfig /DFSRoot:<namespace>
dfsdiag /testdfsintegrity /DFSRoot:<DFS root path> [/recurse] [/full]
dfsdiag /testreferral /DFSpath:<DFS path to get referrals> [/full]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| [дфсдиаг тестдкс](dfsdiag-testdcs.md) | Проверяет конфигурацию контроллера домена. |
| [дфсдиаг тестситес](dfsdiag-testsites.md) | Проверяет связи сайтов. |
| [дфсдиаг тестдфсконфиг](dfsdiag-testdfsconfig.md) | Проверяет конфигурацию пространства имен DFS. |
| [дфсдиаг тестдфсинтегрити](dfsdiag-testdfsintegrity.md) | Проверяет целостность пространства имен DFS. |
| [дфсдиаг тестреферрал](dfsdiag-testreferral.md) | Проверяет ответы на ссылки. |
| /? | Отображение справки в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
