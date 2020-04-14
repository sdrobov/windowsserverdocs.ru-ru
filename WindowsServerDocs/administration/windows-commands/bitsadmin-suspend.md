---
title: bitsadmin suspend
description: Раздел команд Windows для **битсадмин Suspend**, который приостанавливает указанное задание.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f9d42500-7bea-4aa8-a9f0-c22f6ed3e73b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 42ed83d4dbf8c3d982c5c186b440cf17997903c9
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123156"
---
# <a name="bitsadmin-suspend"></a>bitsadmin suspend

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Приостанавливает указанное задание. Если вы приостановили задание по ошибке, можно использовать параметр [возобновления битсадмин](bitsadmin-resume.md) , чтобы перезапустить задание.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /suspend <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ---------- |
| Job | Отображаемое имя задания или идентификатор GUID. |

## <a name="example"></a>Пример

В следующем примере приостанавливается задание с именем *мидовнлоаджоб*.


```
C:\>bitsadmin /suspend myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
