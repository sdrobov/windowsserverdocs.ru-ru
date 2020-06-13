---
title: nslookup set timeout
description: Справочный раздел команды nslookup set timeout, которая изменяет начальное число секунд ожидания ответа на запрос поиска.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 07afdaf4-ffec-496f-a188-4e91cf1a28f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0d8fd0d96226e193ba723cc0a726ddf5362a538c
ms.sourcegitcommit: 99d548141428c964facf666c10b6709d80fbb215
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2020
ms.locfileid: "84721389"
---
# <a name="nslookup-set-timeout"></a>nslookup set timeout

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет начальное число секунд ожидания ответа на запрос поиска. Если ответ не получен в течение указанного промежутка времени, интервал времени ожидания удваивается, и запрос отсылается повторно. Используйте команду [nslookup set retry](nslookup-set-retry.md) , чтобы определить количество попыток отправки запроса.

## <a name="syntax"></a>Синтаксис

```
set timeout=<number>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ---------- | ---------- |
| `<number>` | Указывает количество секунд ожидания ответа. Значение по умолчанию (в секундах) ожидания равно **5**. |
| /? | Отображение справки в командной строке. |
| /help | Отображение справки в командной строке. |

### <a name="examples"></a>Примеры

Установка времени ожидания получения ответа в течение 2 секунд:

```
set timeout=2
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [nslookup set retry](nslookup-set-retry.md)
