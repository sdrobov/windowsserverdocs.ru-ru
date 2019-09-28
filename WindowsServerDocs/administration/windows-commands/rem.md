---
title: rem
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a45b585-a83c-4ff6-badd-ff40f34cec23
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2da0b6e42858582c1485659f3bf8f59e8e2ed97e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384575"
---
# <a name="rem"></a>rem



Записывает комментарии (примечания) в пакетном файле или конфигурации. Представления. Если комментарий не указан, **REM** добавляется пробел по вертикали.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
rem [<Comment>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0Comment >|Указывает строку символов, включаемую в качестве комментария.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Команда **REM** не отображает комментарии на экране. Необходимо использовать команду **echo on** в пакете или конфигурации. SYS для отображения комментариев на экране.
-   В комментарии пакетного файла нельзя использовать символ перенаправления ( **<** или **>** ) или канал ( **|** ).
-   Несмотря на то, что можно использовать **REM** без комментариев для добавления вертикальных пробелов в пакетный файл, можно также использовать пустые строки. При обработке пакетной программы пустые строки игнорируются.

## <a name="BKMK_examples"></a>Примеров

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

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)