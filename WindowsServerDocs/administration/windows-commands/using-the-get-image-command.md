---
title: Get-Image
description: Справочный раздел по Get-Image, который получает сведения о изображении.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0ecaa999-72ad-4191-adb5-a418de42a001
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 04cc7b8d90415e32be4103ef6c7f7b709c3550c3
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719924"
---
# <a name="get-image"></a>Get-Image

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения о изображении.

## <a name="syntax"></a>Синтаксис
для загрузочных образов:
```
wdsutil [Options] /Get-Imagmedia:<Image name> [/Server:<Server name>mediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>]
```
для образов установки:
```
wdsutil [Options] /Get-Imagmedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image group name>] [/Filename:<File name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носител<Image name>|Указывает имя образа.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: {Загрузка &#124; установка}|Указывает тип изображения.|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Указывает архитектуру образа. Так как для образов загрузки в разных архитектурах можно использовать одно и то же имя образа, задание значения архитектуры гарантирует, что будет возвращен правильный образ.|
|[/Филенаме:<File name>]|Если образ не может быть однозначно идентифицирован по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|\Медиаграуп:<Image group name>]|Указывает группу образов, содержащую образ. Если группа образов не указана и на сервере существует только одна группа образов, будет использоваться эта группа. Если на сервере существует несколько групп образов, необходимо использовать этот параметр, чтобы указать группу образов.|
## <a name="examples"></a>Примеры
Чтобы получить сведения о загрузочном образе, введите один из следующих элементов:
```
wdsutil /Get-Imagmedia:WinPE boot imagemediatype:Boot /Architecture:x86
wdsutil /verbose /Get-Imagmedia:WinPE boot image /Server:MyWDSServemediatype:Boot /Architecture:x86 /Filename:boot.wim
```
Чтобы получить сведения о образе установки, введите одно из следующих действий:
```
wdsutil /Get-Imagmedia:Windows Vista with Officemediatype:Install
wdsutil /verbose /Get-Imagmedia:Windows Vista with Office /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ](command-line-syntax-key.md)
синтаксиса командной строки[с помощью команды Add-](using-the-add-image-command.md)
Image с помощью команды "[Копировать](using-the-copy-image-command.md)
изображение" с помощью команды "[Export](using-the-export-image-command.md)
-Image" с помощью команды[Remove](using-the-remove-image-command.md)
-Image с помощью команды[Replace](using-the-replace-image-command.md)
-Image[: Set-Image](subcommand-set-image.md)
