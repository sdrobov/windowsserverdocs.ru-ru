---
title: bitsadmin getaclflags
description: Раздел Windows команды для **bitsadmin getaclflags** -извлекает Флаги распространения списка элемента управления.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99266def-7479-4430-a61c-98ec433fa88b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 185445a97168344f910abc0e644718296de2c712
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59861455"
---
# <a name="bitsadmin-getaclflags"></a>bitsadmin getaclflags

Извлекает Флаги распространения элемента управления списка управления Доступом.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetAclFlags <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Отображает один или несколько из следующих значений флага:
-   O: Скопируйте сведения о владельце с файлом.
-   G: Скопируйте сведения о группах с файлом.
-   D: Скопируйте сведения DACL с файлом.
-   S: Скопируйте сведения системный список управления ДОСТУПОМ с файлом.

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается Флаги распространения списка управления доступом задания с именем *myDownloadJob*.
```
C:\>bitsadmin /getaclflags myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)