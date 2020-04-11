---
title: битсадмин сеткустомхеадерс
description: Раздел команд Windows для **битсадмин сеткустомхеадерс**, который добавляет пользовательский заголовок HTTP к запросу Get.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ed926410-80d0-46ed-9a90-f752c164bb9a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b5b1a28f03815a22a3f8d10b2c3d1d4a3a2ae635
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123029"
---
# <a name="bitsadmin-setcustomheaders"></a>битсадмин сеткустомхеадерс

Добавьте пользовательский заголовок HTTP в запрос GET, отправляемый на HTTP-сервер.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setcustomheaders <job> <header1> <header2> <...>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| `<header1> <header2>` и т. д. | Пользовательские заголовки для задания. |

## <a name="examples"></a>Примеры

В следующем примере добавляется пользовательский заголовок HTTP для задания с именем *мидовнлоаджоб*. Дополнительные сведения о запросах GET см. в разделе [определения методов](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.3) и [определения полей заголовка](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html).

```
C:\>bitsadmin /setcustomheaders myDownloadJob accept-encoding:deflate/gzip
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)