---
title: title
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 42094e0f1231fee5ac9ef0ec9184ba685c8846b1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71385794"
---
# <a name="title"></a>title



Создает заголовок для окна командной строки.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
title [<String>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0String >|Указывает заголовок окна командной строки.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Чтобы создать заголовок окна для пакетных программ, включите команду **Title** в начало пакетной программы.
-   После установки заголовка окна его можно сбросить только с помощью команды **Title** .

## <a name="BKMK_examples"></a>Примеров

В следующем примере скрипта заголовок окна командной строки изменится на «обновление файлов», а пакетный файл выполняет команду **Copy** . После выполнения команды отображается текст `Files Updated`, а название окна командной строки снова меняется на «Командная строка».
```
@echo off
title Updating Files
copy \\server\share\*.xls c:\users\common\*.xls
echo Files Updated.
title Command Prompt
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)