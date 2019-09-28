---
title: Использование команды Get-ImageFile
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e1e296fb-20cf-4a60-9db4-4cbac7d4dab5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6c8136585e04caca02ab16c7b4ca11a825cf400d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392136"
---
# <a name="using-the-get-imagefile-command"></a>Использование команды Get-ImageFile



Извлекает сведения об образах, содержащихся в WIM-файле образа Windows.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL [Options] /Get-ImageFile /ImageFile:<wim file path> [/Detailed]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/Имажефиле: \<WIM путь к файлу >|Указывает полный путь и имя файла WIM.|
|[/Детаилед]|Возвращает все метаданные изображения из каждого изображения. Если этот параметр не используется, поведение по умолчанию — возврат только имени, описания и имени файла изображения.|

## <a name="BKMK_examples"></a>Примеров

Чтобы просмотреть сведения об образе, введите:
```
WDSUTIL /Get-ImageFile /ImageFile:"C:\temp\install.wim"
```
Чтобы просмотреть подробные сведения, введите:
```
WDSUTIL /Verbose /Get-ImageFile /ImageFile:"\\Server\Share\My Folder \install.wim" /Detailed
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)