---
title: Remove-Image
description: Справочный раздел по Remove-Image, который удаляет образ с сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ce5e2384-2264-4b22-92af-74eec8c10ae0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 770c8487bcfe0cba28bffcd32a05285d904ba21c
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720363"
---
# <a name="remove-image"></a>Remove-Image

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет образ с сервера.

## <a name="syntax"></a>Синтаксис
для загрузочных образов:
```
wdsutil [Options] /remove-Imagmedia:<Image name> [/Server:<Server name>mediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<Filename>]
```
для образов установки:
```
wdsutil [Options] /remove-Imagmedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image group name>] [/Filename:<Filename>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носител<Image name>|Указывает имя образа.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
mediaType: {Загрузка &#124; установка}|Указывает тип изображения.|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Указывает архитектуру образа. Так как в разных архитектурах для разных образов загрузки можно использовать одинаковое имя образа, задание значения архитектуры гарантирует, что будет удален нужный образ.|
|\Медиаграуп:<Image group name>]|Указывает группу образов, содержащую образ. Если имя группы образов не указано и на сервере существует только одна группа образов, будет использоваться эта группа образов. Если существует несколько групп образов, необходимо использовать этот параметр, чтобы указать группу образов.|
|[/Филенаме:<File name>]|Если образ не может быть однозначно идентифицирован по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
## <a name="examples"></a>Примеры
Чтобы удалить загрузочный образ, введите:
```
wdsutil /remove-Imagmedia:WinPE Boot Imagemediatype:Boot /Architecture:x86
```
```
wdsutil /verbose /remove-Imagmedia:WinPE Boot Image /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filename:boot.wim
```
Чтобы удалить образ установки, введите:
```
wdsutil /remove-Imagmedia:Windows Vista with Officemediatype:Install
```
```
wdsutil /verbose /remove-Imagmedia:Windows Vista with Office /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Синтаксис](command-line-syntax-key.md)
командной строки[с помощью команды Add-](using-the-add-image-command.md)
Image с помощью команды "[Копировать](using-the-copy-image-command.md)
изображение" с помощью команды "[Export](using-the-export-image-command.md)

-Image" с[помощью команды "](using-the-get-image-command.md)[Replace](using-the-replace-image-command.md)
/Image" с командой "заменить на изображение[": Set-Image](subcommand-set-image.md)
