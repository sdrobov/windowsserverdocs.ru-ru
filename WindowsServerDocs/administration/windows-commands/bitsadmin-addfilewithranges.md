---
title: bitsadmin addfilewithranges
description: Раздел Windows команды для **bitsadmin addfilewithranges** -добавляет файл к указанному заданию. BITS загружает указанных диапазонов из удаленного файла.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df0ce0bf-dff1-4a48-a16f-fd2f4d5f7189
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d5e1e4f8af9117928f9ab044d29e65f57aa5a119
ms.sourcegitcommit: 6ef4986391607bb28593852d06cc6645e548a4b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66811277"
---
# <a name="bitsadmin-addfilewithranges"></a>bitsadmin addfilewithranges

Добавляет файл к указанному заданию. BITS загружает указанных диапазонов из удаленного файла. Этот параметр допустим только для заданий загрузки.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /AddFileWithRanges <Job> <RemoteURL> <LocalName> <RangeList>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|RemoteURL|*RemoteURL* URL-адрес файла на сервере.|
|LocalName|*LocalName* имя файла на локальном компьютере. *LocalName* должен содержать абсолютный путь к файлу.|
|RangeList|*RangeList* — это разделенный запятыми список пар смещение: длина. Для разделения значение смещения из значения длины, используйте двоеточия. Например, значение `0:100,2000:100,5000:eof` указывает BITS для передачи 100 байт по смещению 0, 100 байт по смещению 2000, а оставшиеся байты от смещения 5000 в конец файла.|

## <a name="more-information"></a>Дополнительные сведения

-   Токен **eof** представляет собой значение допустимую длину в пары смещения и длины в  *\<RangeList >* . Он указывает службе для чтения в конец указанного файла.
-   Обратите внимание на то, что AddFileWithRanges завершится ошибкой с кодом ошибки 0x8020002c при нулевой длины диапазон указан вместе с другой диапазон с тем же смещением, таких как: C:\bits > bitsadmin /addfilewithranges j2 http://bitsdc/dload/1k.zip c:\1k.zip 100:0, 100:5

    Сообщение об ошибке: Не удалось добавить файл задания — 0x8020002c. Список диапазонов байтов содержит некоторые перекрывающиеся диапазоны, которые не поддерживаются.

    Инструкции по решению: сначала не указывайте диапазон нулевой длины. Например: bitsadmin /addfilewithranges j2 http://bitsdc/dload/1k.zip c:\1k.zip 100:5, 100:0.

## <a name="examples"></a>Примеры

Следующий пример указывает BITS для передачи 100 байт по смещению 0, 100 байт из смещения 2000, а оставшиеся байты от смещения 5000 в конец файла.

```
C:\>bitsadmin /addfilewithranges http://downloadsrv/10mb.zip c:\10mb.zip "0:100,2000:100,5000:eof"
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)