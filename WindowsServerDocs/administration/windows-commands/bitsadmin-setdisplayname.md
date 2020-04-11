---
title: bitsadmin setdisplayname
description: Раздел команд Windows для **битсадмин сетдисплайнаме**, который задает отображаемое имя указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 13706c53-fb5f-4879-b5ca-82531361d6e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0b1086903dd130392800f325c451bb4750fbf8fa
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123005"
---
# <a name="bitsadmin-setdisplayname"></a>bitsadmin setdisplayname

Задает отображаемое имя для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setdisplayname <job> <display_name>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| display_name | Текст, используемый в качестве отображаемого имени для конкретного задания. |

## <a name="examples"></a>Примеры

В следующем примере задается отображаемое имя задания *мидовнлоаджоб*.

```
C:\>bitsadmin /setdisplayname myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)