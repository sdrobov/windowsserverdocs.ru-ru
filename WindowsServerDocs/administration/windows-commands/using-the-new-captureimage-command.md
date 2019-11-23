---
title: Использование команды New-Каптуреимаже
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2dfd08f0-be59-4715-96e6-c498305873f4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fb48cb76ef99eac51b862a5e1a3d1999a1cfc89d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363048"
---
# <a name="using-the-new-captureimage-command"></a>Использование команды New-Каптуреимаже



Создает новый образ записи из существующего образа загрузки. Образы записи — это загрузочные образы, которые запускают служебную программу записи служб развертывания Windows вместо запуска программы установки. При загрузке компьютера-образца (который был подготовлен с помощью Sysprep) в образ записи мастер создает образ установки эталонного компьютера и сохраняет его как файл образа Windows (WIM). Можно также добавить образ на носитель (например, компакт-диск, DVD-диск или USB-накопитель), а затем загрузить компьютер с этого носителя. После создания образа установки можно добавить образ на сервер для развертывания PXE-загрузки. Дополнительные сведения см. в разделе Создание образов ([https://go.microsoft.com/fwlink/?LinkId=115311](https://go.microsoft.com/fwlink/?LinkId=115311)).

## <a name="syntax"></a>Синтаксис

```
WDSUTIL [Options] /New-CaptureImage [/Server:<Server name>]
     /Image:<Image name>
     /Architecture:{x86 | ia64 | x64}
     [/Filename:<File name>]
     /DestinationImage
        /FilePath:<File path and name>
        [/Name:<Name>]
        [/Description:<Description>]
        [/Overwrite:{Yes | No | Append}]
        [/UnattendFilePath:<File path>]
```

## <a name="parameters"></a>Параметры

|        Параметр         |                                                                                                                                                                                                                         Описание                                                                                                                                                                                                                          |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server:\<имя сервера >] |                                                                                                                                       Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.                                                                                                                                        |
|   /Image:\<имя образа >   |                                                                                                                                                                                                         Указывает имя исходного загрузочного образа.                                                                                                                                                                                                         |
|   /Арчитектуре: {x86    |                                                                                                                                                                                                                             ia64                                                                                                                                                                                                                             |
| [/Филенаме: \<filename >] |                                                                                                                                                                            Если образ не может быть однозначно идентифицирован по имени, необходимо использовать этот параметр, чтобы указать имя файла.                                                                                                                                                                            |
|    /дестинатионимаже     | Задает параметры для конечного образа. Параметры задаются с помощью следующих параметров.</br>-/FilePath.: \<путь к файлу и имя > задает полный путь к файлу для нового образа записи.</br>-[/Name: \<имя >] — задает отображаемое имя образа. Если отображаемое имя не указано, будет использоваться отображаемое имя исходного изображения.</br>-[/Description: \<Description >] — задает описание образа.</br>-[/Overwrite: {Да |

## <a name="BKMK_examples"></a>Примеров

Чтобы создать образ записи и назовите его Винпекаптуре. wim, введите:
```
WDSUTIL /New-CaptureImage /Image:"WinPE boot image" /Architecture:x86 /DestinationImage /FilePath:"C:\Temp\WinPECapture.wim"
```
Чтобы создать образ записи и применить указанные параметры, введите:
```
WDSUTIL /Verbose /Progress /New-CaptureImage /Server:MyWDSServer /Image:"WinPE boot image" /Architecture:x64 /Filename:boot.wim 
/DestinationImage /FilePath:"\\Server\Share\WinPECapture.wim" /Name:"New WinPE image" /Description:"WinPE image with capture utility" /Overwrite:No /UnattendFilePath:"\\Server\Share\WDSCapture.inf"
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)