---
title: compact
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 429b3752-df0a-43a4-a210-df2f3ad03c3b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 068111b293a3eb3987b14744a1bfcf2fde26bced
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59826035"
---
# <a name="compact"></a>compact



Просмотр и изменение режима сжатия для файлов и каталогов в секции NTFS. При использовании без параметров, **compact** отображает состояние сжатия в текущем каталоге и в нем файлы.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
compact [/c | /u] [/s[:<Dir>]] [/a] [/i] [/f] [/q] [<FileName>[...]]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/c|Сжимает заданный каталог или файл.|
|/u|Распаковывает указанный каталог или файл.|
|/s [:\<Dir >]|Применяет **compact** команду ко всем подкаталогам в указанном каталоге (или текущего каталога, если ничего не указано).|
|/a|Отображение скрытых или системных файлов.|
|/i|Игнорирует ошибки.|
|/f|Принудительно или распаковка указанного каталога или файла. **/f** используется при наличии файла, когда операция была прервана в результате сбоя системы. Чтобы принудительно запустить файл будет сжат в полном объеме, используйте **/c** и **/f** параметры и укажите частично сжатый файл.|
|/q|Сообщает только наиболее важные сведения.|
|\<Имя файла >|Указывает файл или каталог. Можно использовать несколько имен файлов и **&#42;** и **?** подстановочные знаки.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   **Compact** параметр командной строки версии средства сжатия файловой системы NTFS. Состояние сжатия каталога, указывает ли файлы будут сжаты автоматически в том случае, когда они добавляются в каталог. Установка состояния сжатия каталога не изменяет состояние сжатия файлов, которые уже находятся в каталоге.
-   Нельзя использовать **compact** для чтения, записи или подключения томов, которые были сжаты с помощью разуплотнять.
-   Нельзя использовать **compact** для сжатия в таблице размещения файлов (FAT) или FAT32 секций.

## <a name="BKMK_examples"></a>Примеры

Чтобы задать состояние сжатия текущий каталог, его подкаталоги и файлы, введите следующую команду:
```
compact /c /s 
```
Чтобы задать состояние сжатия файлы и подкаталоги текущего каталога, без изменения состояния самого текущего каталога, введите следующую команду:
```
compact /c /s *.*
```
Для сжатия на томе, корневом каталоге тома, введите следующую команду:
```
compact /c /i /s:\
```

> [!NOTE]
> Этот пример задает состояние сжатия всех каталогов (включая корневой каталог тома) и сжимает каждый файл на томе. **/I** параметр предотвращает прерывание процесса сжатия сообщений об ошибках.

Чтобы сжать все файлы с расширением имени файла .bmp в каталоге \Tmp и его подкаталогах \Tmp, не изменяя атрибута каталоги, введите следующую команду:
```
compact /c /s:\tmp *.bmp
```
Для принудительного завершения сжатия файла Zebra.bmp, который частично была сжата во время сбоя системы, введите следующую команду:
```
compact /c /f zebra.bmp
```
Чтобы удалить атрибута в каталоге C:\Tmp, не изменяя состояние сжатия файлов в этом каталоге, введите следующую команду:
```
compact /u c:\tmp
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)