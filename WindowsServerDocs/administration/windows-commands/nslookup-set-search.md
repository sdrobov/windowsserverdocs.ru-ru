---
title: nslookup set search
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 064ac660-8b04-4af9-8b2c-e4e0549771b8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9972919eae1be21d5dd30820d64dd1576b935666
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838307"
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

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)