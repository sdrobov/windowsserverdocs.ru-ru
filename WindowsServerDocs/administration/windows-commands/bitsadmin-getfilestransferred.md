---
title: bitsadmin getfilestransferred
description: Справочная статья по команде битсадмин жетфилестрансферред, которая получает количество файлов, переданных для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e282815c-938b-4ac0-a09d-9baafb656dcb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 43257dcb8350974bfb258a9970c1a6fec787a226
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928251"
---
# <a name="bitsadmin-getfilestransferred"></a>bitsadmin getfilestransferred

Возвращает количество файлов, переданных для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getfilestransferred <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить количество файлов, переданных в задании с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /getfilestransferred myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
