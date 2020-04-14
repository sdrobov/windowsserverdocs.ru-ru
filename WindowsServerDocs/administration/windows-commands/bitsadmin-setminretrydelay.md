---
title: bitsadmin setminretrydelay
description: Раздел команд Windows для **битсадмин сетминретриделай**, который задает минимальный промежуток времени в секундах, в течение которого BITS ожидает после возникновения временной ошибки, прежде чем пытаться переместить файл.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ce8674ca-6cc5-4bb2-8dda-7dfbb1cd6830
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ddae9a62a49ca07bb03649f131a0a1ebad8ee3fe
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122879"
---
# <a name="bitsadmin-setminretrydelay"></a>bitsadmin setminretrydelay

Задает минимальное время в секундах, в течение которого BITS ожидает после возникновения временной ошибки, прежде чем пытаться переместить файл.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setminretrydelay <job> <retrydelay>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| retrydelay | Минимальное время ожидания BITS после ошибки во время передачи в секундах. |

## <a name="examples"></a>Примеры

В следующем примере устанавливается минимальная задержка повторных попыток для задания с именем *мидовнлоаджоб* до 35 секунд.

```
C:\>bitsadmin /setminretrydelay myDownloadJob 35
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)