---
title: type
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c44fe905-a865-4c97-8cc5-fb95fec7d4d5
author: coreyp-at-msft
ms.author: coreyp
manager: dansimp
ms.openlocfilehash: 4ceb7365d34a2aeca21d1a699730a589f98fd549
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59887405"
---
# <a name="type"></a>type


В командной строке Windows **тип** — это встроенный в команду, которая отображает содержимое текстового файла. Используйте **тип** команду для просмотра в текстовый файл, не изменяя его.


В PowerShell **тип** — встроенный псевдоним для **[Get-Content](https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content)** который также отображает содержимое файла, но с другой синтаксис.


Примеры для использования этой команды интерпретатора команд Windows (Cmd.exe), см. в разделе [примеры](#BKMK_examples).

## <a name="syntax"></a>Синтаксис

```
type [<Drive>:][<Path>]<FileName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[\<Диска >:] [\<путь >]\<имя файла >|Указывает расположение и имя файла или файлов, которые вы хотите просмотреть. Несколько имен файлов разделяются пробелами.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Если *FileName* содержит пробелы, заключите его в кавычки (например, «файл имя содержащего Spaces.txt»).
-   Если отобразить двоичный файл или файл, который создается программой, на экране, включая символы перевода страницы и escape последовательности символов может появиться странные символы. Эти символы представляют собой управляющие коды, которые используются в двоичный файл. Как правило, избегать использования **тип** команду, чтобы отобразить двоичные файлы.

## <a name="BKMK_examples"></a>Примеры

Чтобы просмотреть содержимое файла с именем Holiday.mar, введите:
```
type holiday.mar 
```
Чтобы отобразить содержимое длительных файл с именем Holiday.mar один экран за раз, введите следующую команду:
```
type holiday.mar | more 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
