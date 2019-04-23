---
title: С помощью команды get-файл изображения
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 6bbe5ece95d1f9821a27b96e56bc34576a0f5f33
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59827625"
---
# <a name="using-the-get-imagefile-command"></a>С помощью команды get-файл изображения



Извлекает сведения об образах, содержащихся в файле образа Windows (WIM).

## <a name="syntax"></a>Синтаксис

```
WDSUTIL [Options] /Get-ImageFile /ImageFile:<wim file path> [/Detailed]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/ Файл изображения:\<путь к файлу WIM >|Указывает полный путь к файлу и имя WIM-файле.|
|[/ Подробные]|Возвращает все метаданные изображения из каждого изображения. Если данный параметр не указан, по умолчанию задается для возврата только имя образа, описание и имя файла.|

## <a name="BKMK_examples"></a>Примеры

Чтобы просмотреть сведения об образе, введите следующую команду:
```
WDSUTIL /Get-ImageFile /ImageFile:"C:\temp\install.wim"
```
Чтобы просмотреть подробные сведения, введите:
```
WDSUTIL /Verbose /Get-ImageFile /ImageFile:"\\Server\Share\My Folder \install.wim" /Detailed
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)