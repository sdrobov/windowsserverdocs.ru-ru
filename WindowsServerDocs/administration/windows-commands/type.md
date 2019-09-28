---
title: type
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c44fe905-a865-4c97-8cc5-fb95fec7d4d5
author: coreyp-at-msft
ms.author: coreyp
manager: dansimp
ms.openlocfilehash: 37f66d54983c002d5d09db5cb255d01635a534de
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392329"
---
# <a name="type"></a>type


В командной оболочке Windows **введите** встроенную команду, которая отображает содержимое текстового файла. Используйте команду **Type** , чтобы просмотреть текстовый файл, не изменяя его.


В PowerShell **введите** встроенный псевдоним для командлета **[Get-Content](https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content)** , который также отображает содержимое файла, но с другим синтаксисом.


Примеры использования этой команды в командной оболочке Windows (cmd. exe) см. в разделе [примеры](#BKMK_examples).

## <a name="syntax"></a>Синтаксис

```
type [<Drive>:][<Path>]<FileName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[@no__t 0Drive >:] [\<Path >] @no__t 2FileName >|Указывает расположение и имя файла или файлов, которые требуется просмотреть. Несколько имен файлов следует разделять пробелами.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Если *имя файла* содержит пробелы, заключите его в кавычки (например, "имя файла с пробелами. txt").
-   При отображении двоичного файла или файла, созданного программой, на экране могут отображаться необычные символы, включая перевода страницы символы и символы escape-последовательности. Эти символы представляют управляющие коды, используемые в двоичном файле. Как правило, Избегайте использования команды **Type** для вывода двоичных файлов.

## <a name="BKMK_examples"></a>Примеров

Чтобы отобразить содержимое файла с именем праздников. Mar, введите:
```
type holiday.mar 
```
Чтобы отобразить содержимое длинного файла с именем праздников. Mar по одному экрану за раз, введите:
```
type holiday.mar | more 
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
