---
title: bitsadmin getvalidationstate
description: Справочная статья по команде битсадмин жетвалидатионстате, которая сообщает состояние проверки содержимого заданного файла в задании.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6ada3f1f-9967-4262-9d22-ed641e23f516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 72d53572411a33259467fa8023b9ef08fe4a5595
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926625"
---
# <a name="bitsadmin-getvalidationstate"></a>bitsadmin getvalidationstate

Сообщает состояние проверки содержимого заданного файла в задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getvalidationstate <job> <file_index>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| file_index | Начинается с 0. |

## <a name="examples"></a>Примеры

Чтобы получить состояние проверки содержимого файла 2 в задании с именем *мидовнлоаджоб*:

```
bitsadmin /getvalidationstate myDownloadJob 1
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
