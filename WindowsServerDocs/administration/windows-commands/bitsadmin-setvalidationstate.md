---
title: bitsadmin setvalidationstate
description: Справочная статья по команде битсадмин сетвалидатионстате, которая задает состояние проверки содержимого указанного файла в задании.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e8fc8e8c-171c-4681-8057-6986b018e576
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ae776279b742e3af5af3cf555765007bbf0eb8de
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927494"
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
