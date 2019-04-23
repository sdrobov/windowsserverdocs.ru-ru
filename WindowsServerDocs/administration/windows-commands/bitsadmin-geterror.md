---
title: bitsadmin geterror
description: Раздел Windows команды для **bitsadmin geterror** — извлекает подробные сведения об ошибке для указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cbe5bca1-d2dd-4ce6-903f-f85de4a2ec6a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 10a3373c0c8f290ff1f5f26ef38531fbc7745890
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889975"
---
# <a name="bitsadmin-geterror"></a>bitsadmin geterror



Извлекает подробные сведения об ошибке для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetError <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

Следующий пример извлекает сведения об ошибке задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetError myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)