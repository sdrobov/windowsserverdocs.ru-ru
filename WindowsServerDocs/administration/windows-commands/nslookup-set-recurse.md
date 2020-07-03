---
title: nslookup set recurse
description: Справочная статья по команде nslookup set recurse, которая сообщает серверу доменных имен (DNS) о необходимости запрашивать другие серверы, если не удается найти сведения на указанном сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d1b7a93f-dfb0-4ccd-b230-e0953057fada
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dd65eaa9ba60e2a3cdf79e808b2efccb28b7d455
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935697"
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
