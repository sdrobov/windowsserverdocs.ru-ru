---
title: С помощью команды remove образа
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ce5e2384-2264-4b22-92af-74eec8c10ae0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2aaf7d63d858045f9dd5df399c5f3f92b038bc2e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59846705"
---
# <a name="using-the-remove-image-command"></a>С помощью команды remove образа

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет изображение с сервера.
## <a name="syntax"></a>Синтаксис
для образов загрузки:
```
wdsutil [Options] /remove-Imagmedia:<Image name> [/Server:<Server name>mediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<Filename>]
```
для образов установки:
```
wdsutil [Options] /remove-Imagmedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image group name>] [/Filename:<Filename>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
мультимедиа:<Image name>|Задает имя образа.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
Тип носителя: {загрузки &#124; установить}|Задает тип изображения.|
|/ Архитектура: {x86 &#124; ia64 &#124; x64}|Задает архитектуру изображения. Так как это может быть то же имя образа для различных загрузочных образов в различных архитектур, указав значение архитектуры гарантирует, что правильный образ будет удален.|
|\mediaGroup:<Image group name>]|Указывает группу образов, содержащий изображение. Если указано имя группы не образа и только один образ группа существует на сервере, будет использоваться этой группы образов. Если существует более одной группы образов, необходимо использовать этот параметр, чтобы указать группу образов.|
|[/ Filename:<File name>]|Если изображение не может быть однозначно идентифицируется по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
## <a name="BKMK_examples"></a>Примеры
Чтобы удалить образ загрузки, введите следующую команду:
```
wdsutil /remove-Imagmedia:"WinPE Boot Imagemediatype:Boot /Architecture:x86
```
```
wdsutil /verbose /remove-Imagmedia:"WinPE Boot Image" /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filename:boot.wim
```
Чтобы удалить образ установки, введите следующую команду:
```
wdsutil /remove-Imagmedia:"Windows Vista with Officemediatype:Install
```
```
wdsutil /verbose /remove-Imagmedia:"Windows Vista with Office" /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add образа](using-the-add-image-command.md)
[с помощью команды копирования образа](using-the-copy-image-command.md)
[Using Команда export-Image](using-the-export-image-command.md)
[с помощью команды get образа](using-the-get-image-command.md)
[с помощью команды заменить изображение](using-the-replace-image-command.md) 
 [ Подкоманда: set-Image](subcommand-set-image.md)
