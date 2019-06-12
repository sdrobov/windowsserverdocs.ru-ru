---
title: С помощью команды convert RiprepImage
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88c2b96f-5947-4b64-9dcf-1946b3c013cf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9b41b6dcc52c3e6700d1d18c61eceea8b990ecdf
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440578"
---
# <a name="using-the-convert-riprepimage-command"></a>С помощью команды convert RiprepImage



Преобразование существующего образа подготовки удаленной установки (RIPrep) в формат образа Windows (WIM).

## <a name="syntax"></a>Синтаксис

```
WDSUTIL [Options] /Convert-RIPrepImage /FilePath:<File path and name>
     /DestinationImage
         /FilePath:<File path and name>
         [/Name:<Name>]
         [/Description:<Description>]
         [/InPlace]
         [/Overwrite:{Yes | No | Append}]
```

## <a name="parameters"></a>Параметры

|            Параметр            |                                                                                                                                                                                                                                                                                                               Описание                                                                                                                                                                                                                                                                                                                |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| / FilePath:\<путь к файлу и имя > |                                                                                                                                                                                                       Указывает полный путь к файлу и имя SIF-файл, соответствующий образ RIPrep. Этот файл обычно вызывается Riprep.sif и находится во вложенной папке \Templates папку, содержащую образа RIPrep.                                                                                                                                                                                                       |
|        /DestinationImage        | Задает параметры для конечного изображения, используя следующие параметры.</br>-/FilePath:\<путь к файлу и имя >-задает полный путь к файлу для нового файла. Пример: **C:\Temp\convert.wim**</br>-[/ Name:\<имя >] — Задает отображаемое имя изображения. Если отображаемое имя не указано, будет использоваться отображаемое имя исходного изображения.</br>-[/ Description: \<Описание >] — Задает описание образа.</br>-[/InPlace] — Указывает, что преобразование должно быть выполнено на исходный образ RIPrep, а не на копию исходного изображения, что является поведением по умолчанию.</br>-[/ Overwrite: {Да |

## <a name="BKMK_examples"></a>Примеры

Чтобы преобразовать указанное изображение RIPrep.sif RIPREP.wim, введите следующую команду:
```
WDSUTIL /Convert-RiPrepImage /FilePath:"R:\RemoteInstall\Setup\English
\Images\Win2k3.SP1\i386\Templates\riprep.sif" /DestinationImage
/FilePath:"C:\Temp\RIPREP.wim"
```
Чтобы преобразовать указанное изображение RIPrep.sif RIPREP.wim с указанным именем и описанием и заменяет его с новым файлом, если файл уже существует, введите:
```
WDSUTIL /Verbose /Progress /Convert-RiPrepImage /FilePath:"\\Server
\RemInst\Setup\English\Images\WinXP.SP2\i386\Templates\riprep.sif"
/DestinationImage /FilePath:"\\Server\Share\RIPREP.wim"
/Name:"WindowsXP image" /Description:"Converted RIPREP image of WindowsXP"
/Overwrite:Append
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)