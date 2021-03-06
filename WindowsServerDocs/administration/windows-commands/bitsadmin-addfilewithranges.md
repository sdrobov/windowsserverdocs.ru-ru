---
title: bitsadmin addfilewithranges
description: Справочная статья по команде битсадмин аддфилевисранжес, которая добавляет файл к указанному заданию. Служба BITS загружает указанные диапазоны из удаленного файла.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: df0ce0bf-dff1-4a48-a16f-fd2f4d5f7189
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5439cfb8330cda7c51150c720fe45faccca8e1ec
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927072"
---
# <a name="bitsadmin-addfilewithranges"></a>bitsadmin addfilewithranges

Добавляет файл в указанное задание. Служба BITS загружает указанные диапазоны из удаленного файла. Этот параметр допустим только для заданий скачивания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /addfilewithranges <job> <remoteURL> <localname> <rangelist>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| ремотеурл | URL-адрес файла на сервере. |
| localname | Имя файла на локальном компьютере. Должен содержать абсолютный путь к файлу. |
| ранжелист | Разделенный запятыми список пар "смещение: длина". Используйте двоеточие, чтобы разделить значение смещения от значения длины. Например, значение указывает, что `0:100,2000:100,5000:eof` бит передает 100 байт со смещения 0, 100 байт из смещения 2000, а остальные байт от смещения 5000 до конца файла. |

## <a name="remarks"></a>Комментарии

- Токен **EOF** — это допустимое значение длины в пределах пар смещения и длины в `<rangelist>` . Он указывает службе выполнить чтение до конца указанного файла.

- Команда завершится `addfilewithranges` ошибкой с кодом ошибки 0x8020002c, если диапазон нулевой длины указан вместе с другим диапазоном с тем же смещением, например:

    `c:\bits>bitsadmin /addfilewithranges j2 http://bitsdc/dload/1k.zip c:\1k.zip 100:0,100:5`

    **Сообщение об ошибке:** Не удалось добавить файл в задание — 0x8020002c. Список диапазонов байтов содержит несколько перекрывающихся диапазонов, которые не поддерживаются.

    **Обходной путь:** Сначала не указывайте диапазон нулевой длины. Например, используйте `bitsadmin /addfilewithranges j2 http://bitsdc/dload/1k.zip c:\1k.zip 100:5,100:0`.

## <a name="examples"></a>Примеры

Для перемещения 100 байт со смещения 0, 100 байт с offset 2000 и оставшихся байтов от смещения 5000 до конца файла:

```
bitsadmin /addfilewithranges http://downloadsrv/10mb.zip c:\10mb.zip 0:100,2000:100,5000:eof
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
