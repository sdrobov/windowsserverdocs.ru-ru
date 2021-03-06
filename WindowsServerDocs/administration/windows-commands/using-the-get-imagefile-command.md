---
title: Get-ImageFile
description: Справочная статья по Get-ImageFile, которая получает сведения об образах, содержащихся в WIM-файле образа Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e1e296fb-20cf-4a60-9db4-4cbac7d4dab5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 127b5282b74020f002c7ccc55663fc2571584582
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932221"
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
|Изображения\<WIM file path>|Указывает полный путь и имя файла WIM.|
|[/Детаилед]|Возвращает все метаданные изображения из каждого изображения. Если этот параметр не используется, поведение по умолчанию — возврат только имени, описания и имени файла изображения.|

## <a name="examples"></a>Примеры

Чтобы просмотреть сведения об образе, введите:
```
WDSUTIL /Get-ImageFile /ImageFile:C:\temp\install.wim
```
Чтобы просмотреть подробные сведения, введите:
```
WDSUTIL /Verbose /Get-ImageFile /ImageFile:\\Server\Share\My Folder \install.wim /Detailed
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)