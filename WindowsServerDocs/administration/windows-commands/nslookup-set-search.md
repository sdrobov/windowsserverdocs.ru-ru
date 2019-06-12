---
title: nslookup set search
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 064ac660-8b04-4af9-8b2c-e4e0549771b8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d95ebe30ce45430787bebbfe63766a571a436bbf
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436589"
---
# <a name="nslookup-set-search"></a>nslookup set search



Добавляет имена доменов доменных имен (DNS) в список поиска DNS домена на запрос, пока не будет получен ответ. Это применимо, когда набор и поиска запросов, содержать по крайней мере одну точку, но не заканчиваться точку.

## <a name="syntax"></a>Синтаксис

```
set [no]search
```

## <a name="parameters"></a>Параметры

|  Параметр   |                                                                          Описание                                                                          |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **nosearch** |                            Останавливает, добавив имена доменов доменных имен (DNS) в список поиска DNS домена на запрос.                            |
|  **Поиск**  | Добавляет имена доменов доменных имен (DNS) в список поиска DNS домена на запрос, пока не будет получен ответ. По умолчанию используется синтаксис **поиска**. |
|    {справки     |                                                                              ?}                                                                               |

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)