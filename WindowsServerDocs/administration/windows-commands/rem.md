---
title: rem
description: Справочная статья для * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1a45b585-a83c-4ff6-badd-ff40f34cec23
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5161a3ba0904396f29b7c567e3a16da5f95e5271
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933500"
---
# <a name="rem"></a>rem



Записывает комментарии (примечания) в пакетном файле или CONFIG.SYS. Если комментарий не указан, **REM** добавляется пробел по вертикали.



## <a name="syntax"></a>Синтаксис

```
rem [<Comment>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Comment>|Указывает строку символов, включаемую в качестве комментария.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Комментарии

-   Команда **REM** не отображает комментарии на экране. Для отображения комментариев на экране необходимо использовать команду **echo on** в пакетном или CONFIG.SYSном файле.
-   **<** В комментариях пакетного файла нельзя использовать символ перенаправления (или **>** ) или pipe ( **|** ).
-   Несмотря на то, что можно использовать **REM** без комментариев для добавления вертикальных пробелов в пакетный файл, можно также использовать пустые строки. При обработке пакетной программы пустые строки игнорируются.

## <a name="examples"></a>Примеры

Для отображения пакетного файла, который использует примечания для комментариев и вертикального пробела:
```
@echo off
rem  This batch program formats and checks new disks.
rem  It is named Checknew.bat.
rem
rem echo Insert new disk in Drive B.
pause
format b: /v chkdsk b:
```
Чтобы включить пояснительный комментарий перед командой **Prompt** в файле CONFIG.SYS, добавьте следующие строки для CONFIG.SYS.
```
rem Set prompt to indicate current directory
prompt $p$g
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)