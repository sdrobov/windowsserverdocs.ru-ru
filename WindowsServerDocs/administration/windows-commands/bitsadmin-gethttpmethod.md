---
title: bitsadmin gethttpmethod
description: Справочная статья по команде битсадмин жесттпмесод, которая получает команду HTTP для использования с заданием.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 3a963eb275c6e635849094906c52fedf90dccd0d
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927025"
---
# <a name="bitsadmin-gethttpmethod"></a>bitsadmin gethttpmethod

Возвращает команду HTTP для использования с заданием.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /gethttpmethod <Job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить команду HTTP для использования с заданием с именем *мидовнлоаджоб*:

```
bitsadmin /gethttpmethod myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
