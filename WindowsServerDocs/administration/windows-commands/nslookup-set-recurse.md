---
title: nslookup set recurse
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d1b7a93f-dfb0-4ccd-b230-e0953057fada
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c4386bd5738806016b9ec15802faebf3efdcedf0
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723593"
---
# <a name="nslookup-set-recurse"></a>nslookup set recurse



Предписывает серверу доменных имен (DNS) запрашивать другие серверы, если у него нет информации.

## <a name="syntax"></a>Синтаксис

```
set [no]recurse
```

### <a name="parameters"></a>Параметры

|   Параметр   |                                                                  Описание                                                                  |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| **неповторение** |                Останавливает запрос сервера доменных имен (DNS) от других серверов, если он не содержит сведений.                |
|  **Recurse**  | Предписывает серверу доменных имен (DNS) запрашивать другие серверы, если у него нет информации. Синтаксис по умолчанию — **рекурсия**. |
|     {Справка     |                                                                      ?}                                                                       |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)