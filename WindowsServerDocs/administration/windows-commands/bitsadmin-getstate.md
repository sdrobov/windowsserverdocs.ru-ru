---
title: bitsadmin getstate
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: f7ed7529fda264efaceb6b4b36e36e728c211f3f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889625"
---
# <a name="bitsadmin-getstate"></a>bitsadmin getstate



Получает состояние указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetState <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Ниже перечислены возможные состояния:

|-----|-----| | В ОЧЕРЕДЬ | Задание ожидает выполнения. | | ПОДКЛЮЧЕНИЕ | BITS пытается связаться с сервера. | | ПЕРЕДАЧА | BITS использует для передачи данных. | | ПРИОСТАНОВЛЕНА | Задание приостановлено. | | ОШИБКА | Произошла неустранимая ошибка; Повторная передача не будет. | | TRANSIENT_ERROR | Произошла устранимая ошибка; Передача повторных попыток, по истечении срока действия задержки повтора минимальное. | | ПОДТВЕРЖДЕНО | Задание было завершено. | | ОТМЕНЕНО | Задание отменено. |

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается состояние задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetState myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)