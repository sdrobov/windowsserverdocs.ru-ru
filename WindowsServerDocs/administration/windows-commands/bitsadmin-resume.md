---
title: bitsadmin resume
description: Справочная статья по команде битсадмин Resume, которая активирует новое или приостановленное задание в очереди на перемещение.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c7540a9-a11a-4910-923a-2a2a61cbf11d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cd2a8dcb486c584ef4adaf96a5288a9db32d4553
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927961"
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
