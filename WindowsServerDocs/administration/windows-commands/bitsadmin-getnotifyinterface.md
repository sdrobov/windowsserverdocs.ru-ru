---
title: bitsadmin getnotifyinterface
description: Справочная статья по команде битсадмин жетнотифинтерфаце, которая определяет, зарегистрировал ли другая программа интерфейс обратного вызова COM для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 40bf9dd8-b167-406a-80a6-a5a6f1b8cf7f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9c86b611eb5f46759c474171085884c5702e07d1
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926903"
---
# <a name="bitsadmin-getnotifyinterface"></a>bitsadmin getnotifyinterface

Определяет, зарегистрировал ли другая программа интерфейс обратного вызова COM (интерфейс уведомления) для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getnotifyinterface <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

#### <a name="output"></a>Выходные данные

Выходные данные этой команды отображаются как, **зарегистрированные** или **отмененные**.

> [!NOTE]
> Невозможно определить программу, которая зарегистрировала интерфейс обратного вызова.

## <a name="examples"></a>Примеры

Чтобы получить интерфейс уведомления для задания с именем *мидовнлоаджоб*:

```
bitsadmin /getnotifyinterface myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
