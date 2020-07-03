---
title: bitsadmin sethttpmethod
description: Справочная статья по команде битсадмин сесттпмесод, которая задает используемый HTTP-команду.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 86d4749de294871a05176239cc1265974d8a7590
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927757"
---
# <a name="bitsadmin-sethttpmethod"></a>bitsadmin sethttpmethod

Задает используемую команду HTTP.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /sethttpmethod <job> <httpmethod>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| HttpMethod | Команда HTTP для использования. Дополнительные сведения о доступных командах см. в разделе [определения методов](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html). |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
