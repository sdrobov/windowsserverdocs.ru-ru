---
title: delete volume
description: Справочная статья по команде удаления тома, которая удаляет выбранный том.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f625933d-0f47-409e-93b2-a3e234049a5d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 217e9ff1ccb470b5431143360286d312b09a1951
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928714"
---
# <a name="delete-volume"></a>delete volume

Удаляет выбранный том. Прежде чем начать, необходимо выбрать том для выполнения этой операции. Используйте команду [выбрать том](select-volume.md) , чтобы выбрать том и переместить фокус на него.

> [!IMPORTANT]
> Нельзя удалить системный том, загрузочный том или любой том, содержащий активный файл подкачки или аварийный дамп (дамп памяти).

## <a name="syntax"></a>Синтаксис

```
delete volume [noerr]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Noerr | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |

## <a name="examples"></a>Примеры

Чтобы удалить том с фокусом, введите:

```
delete volume
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [select volume](select-volume.md)

- [удалить команду](delete.md)