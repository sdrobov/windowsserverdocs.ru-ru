---
title: битсадмин сесттпмесод
description: Раздел команд Windows для **битсадмин сесттпмесод**, который задает используемую команду HTTP.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: d349dcad7bdf6a6fc566ed961c3160836d7f49da
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122969"
---
# <a name="bitsadmin-sethttpmethod"></a>битсадмин сесттпмесод

Задает используемую команду HTTP.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /sethttpmethod <job> <httpmethod>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| HttpMethod | Команда HTTP для использования. Дополнительные сведения о доступных командах см. в разделе [определения методов](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html). |

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)