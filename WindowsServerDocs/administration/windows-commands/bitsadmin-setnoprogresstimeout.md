---
title: bitsadmin setnoprogresstimeout
description: Раздел команд Windows для **битсадмин сетнопрогресстимеаут**, который задает время в секундах, в течение которого служба пытается переместить файл после возникновения временной ошибки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7fac50d9-cc6b-46a4-a96f-fab751ee1756
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8adff95b0dbae68634db2e248d4493549c5ac85d
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122886"
---
# <a name="bitsadmin-setnoprogresstimeout"></a>bitsadmin setnoprogresstimeout

Задает период времени в секундах, в течение которого BITS пытается переместить файл после первой временной ошибки.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setnoprogresstimeout <job> <timeoutvalue>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| тимеаутвалуе | Продолжительность времени, в течение которого служба BITS ожидает передачи файла после первой ошибки в секундах. |

## <a name="remarks"></a>Примечания

- Интервал времени ожидания "не выполняется" начинается, когда задание сталкивается с первой временной ошибкой.

- Интервал времени ожидания останавливается или сбрасывается при успешном передаче байта данных.

- Если интервал времени ожидания "не выполнено" превышает значение *тимеаутвалуе*, задание помещается в неустранимую ошибку.

## <a name="examples"></a>Примеры

В следующем примере для задания с именем *мидовнлоаджоб*устанавливается значение времени ожидания "не выполняется", равное 20 секундам.

```
C:\>bitsadmin /setnoprogresstimeout myDownloadJob 20
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)