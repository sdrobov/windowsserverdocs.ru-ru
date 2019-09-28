---
title: bitsadmin getbytestransferred
description: Раздел команд Windows для **битсадмин жетбитестрансферред** — получает число байтов, переданных для указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47bbf184-e06f-4be0-b2ba-d32b10d82002
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f690fa55a4ac5ae31223794c5e7eabc0c982c2ce
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381731"
---
# <a name="bitsadmin-getbytestransferred"></a>bitsadmin getbytestransferred



Возвращает число байтов, переданных для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetBytesTransferred <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается число байтов, передаваемых для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetBytesTransferred myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)