---
title: rem
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1a45b585-a83c-4ff6-badd-ff40f34cec23
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 94428e6d5ec6fdb482a5d0d15bd1120e45ffea80
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836117"
---
# <a name="rem"></a>rem



Записывает комментарии (примечания) в пакетном файле или конфигурации. Представления. Если комментарий не указан, **REM** добавляется пробел по вертикали.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
rem [<Comment>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<комментарий >|Указывает строку символов, включаемую в качестве комментария.|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

-   Команда **REM** не отображает комментарии на экране. Необходимо использовать команду **echo on** в пакете или конфигурации. SYS для отображения комментариев на экране.
-   В комментариях пакетного файла нельзя использовать символ перенаправления ( **<** или **>** ) или канал ( **|** ).
-   Несмотря на то, что можно использовать **REM** без комментариев для добавления вертикальных пробелов в пакетный файл, можно также использовать пустые строки. При обработке пакетной программы пустые строки игнорируются.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере показан пакетный файл, в котором используются примечания для комментариев и вертикального пробела:
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

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)