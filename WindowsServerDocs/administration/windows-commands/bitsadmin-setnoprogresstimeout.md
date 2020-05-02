---
title: bitsadmin setnoprogresstimeout
description: Справочный раздел по команде битсадмин сетнопрогресстимеаут, который задает время в секундах, в течение которого служба пытается переместить файл после возникновения временной ошибки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7fac50d9-cc6b-46a4-a96f-fab751ee1756
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 398882cf795e98dc0bbc0fb81006d3406fded707
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720106"
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
| задание | Отображаемое имя задания или идентификатор GUID. |
| тимеаутвалуе | Продолжительность времени, в течение которого служба BITS ожидает передачи файла после первой ошибки в секундах. |

### <a name="remarks"></a>Примечания

- Интервал времени ожидания "не выполняется" начинается, когда задание сталкивается с первой временной ошибкой.

- Интервал времени ожидания останавливается или сбрасывается при успешном передаче байта данных.

- Если интервал времени ожидания "не выполнено" превышает значение *тимеаутвалуе*, задание помещается в неустранимую ошибку.

## <a name="examples"></a>Примеры

Чтобы установить значение времени ожидания "не выполняется" равным 20 секундам, для задания с именем *мидовнлоаджоб*:

```
bitsadmin /setnoprogresstimeout myDownloadJob 20
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
