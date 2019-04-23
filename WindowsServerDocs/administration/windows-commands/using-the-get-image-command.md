---
title: С помощью команды get образа
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ecaa999-72ad-4191-adb5-a418de42a001
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b78f4ed9352c21bf6de19136a625a4f4fe7ac5f5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59877445"
---
# <a name="using-the-get-image-command"></a>С помощью команды get образа

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения об образе.
## <a name="syntax"></a>Синтаксис
для образов загрузки:
```
wdsutil [Options] /Get-Imagmedia:<Image name> [/Server:<Server name>mediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>]
```
для образов установки:
```
wdsutil [Options] /Get-Imagmedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image group name>] [/Filename:<File name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
мультимедиа:<Image name>|Задает имя образа.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
Тип носителя: {загрузки &#124; установить}|Задает тип изображения.|
|/ Архитектура: {x86 &#124; ia64 &#124; x64}|Задает архитектуру изображения. Так как это может быть то же имя образа для загрузочных образов в различных архитектур, значение архитектуры гарантирует возврат нужного образа.|
|[/ Filename:<File name>]|Если изображение не может быть однозначно идентифицируется по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|\mediaGroup:<Image group name>]|Указывает группу образов, содержащий изображение. Если группа образа не указана, и только один образ группа существует на сервере, будет использоваться этой группы. Если на сервере существует более одной группы образов, этот параметр следует использовать для указания группы образов.|
## <a name="BKMK_examples"></a>Примеры
Чтобы получить информацию о загрузочного образа, введите одно из следующих:
```
wdsutil /Get-Imagmedia:"WinPE boot imagemediatype:Boot /Architecture:x86
wdsutil /verbose /Get-Imagmedia:"WinPE boot image" /Server:MyWDSServemediatype:Boot /Architecture:x86 /Filename:boot.wim
```
Чтобы получить информацию о образа установки, введите одно из следующих:
```
wdsutil /Get-Imagmedia:"Windows Vista with Officemediatype:Install
wdsutil /verbose /Get-Imagmedia:"Windows Vista with Office" /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add образа](using-the-add-image-command.md)
[с помощью команды копирования образа](using-the-copy-image-command.md)
[Using Команда export-Image](using-the-export-image-command.md)
[с помощью команды remove образа](using-the-remove-image-command.md)
[с помощью команды заменить изображение](using-the-replace-image-command.md) 
 [Подкоманда: set-Image](subcommand-set-image.md)
