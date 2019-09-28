---
title: bitsadmin setaclflag
description: Раздел команд Windows для **битсадмин сетаклфлаг** . задает флаги распространения списка управления доступом.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: fbdb12c29af7b4db8b25846d43ee1c93b2454ff2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380765"
---
# <a name="bitsadmin-setaclflag"></a>bitsadmin setaclflag

Задает флаги распространения списка управления доступом (ACL) для задания. Флаги указывают, что вы хотите сохранить сведения о владельце и списке ACL с загружаемым файлом. Например, чтобы сохранить владельца и группу с файлом, установите **флаги** to `OG`.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetAclFlags <Job> <Flags>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Флажки|Укажите одно или несколько из следующих значений флагов:</br>ВЫВОДА Копирование сведений о владельце с помощью файла.</br>МОДУЛЕ Копирование сведений о группе с помощью файла.</br>ЧЕТЫРЕХМЕРНОГО Копирование сведений DACL в файл.</br>-S: копирование сведений SACL с помощью файла.|

## <a name="remarks"></a>Примечания

Параметр Сетаклфлагс используется для сохранения сведений о владельце и списке управления доступом, когда задание скачивает данные из общего ресурса Windows (SMB).

## <a name="BKMK_examples"></a>Примеров

В следующем примере задается флаги распространения списка управления доступом для задания с именем *мидовнлоаджоб* , чтобы сохранить сведения о владельце и группе с скачанными файлами.
```
C:\>bitsadmin /setaclflags myDownloadJob OG
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)