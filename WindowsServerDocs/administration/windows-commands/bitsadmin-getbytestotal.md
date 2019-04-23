---
title: bitsadmin getbytestotal
description: Раздел Windows команды для **bitsadmin getbytestotal** -извлекает размер указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 784e0bfa-7b09-4262-9104-adbc9beb479b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d7a33b02dbdea63e87bd8ce56a2d50e15ca19d05
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882865"
---
# <a name="bitsadmin-getbytestotal"></a>bitsadmin getbytestotal



Возвращает размер указанного задания

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetBytesTotal <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается размер задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetBytesTotal myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)