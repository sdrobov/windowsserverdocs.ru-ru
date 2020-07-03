---
title: bitsadmin cancel
description: Справочная статья по команде битсадмин Cancel, которая удаляет задание из очереди на перемещение и удаляет все временные файлы, связанные с заданием.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7374b544-6a16-4d3e-872c-dcf4c02ad89d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 35173fe8b2e4f3888fa3a365ca25da35b8153eb4
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928365"
---
# <a name="bitsadmin-cancel"></a>bitsadmin cancel

Удаляет задание из очереди на перемещение и удаляет все временные файлы, связанные с заданием.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /cancel <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы удалить задание *мидовнлоаджоб* из очереди обмена:

```
bitsadmin /cancel myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
