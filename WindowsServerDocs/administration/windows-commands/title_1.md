---
title: title
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0bbe8bd-201a-4b6c-b617-5d9809881dc8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d1d1ea70849c3beb4503edfdaa5116384c14a2fd
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59848505"
---
# <a name="title"></a>title



Создает заголовок окна командной строки.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
title [<String>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<строка >|Указывает заголовок окна командной строки.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Чтобы создать заголовок окна для пакетных программ, включите **title** команду в начале программы пакетной службы.
-   Настроив заголовок окна, ее можно восстановить только с помощью **title** команды.

## <a name="BKMK_examples"></a>Примеры

В следующем примере скрипта, заголовок окна командной строки изменяется на «Обновление файлов», хотя пакетный файл выполняет **копирования** команды. После выполнения команды, текст `Files Updated` отображается, и заголовок окна командной строки изменяется обратно на «Командная строка».
```
@echo off
title Updating Files
copy \\server\share\*.xls c:\users\common\*.xls
echo Files Updated.
title Command Prompt
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)