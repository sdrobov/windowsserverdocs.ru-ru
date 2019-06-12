---
title: autochk
description: Раздел Windows команды для **autochk** — запускается при запуске и до Windows Server, начиная для проверки логической целостности файловой системы.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8787e6a3-f023-4ea5-b2d1-61c6876d8aff
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e6c26d42410e5466950ede4f9aa059e315030588
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66435035"
---
# <a name="autochk"></a>autochk



Выполняется, когда компьютер запускается и более ранние версии до Windows Server® 2008 R2 начиная для проверки логической целостности файловой системы.

**Autochk.exe** — это версия **Chkdsk** , которое будет выполняться только на дисках NTFS и только до запуска Windows Server 2008 R2. **Autochk** нельзя запускать непосредственно из командной строки. Вместо этого **Autochk** выполняется в следующих ситуациях:
-   Если попытаться выполнить **Chkdsk** на загрузочном томе
-   Если **Chkdsk** не удается получить монопольного использования тома
-   Если том помечен как "грязный"

## <a name="remarks"></a>Примечания

> -   [!WARNING]
>     **Autochk** средство командной строки невозможно запустить непосредственно из командной строки. Вместо этого используйте **Chkntfs** средство командной строки для настройки, как вам нужно **Autochk** для выполнения при запуске.
> -   Можно использовать **Chkntfs** с **/x** параметр для предотвращения **Autochk** по определенного тома или несколько томов.
> -   Используйте **Chkntfs.exe** средство командной строки с **/t** параметр, чтобы задать задержку Autochk 0 секунд до 3 дней (259 200 секунд). Тем не менее, длительная задержка означает, что компьютер не запускается до истечения времени или до нажатия клавиши для отмены **Autochk**.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[CHKDSK](chkdsk.md)

[chkntfs](chkntfs.md)

[Устранение неполадок дисков и файловых систем](https://go.microsoft.com/fwlink/?LinkId=4527)