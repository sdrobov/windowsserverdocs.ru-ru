---
title: bitsadmin cache и setlimit
description: Справочный раздел по битсадмин кэшу и команде сетлимит, который устанавливает предельный размер кэша.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 46578835-d5ce-423b-be4d-62ddb9e1908d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a4c41102bfb87ff6d48113c4e85a821b821b5b01
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718291"
---
# <a name="bitsadmin-cache-and-setlimit"></a>bitsadmin cache и setlimit

Задает предельный размер кэша.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /cache /setlimit percent
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| percent | Предельный размер кэша, определенный в процентах от общего пространства на жестком диске. |

## <a name="examples"></a>Примеры

Чтобы установить предельный размер кэша 50%:

```
bitsadmin /cache /setlimit 50
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда кэша битсадмин](bitsadmin-cache.md)
