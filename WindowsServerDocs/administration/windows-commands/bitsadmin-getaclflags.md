---
title: bitsadmin getaclflags
description: Раздел команд Windows для **битсадмин жетаклфлагс** — получение флагов распространения списка управления доступом.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: ad98cd742161ae06be5cba7acde7b810eaf199d6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381787"
---
# <a name="bitsadmin-getaclflags"></a>bitsadmin getaclflags

Извлекает флаги распространения списка управления доступом (ACL).

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetAclFlags <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Отображает одно или несколько из следующих значений флагов:
-   ВЫВОДА Копирование сведений о владельце с помощью файла.
-   МОДУЛЕ Копирование сведений о группе с помощью файла.
-   ЧЕТЫРЕХМЕРНОГО Копирование сведений DACL в файл.
-   #D0 Копирование сведений SACL с помощью файла.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекаются флаги распространения списка управления доступом для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /getaclflags myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)