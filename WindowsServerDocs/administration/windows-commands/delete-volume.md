---
title: delete volume
description: Раздел команд Windows для удаления тома, который удаляет выбранный том.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f625933d-0f47-409e-93b2-a3e234049a5d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f2e958785c278306563999b09c1fecc0fdfa7ecb
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846557"
---
# <a name="delete-volume"></a>delete volume

Удаляет выбранный том.

## <a name="syntax"></a>Синтаксис

```
delete volume [noerr]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Noerr | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |

## <a name="remarks"></a>Примечания

-   Невозможно удалить системный том, загрузочный том, а также любой том, содержащий активный файл подкачки или аварийный дамп (дамп памяти).
-   Для выполнения этой операции необходимо выбрать том. Используйте команду **выбрать том** , чтобы выбрать том и переместить фокус на него.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы удалить том с фокусом, введите:
```
delete volume
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

