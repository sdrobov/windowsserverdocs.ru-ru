---
title: bitsadmin gethttpmethod
description: Справочный раздел для команды битсадмин жесттпмесод, которая получает команду HTTP для использования с заданием.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: a458322a5ace69df74df054a537a7365da9e7329
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717886"
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
