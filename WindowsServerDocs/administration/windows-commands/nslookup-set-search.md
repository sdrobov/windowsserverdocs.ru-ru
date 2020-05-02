---
title: nslookup set search
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 064ac660-8b04-4af9-8b2c-e4e0549771b8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2e3f5bce42d3614b535b2dfb00c4c9ea9cac2346
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723567"
---
# <a name="nslookup-set-search"></a>nslookup set search



Добавляет доменные имена DNS в списке поиска доменов DNS в запрос, пока не будет получен ответ. Это применимо, когда набор и запрос уточняющего запроса содержат по крайней мере одну точку, но не заканчиваются точкой в конце.

## <a name="syntax"></a>Синтаксис

```
set [no]search
```

### <a name="parameters"></a>Параметры

|  Параметр   |                                                                          Описание                                                                          |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **не искать** |                            Прекращает добавление доменных имен службы доменных имен (DNS) в список поиска доменов DNS для запроса.                            |
|  **осуществлять**  | Добавляет доменные имена DNS в списке поиска доменов DNS в запрос, пока не будет получен ответ. Синтаксис по умолчанию — **Поиск**. |
|    {Справка     |                                                                              ?}                                                                               |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)