---
title: bitsadmin cache и delete
description: Справочная статья по команде битсадмин Cache и DELETE, которая удаляет определенную запись кэша.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 22540273-55a5-46ea-869b-6df2aa6808a1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 739215722eac761aed45d6b4dba32b2b001450b3
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927046"
---
# <a name="bitsadmin-cache-and-delete"></a>bitsadmin cache и delete

Удаляет определенную запись кэша.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /cache /delete recordID
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| recordID | Идентификатор GUID, связанный с записью кэша. |

## <a name="examples"></a>Примеры

Чтобы удалить запись кэша с RecordID {6511FB02-E195-40A2-B595-E8E2F8F47702}, сделайте следующее:

```
bitsadmin /cache /delete {6511FB02-E195-40A2-B595-E8E2F8F47702}
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда кэша битсадмин](bitsadmin-cache.md)
