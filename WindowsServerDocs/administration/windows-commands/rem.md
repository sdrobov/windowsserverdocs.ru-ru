---
title: rem
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1a45b585-a83c-4ff6-badd-ff40f34cec23
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d115548f15ff45087a771458062da8a3ef919eb3
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722465"
---
# <a name="rem"></a>rem



Записывает комментарии (примечания) в пакетном файле или конфигурации. Представления. Если комментарий не указан, **REM** добавляется пробел по вертикали.



## <a name="syntax"></a>Синтаксис

```
rem [<Comment>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<> комментариев|Указывает строку символов, включаемую в качестве комментария.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Команда **REM** не отображает комментарии на экране. Необходимо использовать команду **echo on** в пакете или конфигурации. SYS для отображения комментариев на экране.
-   В комментариях пакетного файла нельзя использовать символ**<** перенаправления (или **>**)**|** или pipe ().
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
Чтобы включить пояснительный комментарий перед командой **Prompt** в файле конфигурации. SYS, добавьте следующие строки в файл конфигурации. ПРЕДСТАВЛЕНИЯ
```
rem Set prompt to indicate current directory
prompt $p$g
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)