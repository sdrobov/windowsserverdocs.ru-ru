---
title: nslookup set search
description: Справочная статья по команде nslookup set Search, которая добавляет имена доменов службы доменных имен (DNS) в список поиска доменов DNS для запроса, пока не будет получен ответ.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 064ac660-8b04-4af9-8b2c-e4e0549771b8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7b1740dd9bb3eb35c4cd1ef4890fcb977b2dc1ff
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935506"
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
| поиск | Добавляет доменные имена системы доменных имен (DNS) в список поиска доменов DNS для запроса, пока не будет получен ответ. Это значение по умолчанию. |
| /? | Отображение справки в командной строке. |
| /help | Отображение справки в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
