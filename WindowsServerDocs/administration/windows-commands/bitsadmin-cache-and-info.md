---
title: bitsadmin cache и info
description: Справочная статья по команде кэша битсадмин и info, которая создает дамп определенной записи кэша.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 15975cbf-dba6-49ca-a725-d15ce1952de5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dabf9b229138bf1d39863643574c5509ffcfcd91
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923263"
---
# <a name="bitsadmin-cache-and-info"></a>bitsadmin cache и info

Создает дамп определенной записи кэша.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /cache /info recordID [/verbose]
```

### <a name="parameters"></a>Параметры

| парамретер | Описание |
| -------------- | -------------- |
| recordID | Идентификатор GUID, связанный с записью кэша. |

## <a name="examples"></a>Примеры

Чтобы сохранить запись кэша с значением recordID, равным {6511FB02-E195-40A2-B595-E8E2F8F47702}:

```
bitsadmin /cache /info {6511FB02-E195-40A2-B595-E8E2F8F47702}
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда кэша битсадмин](bitsadmin-cache.md)
