---
title: nslookup set recurse
description: Справочный раздел команды nslookup set recurse, которая сообщает серверу доменных имен (DNS) о необходимости запрашивать другие серверы, если не удается найти сведения на указанном сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d1b7a93f-dfb0-4ccd-b230-e0953057fada
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 082ba3bd926d1f47be5510c2340804b1b92991f1
ms.sourcegitcommit: 99d548141428c964facf666c10b6709d80fbb215
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2020
ms.locfileid: "84721623"
---
# <a name="nslookup-set-recurse"></a>nslookup set recurse

Указывает серверу доменных имен (DNS) запрашивать другие серверы, если не удается найти сведения на указанном сервере.

## <a name="syntax"></a>Синтаксис

```
set [no]recurse
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ---------- | ---------- |
| неповторение | Останавливает запросы сервера доменных имен (DNS) от других серверов, если не удается найти сведения на указанном сервере. |
| Recurse | Указывает серверу доменных имен (DNS) запрашивать другие серверы, если не удается найти сведения на указанном сервере. Это значение по умолчанию. |
| /? | Отображение справки в командной строке. |
| /help | Отображение справки в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
