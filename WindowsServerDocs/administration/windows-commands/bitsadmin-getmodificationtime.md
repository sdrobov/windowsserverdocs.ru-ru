---
title: bitsadmin getmodificationtime
description: Справочная статья по команде битсадмин жетмодификатионтиме, которая получает время последнего изменения задания или передачи данных.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e543945e-92c4-491e-8c2d-344f8a3e342d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9055c0ac70bc2360601ecd1b1f91c8ad3908d704
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928168"
---
# <a name="bitsadmin-getmodificationtime"></a>bitsadmin getmodificationtime

Извлекает время последнего изменения задания или передачи данных.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getmodificationtime <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить время последнего изменения для задания с именем *мидовнлоаджоб*:

```
bitsadmin /getmodificationtime myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
