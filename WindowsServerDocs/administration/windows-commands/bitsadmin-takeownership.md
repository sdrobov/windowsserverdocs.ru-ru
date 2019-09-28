---
title: bitsadmin takeownership
description: Раздел команд Windows для **битсадмин такеовнершип** . позволяет пользователю с правами администратора становиться владельцем указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea0ce7cb-440a-498f-a3ef-8368fa43e399
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f0d0610b2ba6437f6fdd41bf1b875993cf11f2a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380359"
---
# <a name="bitsadmin-takeownership"></a>bitsadmin takeownership



Позволяет пользователю с правами администратора становиться владельцем указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /TakeOwnership <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере выполняется владение заданием с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /TakeOwnership myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)