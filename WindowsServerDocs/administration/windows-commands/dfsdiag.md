---
title: dfsdiag
description: Справочная статья по команде дфсдиаг, которая предоставляет диагностические сведения для пространств имен DFS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c0891e67-0187-4f18-923d-5623e6127f90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 97f39d740bc321ebcece69ff0690dfac7aab6567
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928669"
---
# <a name="dfsdiag"></a>dfsdiag

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
| [dfsdiag testdcs](dfsdiag-testdcs.md) | Проверяет конфигурацию контроллера домена. |
| [dfsdiag testsites](dfsdiag-testsites.md) | Проверяет связи сайтов. |
| [dfsdiag testdfsconfig](dfsdiag-testdfsconfig.md) | Проверяет конфигурацию пространства имен DFS. |
| [dfsdiag testdfsintegrity](dfsdiag-testdfsintegrity.md) | Проверяет целостность пространства имен DFS. |
| [dfsdiag testreferral](dfsdiag-testreferral.md) | Проверяет ответы на ссылки. |
| /? | Отображение справки в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
