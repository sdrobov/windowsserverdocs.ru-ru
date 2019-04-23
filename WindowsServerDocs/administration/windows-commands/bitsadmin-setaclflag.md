---
title: bitsadmin setaclflag
description: Раздел Windows команды для **bitsadmin setaclflag** -задает флаги распространения списка управления доступом.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e3bcda0-827d-4dfd-8384-d1da018f3e10
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 89d825a4bc4512022fed98a3188537d3977fa3c3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59867405"
---
# <a name="bitsadmin-setaclflag"></a>bitsadmin setaclflag

Задает флаги распространения списка управления Доступом для задания для управления доступом. Флаги указывают, что вы хотите поддерживать владельца и данные ACL с загружаемый файл. Например, чтобы обеспечить владельца и группу с файлом, задать **флаги** для `OG`.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetAclFlags <Job> <Flags>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Флажки|Укажите одно или несколько из следующих значений флага:</br>-O: Скопируйте сведения о владельце с файлом.</br>-   G: Скопируйте сведения о группах с файлом.</br>-D: Скопируйте сведения DACL с файлом.</br>-S: Копировать системный список управления ДОСТУПОМ сведения с файлом.|

## <a name="remarks"></a>Примечания

Параметр SetAclFlags используется для поддержания сведения о списке управления владельца и доступа, при задании загружает данные из общей папки Windows (SMB).

## <a name="BKMK_examples"></a>Примеры

В следующем примере задается контроль доступа, флаги распространения списка задания с именем *myDownloadJob* для поддержания актуальности информации владельца и группу с загруженные файлы.
```
C:\>bitsadmin /setaclflags myDownloadJob OG
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)