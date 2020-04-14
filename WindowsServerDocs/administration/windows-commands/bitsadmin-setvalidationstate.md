---
title: битсадмин сетвалидатионстате
description: Раздел команд Windows для **битсадмин сетвалидатионстате**, который задает состояние проверки содержимого заданного файла в задании.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e8fc8e8c-171c-4681-8057-6986b018e576
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6bec42ae926050cd21df594a38f1c441a40a527f
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122711"
---
# <a name="bitsadmin-setvalidationstate"></a>битсадмин сетвалидатионстате

Задает состояние проверки содержимого заданного файла в задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setvalidationstate <job> <file_index> <TRUE|FALSE>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ---------- |
| Job | Отображаемое имя задания или идентификатор GUID. |
| file_index | Начинается с 0. |
| TRUE или FALSE | **Значение true** включает проверку содержимого для указанного файла, а **значение false** отключает его. |

## <a name="examples"></a>Примеры

В следующем примере состояние проверки содержимого файла 2 устанавливается равным TRUE для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /setvalidationstate myDownloadJob 2 TRUE
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)