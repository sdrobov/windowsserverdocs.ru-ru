---
title: bitsadmin setminretrydelay
description: Справочный раздел по команде битсадмин сетминретриделай, который задает минимальный интервал времени в секундах, в течение которого BITS ожидает после возникновения временной ошибки, прежде чем пытаться переместить файл.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ce8674ca-6cc5-4bb2-8dda-7dfbb1cd6830
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7fc54b4466d8f0bac12bd42ebf6c5e2c66087a15
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720124"
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
| задание | Отображаемое имя задания или идентификатор GUID. |
| retrydelay | Минимальное время ожидания BITS после ошибки во время передачи в секундах. |

## <a name="examples"></a>Примеры

Чтобы задать минимальную задержку повторных попыток в 35 секунд для задания с именем *мидовнлоаджоб*:

```
bitsadmin /setminretrydelay myDownloadJob 35
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
