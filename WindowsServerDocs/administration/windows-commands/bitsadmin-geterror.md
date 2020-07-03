---
title: bitsadmin geterror
description: Справочная статья по команде битсадмин Error, которая получает подробные сведения об ошибке для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: cbe5bca1-d2dd-4ce6-903f-f85de4a2ec6a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1d729b946df4af33da3a55ff8051c59fbb5d7efe
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928301"
---
# <a name="bitsadmin-geterror"></a>bitsadmin geterror

Извлекает подробные сведения об ошибке для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /geterror <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить сведения об ошибке для задания с именем *мидовнлоаджоб*:

```
bitsadmin /geterror myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
