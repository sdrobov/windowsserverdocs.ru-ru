---
title: bitsadmin setvalidationstate
description: Справочный раздел по команде битсадмин сетвалидатионстате, который задает состояние проверки содержимого заданного файла в задании.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e8fc8e8c-171c-4681-8057-6986b018e576
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e3f22dc09eb1f70ce3c1ebd80fd6ba721e864377
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720464"
---
# <a name="bitsadmin-setvalidationstate"></a>bitsadmin setvalidationstate

Задает состояние проверки содержимого заданного файла в задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setvalidationstate <job> <file_index> <TRUE|FALSE>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ---------- |
| Задание | Отображаемое имя задания или идентификатор GUID. |
| file_index | Начинается с 0. |
| TRUE или FALSE | **Значение true** включает проверку содержимого для указанного файла, а **значение false** отключает его. |

## <a name="examples"></a>Примеры

Чтобы установить состояние проверки содержимого файла 2 в значение TRUE для задания с именем *мидовнлоаджоб*:

```
bitsadmin /setvalidationstate myDownloadJob 2 TRUE
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
