---
title: Convert-Рипрепимаже
description: Раздел команд Windows для Convert-Рипрепимаже, который преобразует существующий образ подготовки удаленной установки (RIPrep) в формат образа Windows (WIM).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 88c2b96f-5947-4b64-9dcf-1946b3c013cf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 01e33580a6d2da55df15fabde70697c22f894f7c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831817"
---
# <a name="convert-riprepimage"></a>Convert-Рипрепимаже

Преобразует существующий образ подготовки удаленной установки (RIPrep) в формат образа Windows (WIM).

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

### <a name="parameters"></a>Параметры

|            Параметр            |                                                                                                                                                                                                                                                                                                               Описание                                                                                                                                                                                                                                                                                                                |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /FilePath.:\<путь к файлу и имя > |                                                                                                                                                                                                       Указывает полный путь и имя файла. sif, соответствующего образу RIPrep. Этот файл обычно называется RIPrep. sif и находится во вложенной папке \Темплатес папки, содержащей образ RIPrep.                                                                                                                                                                                                       |
|        /дестинатионимаже        | Задает параметры для конечного образа, используя следующие параметры.</br>-/FilePath.:\<путь к файлу и имя > — задает полный путь к файлу для нового файла. Например: **к:\темп\конверт.Вим**</br>-[/Name:\<имя >] — задает отображаемое имя образа. Если отображаемое имя не указано, будет использоваться отображаемое имя исходного изображения.</br>-[/Description: \<Description >] — задает описание образа.</br>-[/Инплаце] — указывает, что преобразование должно осуществляться на исходном образе RIPrep, а не на копии исходного образа, что является поведением по умолчанию.</br>-[/Overwrite: {Да |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы преобразовать указанный образ RIPrep. sif в файл RIPREP. wim, введите:
```
WDSUTIL /Convert-RiPrepImage /FilePath:R:\RemoteInstall\Setup\English
\Images\Win2k3.SP1\i386\Templates\riprep.sif /DestinationImage
/FilePath:C:\Temp\RIPREP.wim
```
Чтобы преобразовать указанный образ RIPrep. sif в файл RIPREP. wim с указанным именем и описанием и перезаписать его новым файлом, если он уже существует, введите:
```
WDSUTIL /Verbose /Progress /Convert-RiPrepImage /FilePath:\\Server
\RemInst\Setup\English\Images\WinXP.SP2\i386\Templates\riprep.sif
/DestinationImage /FilePath:\\Server\Share\RIPREP.wim
/Name:WindowsXP image /Description:Converted RIPREP image of WindowsXP
/Overwrite:Append
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)