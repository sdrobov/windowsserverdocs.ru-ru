---
title: bitsadmin cache и setexpirationtime
description: Справочная статья по битсадмин кэшу и команде сетекспиратионтиме, которая задает срок действия кэша.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 00ea6e4e-b707-4b31-88dd-b61a78565c8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 60372a74acc6ea5312afb5dafcb3ab7b3299f4d2
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923252"
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
