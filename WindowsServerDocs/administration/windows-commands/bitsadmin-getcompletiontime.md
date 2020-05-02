---
title: bitsadmin getcompletiontime
description: Справочный раздел по команде битсадмин жеткомплетионтиме, который получает время завершения передачи данных заданием.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7a4b3c1c-9832-4724-86b2-cce3c01bfa28
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9b3721401e450ae60fb77534f8eb845ff5ac3443
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718119"
---
# <a name="bitsadmin-getcompletiontime"></a>bitsadmin getcompletiontime

Возвращает время, когда задание завершило передачу данных.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getcompletiontime <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить время, когда задание с именем *мидовнлоаджоб* завершило передачу данных, сделайте следующее:

```
bitsadmin /getcompletiontime myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
