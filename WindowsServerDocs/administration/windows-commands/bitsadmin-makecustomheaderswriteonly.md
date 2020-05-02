---
title: bitsadmin makecustomheaderswriteonly
description: Справочный раздел по команде битсадмин макекустомхеадерсвритеонли, который делает пользовательские заголовки HTTP для задания только для записи.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 2aeab7e0ee7797b3e0be7be1156920f3bafc84dc
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717403"
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
