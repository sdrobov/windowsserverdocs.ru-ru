---
title: С помощью команды add-ImageDriverPackage
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6c2a4833-6427-47f8-9ffb-20b3786cb406
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 38d6c032f347f9945701f17b9289f3e3ff474031
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440621"
---
# <a name="using-the-add-imagedriverpackage-command"></a>С помощью команды add-ImageDriverPackage

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет пакет драйверов, который находится в хранилище драйверов на существующий образ загрузки на сервере. Версия образа должна быть Windows 7 или Windows Server 2008 R2 или более поздней версии.
## <a name="syntax"></a>Синтаксис
```
wdsutil /add-ImageDriverPackage [/Server:<Server name>media:<Image namemediatype:Boot /Architecture:{x86 | ia64 | x64} 
```
```
[/Filename:<File name>] {/DriverPackage:<Package Name> | /PackageId:<ID>}
```
## <a name="parameters"></a>Параметры

|                 Параметр                  |                                                                                                                                                                                                            Описание                                                                                                                                                                                                             |
|--------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           [/ Server:<Server name>           |                                                                                                                                               Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя. Если имя сервера не указан, используется локальный сервер.                                                                                                                                                |
|             мультимедиа:<Image name>             |                                                                                                                                                                                       Указывает имя образа, чтобы добавить драйвер.                                                                                                                                                                                        |
|               MediaType:Boot               |                                                                                                                                                                Задает тип изображения, чтобы добавить драйвер. Пакеты драйверов могут добавляться только в образы загрузки.                                                                                                                                                                 |
| / Архитектура: {x86 &#124; ia64 &#124; x64} |                                                                                                       Задает архитектуру загрузочного образа. Так как это может быть то же имя образа для загрузочных образов в различных архитектур, следует указать архитектуры, чтобы убедиться, что используется правильный образ.                                                                                                        |
|           / Filename:<File name>]           |                                                                                                                                                        Задает имя файла. Если изображение не может быть однозначно идентифицируется по имени, необходимо указать имя файла.                                                                                                                                                        |
|           [/ DriverPackage:<Name>           |                                                                                                                                                                                   Указывает имя пакета драйверов, чтобы добавить к образу.                                                                                                                                                                                    |
|             [/ PackageId:<ID>]              | Указывает идентификатор службы развертывания Windows из пакета драйверов. Необходимо указать этот параметр, если пакет драйверов не может быть однозначно идентифицируется по имени. Чтобы найти идентификатор пакета, щелкните группу драйверов, в который входит пакет (или **все пакеты** узла), щелкните правой кнопкой мыши пакет и нажмите кнопку **свойства**. Идентификатор пакета указан на **Общие** вкладки. Например: {DD098D20-1850-4fc8-8E35-EA24A1BEFF5E}. |

## <a name="BKMK_examples"></a>Примеры
Чтобы добавить пакет драйвера к образу загрузки, введите одно из следующих:
```
wdsutil /add-ImageDriverPackagmedia:"WinPE Boot Imagemediatype:Boot /Architecture:x86 /DriverPackage:XYZ
```
```
wdsutil /verbose /add-ImageDriverPackagmedia:"WinPE Boot Image" /Server:MyWDSServemediatype:Boot /Architecture:x64 /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add-ImageDriverPackages](using-the-add-imagedriverpackages-command.md)
