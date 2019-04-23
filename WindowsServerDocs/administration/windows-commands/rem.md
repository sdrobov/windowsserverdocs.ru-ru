---
title: rem
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 85c8a69bf21a386cd36e45bbca6dacd35aef2509
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59847005"
---
# <a name="rem"></a>rem



Записи комментариев в пакетный файл и файл CONFIG. SYS. Если нет комментариев не указан, **rem** добавляет интервалы по вертикали.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
rem [<Comment>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Комментарий >|Указывает строку символов, которые нужно включить в качестве комментария.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   **Rem** команда выводит комментарии на экране. Необходимо использовать **включить вывод** команд в пакетных файлах или конфигурации. Файл SYS Отображение комментариев на экране.
-   Нельзя использовать символ перенаправления (**<** или **>**) или вертикальной черты (**|**) в комментарий пакетного файла.
-   Несмотря на то, что можно использовать **rem** без комментарий, добавляемый интервал по вертикали пакетный файл, можно также использовать пустые строки. Пустые строки учитываются при обработке пакетного файла.

## <a name="BKMK_examples"></a>Примеры

В следующем примере пакетный файл, который использует "Примечания" для комментариев и расстояния по вертикали:
```
@echo off
rem  This batch program formats and checks new disks.
rem  It is named Checknew.bat.
rem
rem echo Insert new disk in Drive B.
pause 
format b: /v chkdsk b: 
```
Чтобы включить комментарий перед **строке** команды в файле CONFIG. SYS добавьте следующие строки в файл config. SYS:
```
rem Set prompt to indicate current directory
prompt $p$g
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)