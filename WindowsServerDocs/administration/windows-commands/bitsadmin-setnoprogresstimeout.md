---
title: bitsadmin setnoprogresstimeout
description: Справочная статья по команде битсадмин сетнопрогресстимеаут, которая задает время в секундах, в течение которого служба пытается переместить файл после возникновения временной ошибки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7fac50d9-cc6b-46a4-a96f-fab751ee1756
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9bb7ac4cd03148c533aa27f62a1c9770465673a5
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927670"
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

### <a name="remarks"></a>Комментарии

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
