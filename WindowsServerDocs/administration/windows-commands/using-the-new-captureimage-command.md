---
title: С помощью команды новый CaptureImage
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 00f15ae7ee1a7ab1ac1f71599d2cae9bb51d921e
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440413"
---
# <a name="using-the-new-captureimage-command"></a>С помощью команды новый CaptureImage



Создает новый образ записи из существующего образа загрузки. Образы записи — это программы, вместо запуска программы установки съемки загрузочные образы, запускающие службы развертывания Windows. При запуске компьютера-образца (который был подготовлен с помощью средства Sysprep) с использованием образа записи мастер создает образ установки компьютера-образца и сохраняет его как файл образа Windows (WIM). Можно также добавить изображение к носитель (такой как компакт-ДИСК, DVD-ДИСК или USB-диск) и затем загрузите компьютер с этого носителя. После создания образа установки, можно добавить изображение к серверу PXE-развертываний. Дополнительные сведения см. в разделе Создание образов ([https://go.microsoft.com/fwlink/?LinkId=115311](https://go.microsoft.com/fwlink/?LinkId=115311)).

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
| [/ Server:\<имя сервера >] |                                                                                                                                       Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.                                                                                                                                        |
|   / Image:\<имя образа >   |                                                                                                                                                                                                         Указывает имя исходного загрузочного образа.                                                                                                                                                                                                         |
|   / Архитектура: {x 86    |                                                                                                                                                                                                                             IA64                                                                                                                                                                                                                             |
| [/ Имя файла: \<Имя файла >] |                                                                                                                                                                            Если изображение не может быть однозначно идентифицируется по имени, необходимо использовать этот параметр, чтобы указать имя файла.                                                                                                                                                                            |
|    /DestinationImage     | Задает параметры для конечного изображения. Необходимо указать параметры, используя следующие параметры:</br>-   /FilePath: \<Путь к файлу и имя > задает полный путь к файлу для нового образа записи.</br>-[/ Name: \<Имя >] — Задает отображаемое имя изображения. Если отображаемое имя не указано, будет использоваться отображаемое имя исходного изображения.</br>-[/ Description: \<Описание >] — Задает описание образа.</br>-[/ Overwrite: {Да |

## <a name="BKMK_examples"></a>Примеры

Чтобы создать образ записи и назовите его WinPECapture.wim, введите следующую команду:
```
WDSUTIL /New-CaptureImage /Image:"WinPE boot image" /Architecture:x86 /DestinationImage /FilePath:"C:\Temp\WinPECapture.wim"
```
Чтобы создать образ записи и применить указанные параметры, введите следующую команду:
```
WDSUTIL /Verbose /Progress /New-CaptureImage /Server:MyWDSServer /Image:"WinPE boot image" /Architecture:x64 /Filename:boot.wim 
/DestinationImage /FilePath:"\\Server\Share\WinPECapture.wim" /Name:"New WinPE image" /Description:"WinPE image with capture utility" /Overwrite:No /UnattendFilePath:"\\Server\Share\WDSCapture.inf"
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)