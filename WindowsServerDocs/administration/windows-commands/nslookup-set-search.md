---
title: nslookup set search
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: d9da08a296d61789dbafeccde5d46c8a220d874c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372777"
---
# <a name="nslookup-set-search"></a>nslookup set search



Добавляет доменные имена DNS в списке поиска доменов DNS в запрос, пока не будет получен ответ. Это применимо, когда набор и запрос уточняющего запроса содержат по крайней мере одну точку, но не заканчиваются точкой в конце.

## <a name="syntax"></a>Синтаксис

```
set [no]search
```

## <a name="parameters"></a>Параметры

|  Параметр   |                                                                          Описание                                                                          |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **не искать** |                            Прекращает добавление доменных имен службы доменных имен (DNS) в список поиска доменов DNS для запроса.                            |
|  **осуществлять**  | Добавляет доменные имена DNS в списке поиска доменов DNS в запрос, пока не будет получен ответ. Синтаксис по умолчанию — **Поиск**. |
|    {Справка     |                                                                              ?}                                                                               |

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)