---
title: bitsadmin getstate
description: Раздел команд Windows для битсадминного состояния
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1252d6cf-14ca-44df-beb2-930ff011f297
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2cff790c8787b1514e8523a4583184d6f6a59efc
ms.sourcegitcommit: 51e0b575ef43cd16b2dab2db31c1d416e66eebe8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2020
ms.locfileid: "76259109"
---
# <a name="bitsadmin-getstate"></a>bitsadmin getstate


Возвращает состояние указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetState <Job>
```

## <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
|    Job    | Отображаемое имя задания или идентификатор GUID |

## <a name="remarks"></a>Примечания.

Возможные состояния:

|      Штат или регион      | Описание |
| --------------- | ----------- |
| В очереди          | Задание ожидает запуска. |
| ПОДКЛЮЧЕНИЕ      | Служба BITS свяжется с сервером. |
| ПЕРЕДАЧА    | BITS передает данные. |
| ПЕРЕДАЮТСЯ     | Служба BITS успешно передала все файлы в задании. |
| ПРИОСТАНОВЛЕННЫЕ       | Задание приостановлено. |
| ОШИБКА           | Произошла неустранимая ошибка; Повторная попытка перемещения не выполняется. |
| TRANSIENT_ERROR | Произошла устранимая ошибка; Повторная попытка передачи после истечения минимальной задержки. |
| ПОДТВЕРЖДЕНО    | Задание завершено. |
| ОТМЕНЕНО        | Задание отменено. |

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается состояние для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /GetState myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
