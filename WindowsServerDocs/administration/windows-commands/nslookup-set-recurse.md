---
title: nslookup set recurse
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d1b7a93f-dfb0-4ccd-b230-e0953057fada
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bdcdaecdfc6923584a53bc09f985a16ff9b76126
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838397"
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

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)