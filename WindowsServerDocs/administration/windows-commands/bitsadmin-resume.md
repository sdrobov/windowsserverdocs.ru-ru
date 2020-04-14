---
title: bitsadmin resume
description: Раздел команд Windows для **битсадмин Resume**, который активирует новое или приостановленное задание в очереди на перемещение.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c7540a9-a11a-4910-923a-2a2a61cbf11d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e81bd80232cd4ec8fbba70c86cd97bb9695680f8
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123070"
---
# <a name="bitsadmin-resume"></a>bitsadmin resume

Активирует новое или приостановленное задание в очереди на перемещение.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /resume <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

В следующем примере возобновляется задание с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /resume myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)