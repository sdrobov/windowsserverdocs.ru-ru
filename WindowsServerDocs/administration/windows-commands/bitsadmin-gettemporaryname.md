---
title: битсадмин жеттемпораринаме
description: Раздел команд Windows для **битсадмин жеттемпораринаме** . сообщает о временном имени файла заданного в задании.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68925edc-a801-4292-a812-7471c4f60fdd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7b665fae4c0bfdd5ea04b929be49f9590430b358
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381302"
---
# <a name="bitsadmin-gettemporaryname"></a>битсадмин жеттемпораринаме



Сообщает имя временного файла заданного файла в задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetTemporaryName <Job> <file index> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Индекс файла|Начинается с 0|

## <a name="BKMK_examples"></a>Примеров

В следующем примере выводится временное имя файла 2 для задания с именем *myJob*.
```
C:\>bitsadmin /GetTemporaryName myJob 1 
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)