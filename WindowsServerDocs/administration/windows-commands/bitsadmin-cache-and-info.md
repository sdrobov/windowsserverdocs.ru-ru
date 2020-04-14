---
title: кэш битсадмин и сведения
description: Раздел команд Windows для **кэша битсадмин и сведения**, который создает дамп определенной записи кэша.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 15975cbf-dba6-49ca-a725-d15ce1952de5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3e9c6ce1eb972a76408483b8a27a3abca5500e56
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850897"
---
# <a name="bitsadmin-cache-and-info"></a>кэш битсадмин и сведения

Создает дамп определенной записи кэша.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /cache /info recordID [/verbose]
```

### <a name="parameters"></a>Параметры

| парамретер | Описание |
| -------------- | -------------- |
| recordID | Идентификатор GUID, связанный с записью кэша. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере запись кэша выводится с помощью значения recordID, равного {6511FB02-E195-40A2-B595-E8E2F8F47702}.

```
C:\>bitsadmin /cache /info {6511FB02-E195-40A2-B595-E8E2F8F47702}
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)