---
title: bitsadmin getmodificationtime
description: Раздел команд Windows для **битсадмин жетмодификатионтиме**, который извлекает время последнего изменения задания или передачи данных.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e543945e-92c4-491e-8c2d-344f8a3e342d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ace0f64b1fbe7ba72174bb3df2bd4dd65e929769
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850617"
---
# <a name="bitsadmin-getmodificationtime"></a>bitsadmin getmodificationtime

Извлекает время последнего изменения задания или передачи данных.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getmodificationtime <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается время последнего изменения для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getmodificationtime myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)