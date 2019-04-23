---
title: bitsadmin gettemporaryname
description: Раздел Windows команды для **bitsadmin gettemporaryname** -сообщает временного имени файла для заданного файла, в рамках задания.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 762a2a5943202b38e94a245b74745e6631e0792d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59876715"
---
# <a name="bitsadmin-gettemporaryname"></a>bitsadmin gettemporaryname



Сообщает временного имени файла для заданного файла, в рамках задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetTemporaryName <Job> <file index> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Индекс файла|Начинается с 0|

## <a name="BKMK_examples"></a>Примеры

В следующем примере сообщается временного имени файла, файла 2 задания с именем *myJob*.
```
C:\>bitsadmin /GetTemporaryName myJob 1 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)