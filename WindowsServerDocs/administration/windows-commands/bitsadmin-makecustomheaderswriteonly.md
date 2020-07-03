---
title: bitsadmin makecustomheaderswriteonly
description: Справочная статья по команде битсадмин макекустомхеадерсвритеонли, которая делает пользовательские заголовки HTTP для задания только для записи.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 3a97054bb9e8156de23e07d18d9806e04c59e967
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926527"
---
# <a name="bitsadmin-makecustomheaderswriteonly"></a>bitsadmin makecustomheaderswriteonly

Сделайте пользовательские HTTP-заголовки задания только для записи.

> [!IMPORTANT]
> Это действие нельзя отменить.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /makecustomheaderswriteonly <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы сделать пользовательские заголовки HTTP только для записи для задания с именем *мидовнлоаджоб*, сделайте следующее:

```
bitsadmin /makecustomheaderswriteonly myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
