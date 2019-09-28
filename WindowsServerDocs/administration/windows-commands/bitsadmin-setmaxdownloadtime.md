---
title: битсадмин сетмаксдовнлоадтиме
description: Раздел команд Windows для **битсадмин сетмаксдовнлоадтиме** — задает время ожидания загрузки в секундах.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16b96cf1-5738-415c-9b9d-c4ea8d5e4fec
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 985453de5bd2f4a06b5635ae5b0a9794d30175b0
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380558"
---
# <a name="bitsadmin-setmaxdownloadtime"></a>битсадмин сетмаксдовнлоадтиме



Задает время ожидания загрузки в секундах.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetMaxDownloadTime <Job> <Timeout>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Время ожидания|Время ожидания в секундах|

## <a name="remarks"></a>Примечания

-   Н/Д

## <a name="BKMK_examples"></a>Примеров

В следующем примере задается время ожидания для задания с именем *мидовнлоаджоб* равным 10 секундам.
```
C:\>bitsadmin /SetMaxDownloadTime myDownloadJob 10
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)