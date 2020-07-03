---
title: bitsadmin suspend
description: Справочная статья по команде битсадмин Suspend, которая приостанавливает указанное задание.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f9d42500-7bea-4aa8-a9f0-c22f6ed3e73b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 42257d31dbada2badc12b44b6375702ac41a91ca
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927475"
---
# <a name="bitsadmin-suspend"></a>bitsadmin suspend

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Приостанавливает указанное задание. Если вы приостановили задание по ошибке, можно использовать параметр [возобновления битсадмин](bitsadmin-resume.md) , чтобы перезапустить задание.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /suspend <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ---------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="example"></a>Пример

Чтобы приостановить задание с именем *мидовнлоаджоб*:


```
bitsadmin /suspend myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда возобновления битсадмин](bitsadmin-resume.md)

- [Команда битсадмин](bitsadmin.md)
