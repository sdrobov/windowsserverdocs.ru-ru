---
title: bitsadmin getstate
description: 'Раздел Windows команды для ****- '
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
ms.openlocfilehash: 55be37a6b1b44b81ed9002e5e3b9eb1fd46bd0dc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381230"
---
# <a name="bitsadmin-getstate"></a>bitsadmin getstate



Возвращает состояние указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetState <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Возможные состояния:

|-----|-----| | В очереди | Задание ожидает выполнения. | | ПОДКЛЮЧЕНИЕ | Служба BITS свяжется с сервером. | | ПЕРЕДАЧА | BITS передает данные. | | ПРИОСТАНОВЛЕНо | Задание приостановлено. | | Ошибка | Произошла неустранимая ошибка; перенаправление не будет повторено. | | TRANSIENT_ERROR | Произошла устранимая ошибка; Повторная попытка передачи после истечения минимальной задержки. | | ПОДТВЕРЖДЕНо | Задание завершено. | | ОТМЕНЕНо | Задание отменено. |

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается состояние для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetState myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)