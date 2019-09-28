---
title: bitsadmin list
description: Раздел команд Windows для **битсадмин List** — список заданий перемещения, принадлежащих текущему пользователю.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1416965e-e0e6-49cf-b1d4-b286d3cf8716
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bd4787f51dc2a7843ff6cf5c4f786658e530ad8f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381096"
---
# <a name="bitsadmin-list"></a>bitsadmin list



Список заданий перемещения, принадлежащих текущему пользователю.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /List [/allusers][/verbose]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/аллусерс|(Необязательно) список заданий для всех пользователей|
|/Verbose|(Необязательно) предоставляет подробные сведения для каждого задания.|

## <a name="remarks"></a>Примечания

Для использования параметра/аллусерс необходимо иметь права администратора.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекаются сведения о заданиях, принадлежащих текущему пользователю.
```
C:\>bitsadmin /List 
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)