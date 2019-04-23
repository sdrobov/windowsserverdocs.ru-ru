---
title: С помощью команды новый DiscoverImage
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ede9fbbb-0bba-4309-8c21-3cc13e1dc3cd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1212571fc07b912ab9fa3344b973ce5a25085d86
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59835775"
---
# <a name="using-the-new-discoverimage-command"></a>С помощью команды новый DiscoverImage



Создает новый образ обнаружения из существующего образа загрузки. Узнайте, что образы, загрузочные образы, которые принудительно передают программы Setup.exe для запуска в режиме служб развертывания Windows и затем обнаружить сервер служб развертывания Windows. Обычно эти образы используются для развертывания образов на компьютеры, которые не может загружаться с PXE. Дополнительные сведения см. в разделе Создание образов ([https://go.microsoft.com/fwlink/?LinkId=115311](https://go.microsoft.com/fwlink/?LinkId=115311)).

## <a name="syntax"></a>Синтаксис

```
WDSUTIL [Options] /New-DiscoverImage [/Server:<Server name>]
     /Image:<Image name>
     /Architecture:{x86 | ia64 | x64}
     [/Filename:<File name>]
     /DestinationImage
         /FilePath:<File path and name>
         [/Name:<Name>]
         [/Description:<Description>]
         [/WDSServer:<Server name>]
         [/Overwrite:{Yes | No | Append}]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[/ Server:\<имя сервера >]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|/ Image:\<имя образа >|Указывает имя исходного загрузочного образа.|
|/ Архитектура: {x86 | IA64 | x64}|Задает архитектуру изображения должны быть возвращены. Так как это может быть то же имя образа для различных загрузочных образов в различных архитектур, указав значение архитектуры гарантирует, что WDSUTIL возвращает правильное изображение.|
|[/ Filename:\<имя файла >]|Если изображение не может быть однозначно идентифицируется по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|/DestinationImage|Задает параметры для конечного изображения. Можно указать параметры, используя следующие параметры:</br>-/FilePath: < путь к файлу и имя > - задает полный путь к файлу для нового образа.</br>-[/ Name:\<имя >] — Задает отображаемое имя изображения. Если отображаемое имя не указано, будет использоваться отображаемое имя исходного изображения.</br>-[/ Description: \<Описание >] — Задает описание образа.</br>-[/ WDSServer: \<Имя сервера >] — Задает имя сервера, все клиенты, загружается из указанного изображения следует обратиться к скачиванию образа установки. По умолчанию все клиенты, загрузить этот образ будет обнаруживать допустимый сервер служб развертывания Windows. С помощью этого параметра обходит функции обнаружения и принудительно загружаемый клиентский для связи с сервером.</br>-[/ Overwrite: {Да | Нет | Append}] — определяет, является ли файл, указанный в **/DestinationImage** следует перезаписать, если другой файл с таким именем уже существует в /FilePath. **Да** перезаписывает существующий файл. **Не** (по умолчанию), приводит к ошибке в случае, если другой файл с таким именем уже существует. **Добавление** присоединяет созданное изображение как новый образ в существующий WIM-файл.|

## <a name="BKMK_examples"></a>Примеры

Чтобы создать образ обнаружения из загрузочного образа и назовите его WinPEDiscover.wim, введите следующую команду:
```
WDSUTIL /New-DiscoverImage /Image:"WinPE boot image" /Architecture:x86 /DestinationImage /FilePath:"C:\Temp\WinPEDiscover.wim"
```
Чтобы создать образ обнаружения из загрузочного образа и назовите его WinPEDiscover.wim с указанными параметрами, введите следующую команду:
```
WDSUTIL /Verbose /Progress /New-DiscoverImage /Server:MyWDSServer
/Image:"WinPE boot image" /Architecture:x64 /Filename:boot.wim /DestinationImage /FilePath:"\\Server\Share\WinPEDiscover.wim" 
/Name:"New WinPE image" /Description:"WinPE image for WDS Client discovery" /Overwrite:No
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)