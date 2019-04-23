---
title: bitsadmin setnoprogresstimeout
description: Раздел Windows команды для **bitsadmin setnoprogresstimeout** -задает продолжительность времени, в секундах, которое служба пытается передать файл после возникает временная ошибка.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7fac50d9-cc6b-46a4-a96f-fab751ee1756
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 45dd8a7ddfae877984a98db66c742e0af4d18f0d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873775"
---
# <a name="bitsadmin-setnoprogresstimeout"></a>bitsadmin setnoprogresstimeout

Задает продолжительность времени, в секундах, которое служба BITS пытается передать файл после первой временной ошибки.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetNoProgressTimeout <Job> <TimeOutvalue>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Значение_таймаута|Число, представленное в секундах.|

## <a name="remarks"></a>Примечания

-   Интервал времени ожидания не ход выполнения начинается, когда задание обнаруживает ошибку.
-   Интервал времени ожидания, останавливает или сбрасывает при успешной передаче байт данных.
-   Если интервал времени ожидания не ход выполнения превышает *Значение_таймаута*, то задание помещается в состоянии Неустранимая ошибка.

## <a name="BKMK_examples"></a>Примеры

В следующем примере значение без времени ожидания ход выполнения задания с именем *myDownloadJob* до 20 секунд
```
C:\>bitsadmin /SetNoProgressTimeout myDownloadJob 20
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)