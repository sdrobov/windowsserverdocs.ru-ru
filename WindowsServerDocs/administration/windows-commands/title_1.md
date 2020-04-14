---
title: title
description: Раздел команд Windows для заголовка, который создает заголовок для окна командной строки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c0bbe8bd-201a-4b6c-b617-5d9809881dc8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: aae18e97daaef226443c5f18c6c401a4e2b82b59
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832807"
---
# <a name="title"></a>title

Создает заголовок для окна командной строки.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
title [<String>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Строка \<>|Указывает заголовок окна командной строки.|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

-   Чтобы создать заголовок окна для пакетных программ, включите команду **Title** в начало пакетной программы.
-   После установки заголовка окна его можно сбросить только с помощью команды **Title** .

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере скрипта заголовок окна командной строки изменяется на обновление файлов, а пакетный файл выполняет команду **Copy** . После выполнения команды отображается текст `Files Updated`, а название окна командной строки снова меняется на командную строку.
```
@echo off
title Updating Files
copy \\server\share\*.xls c:\users\common\*.xls
echo Files Updated.
title Command Prompt
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)