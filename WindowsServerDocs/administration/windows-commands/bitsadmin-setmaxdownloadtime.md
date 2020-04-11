---
title: битсадмин сетмаксдовнлоадтиме
description: Раздел команд Windows для **битсадмин сетмаксдовнлоадтиме**, который задает время ожидания загрузки в секундах.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 16b96cf1-5738-415c-9b9d-c4ea8d5e4fec
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f07931dfb9fabaec272384dced6d60f1335b6a94
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122915"
---
# <a name="bitsadmin-setmaxdownloadtime"></a>битсадмин сетмаксдовнлоадтиме

Задает время ожидания загрузки в секундах.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setmaxdownloadtime <job> <timeout>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| timeout | Длина времени ожидания скачивания в секундах. |

## <a name="examples"></a>Примеры

В следующем примере задается время ожидания для задания с именем *мидовнлоаджоб* равным 10 секундам.

```
C:\>bitsadmin /setmaxdownloadtime myDownloadJob 10
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)