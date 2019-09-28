---
title: bitsadmin setnoprogresstimeout
description: Раздел команд Windows для **битсадмин сетнопрогресстимеаут** . задает время в секундах, в течение которого служба пытается переместить файл после возникновения временной ошибки.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 761d0d76a2c70af9d4ad68aa564c1a9816691d0d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380496"
---
# <a name="bitsadmin-setnoprogresstimeout"></a>bitsadmin setnoprogresstimeout

Задает период времени в секундах, в течение которого BITS пытается переместить файл после первой временной ошибки.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetNoProgressTimeout <Job> <TimeOutvalue>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|тимеаутвалуе|Число, представленное в секундах.|

## <a name="remarks"></a>Примечания

-   Интервал времени ожидания не выполняется, когда задание встречает временную ошибку.
-   Интервал времени ожидания останавливается или сбрасывается при успешном передаче байта данных.
-   Если интервал времени ожидания выполнения превышает *тимеаутвалуе*, задание помещается в неустранимую ошибку.

## <a name="BKMK_examples"></a>Примеров

В следующем примере устанавливается значение времени ожидания "нет выполнения" для задания с именем *мидовнлоаджоб* равным 20 секундам.
```
C:\>bitsadmin /SetNoProgressTimeout myDownloadJob 20
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)