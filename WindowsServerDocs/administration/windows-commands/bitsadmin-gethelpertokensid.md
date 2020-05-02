---
title: bitsadmin gethelpertokensid
description: Справочный раздел по команде битсадмин жеселпертокенсид, который возвращает идентификатор безопасности маркера вспомогательного метода задания передачи BITS, если он задан.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: c45bf86d8a7364289db41fa390f319270a2a8386
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717893"
---
# <a name="bitsadmin-gethelpertokensid"></a>bitsadmin gethelpertokensid

Возвращает идентификатор безопасности [вспомогательного токена](https://docs.microsoft.com/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)задания передачи BITS, если он задан.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 3,0 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /gethelpertokensid <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить идентификатор безопасности для задания передачи BITS с именем *мидовнлоаджоб*, сделайте следующее:

```
bitsadmin /gethelpertokensid myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
