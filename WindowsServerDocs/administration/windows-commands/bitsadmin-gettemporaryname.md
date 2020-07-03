---
title: bitsadmin gettemporaryname
description: Справочная статья по команде битсадмин жеттемпораринаме, которая сообщает о временном файле имени файла, указанного в задании.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 68925edc-a801-4292-a812-7471c4f60fdd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0b5dab756856f0c0905d7e3b523a2ec4f3d7cad6
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926659"
---
# <a name="bitsadmin-gettemporaryname"></a>bitsadmin gettemporaryname

Сообщает имя временного файла заданного файла в задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /gettemporaryname <job> <file_index>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| file_index | Начинается с 0. |

## <a name="examples"></a>Примеры

Чтобы сообщить о временном имени файла 2 для задания с именем *мидовнлоаджоб*:

```
bitsadmin /gettemporaryname myDownloadJob 1
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
