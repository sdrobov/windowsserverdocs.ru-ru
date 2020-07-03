---
title: title
description: Справочная статья для Title, которая создает заголовок для окна командной строки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c0bbe8bd-201a-4b6c-b617-5d9809881dc8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 732a0de30b9495e6281248120d2a90f85734ad8b
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85930058"
---
# <a name="title"></a>title

Создает заголовок для окна командной строки.



## <a name="syntax"></a>Синтаксис

```
title [<String>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<String>|Указывает заголовок окна командной строки.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Комментарии

-   Чтобы создать заголовок окна для пакетных программ, включите команду **Title** в начало пакетной программы.
-   После установки заголовка окна его можно сбросить только с помощью команды **Title** .

## <a name="examples"></a>Примеры

В следующем примере скрипта заголовок окна командной строки изменяется на обновление файлов, а пакетный файл выполняет команду **Copy** . После выполнения команды `Files Updated` отображается текст, а название окна командной строки снова меняется на командную строку.
```
@echo off
title Updating Files
copy \\server\share\*.xls c:\users\common\*.xls
echo Files Updated.
title Command Prompt
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)