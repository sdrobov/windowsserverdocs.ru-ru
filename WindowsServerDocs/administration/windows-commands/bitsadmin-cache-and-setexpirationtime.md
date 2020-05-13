---
title: bitsadmin cache и setexpirationtime
description: Справочный раздел по битсадмин кэшу и команде сетекспиратионтиме, который задает срок действия кэша.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 00ea6e4e-b707-4b31-88dd-b61a78565c8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: eeb1dbd0439a1a39711e2a074ada4c772b9ca016
ms.sourcegitcommit: aed942d11f1a361fc1d17553a4cf190a864d1268
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83235040"
---
# <a name="bitsadmin-cache-and-setexpirationtime"></a>bitsadmin cache и setexpirationtime

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает срок действия кэша.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /cache /setexpirationtime secs
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| сек | Количество секунд до истечения срока действия кэша. |

## <a name="examples"></a>Примеры

Чтобы задать срок действия кэша через 60 секунд:

```
bitsadmin /cache / setexpirationtime 60
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда кэша битсадмин](bitsadmin-cache.md)
