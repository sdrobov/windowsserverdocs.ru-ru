---
title: bitsadmin setdisplayname
description: Справочная статья по команде битсадмин сетдисплайнаме, которая задает отображаемое имя указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 13706c53-fb5f-4879-b5ca-82531361d6e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b7cd1ce068e1e2a89b27ee88653fdd014d2da178
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927793"
---
# <a name="bitsadmin-setdisplayname"></a>bitsadmin setdisplayname

Задает отображаемое имя для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setdisplayname <job> <display_name>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| display_name | Текст, используемый в качестве отображаемого имени для конкретного задания. |

## <a name="examples"></a>Примеры

Чтобы задать отображаемое имя для задания *мидовнлоаджоб*, сделайте следующее:

```
bitsadmin /setdisplayname myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
