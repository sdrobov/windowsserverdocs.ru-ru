---
title: Get-ImageFile
description: Раздел команд Windows для Get-ImageFile, который извлекает сведения об образах, содержащихся в WIM-файле образа Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e1e296fb-20cf-4a60-9db4-4cbac7d4dab5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ef1cf2b9eec6739690d286c32d26dd84b07e348c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830997"
---
# <a name="get-imagefile"></a>Get-ImageFile

Извлекает сведения об образах, содержащихся в WIM-файле образа Windows.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL [Options] /Get-ImageFile /ImageFile:<wim file path> [/Detailed]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/Имажефиле:\<путь к WIM-файлу >|Указывает полный путь и имя файла WIM.|
|[/Детаилед]|Возвращает все метаданные изображения из каждого изображения. Если этот параметр не используется, поведение по умолчанию — возврат только имени, описания и имени файла изображения.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы просмотреть сведения об образе, введите:
```
WDSUTIL /Get-ImageFile /ImageFile:C:\temp\install.wim
```
Чтобы просмотреть подробные сведения, введите:
```
WDSUTIL /Verbose /Get-ImageFile /ImageFile:\\Server\Share\My Folder \install.wim /Detailed
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)