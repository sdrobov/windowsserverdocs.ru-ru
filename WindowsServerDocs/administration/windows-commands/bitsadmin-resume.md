---
title: bitsadmin resume
description: Справочный раздел по команде битсадмин Resume, который активирует новое или приостановленное задание в очереди на перемещение.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c7540a9-a11a-4910-923a-2a2a61cbf11d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ba4cd57ddeeb3c35ca0871c2953fd409ddb57e73
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716996"
---
# <a name="bitsadmin-resume"></a>bitsadmin resume

Активирует новое или приостановленное задание в очереди на перемещение. Если вы возобновили задание по ошибке или просто хотите приостановить задание, можно использовать параметр [Suspend битсадмин](bitsadmin-suspend.md) для приостановки задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /resume <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы возобновить задание с именем *мидовнлоаджоб*:

```
bitsadmin /resume myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [битсадмин Suspend, команда](bitsadmin-suspend.md)

- [Команда битсадмин](bitsadmin.md)
