---
title: кэш битсадмин и сетлимит
description: Команды Windows для **кэша битсадмин и сетлимит**, устанавливающие предельный размер кэша.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 46578835-d5ce-423b-be4d-62ddb9e1908d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 746ee0b69da8f5bd22fec2ccbd432126cc25d94d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850877"
---
# <a name="bitsadmin-cache-and-setlimit"></a>кэш битсадмин и сетлимит

Задает предельный размер кэша.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /cache /setlimit percent
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| percent | Предельный размер кэша, определенный в процентах от общего пространства на жестком диске. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере размер кэша ограничивается 50%.

```
C:\>bitsadmin /cache /setlimit 50
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)