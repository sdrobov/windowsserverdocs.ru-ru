---
title: nslookup set search
description: Справочный раздел по команде nslookup set Search, который добавляет доменные имена DNS в список поиска доменов DNS, пока не будет получен ответ.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 064ac660-8b04-4af9-8b2c-e4e0549771b8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c3219434f768a573c9e433c44b6b38bc9dc75f14
ms.sourcegitcommit: 99d548141428c964facf666c10b6709d80fbb215
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2020
ms.locfileid: "84721429"
---
# <a name="nslookup-set-search"></a>nslookup set search

Добавляет доменные имена DNS в списке поиска доменов DNS в запрос, пока не будет получен ответ. Это применимо, когда набор и запрос уточняющего запроса содержат по крайней мере одну точку, но не заканчиваются точкой в конце.

## <a name="syntax"></a>Синтаксис

```
set [no]search
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| не искать | Прекращает добавление доменных имен службы доменных имен (DNS) в списке поиска доменов DNS для запроса. |
| search | Добавляет доменные имена системы доменных имен (DNS) в список поиска доменов DNS для запроса, пока не будет получен ответ. Это значение по умолчанию. |
| /? | Отображение справки в командной строке. |
| /help | Отображение справки в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
