---
title: autochk
description: Раздел команд Windows для **Autochk** — запускается при запуске компьютера и до Windows Server, начиная с проверки логической целостности файловой системы.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 76e54d14879cefd4661a1ca7f1c3b8ee7ec58de2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382352"
---
# <a name="autochk"></a>autochk



Запускается при запуске компьютера и до Windows Server® 2008 R2, начиная с проверки логической целостности файловой системы.

**Autochk. exe** — это версия **chkdsk** , которая работает только на дисках NTFS и только до запуска Windows Server 2008 R2. Программу **Autochk** нельзя запускать непосредственно из командной строки. Вместо этого **Autochk** запускается в следующих ситуациях:
-   При попытке запустить **chkdsk** на загрузочном томе
-   Если **chkdsk** не может получить монопольное использование тома
-   Если том помечен как "грязный"

## <a name="remarks"></a>Примечания

> -   [!WARNING]
>     Программу командной строки **Autochk** нельзя запустить непосредственно из командной строки. Вместо этого используйте программу командной строки **chkntfs** , чтобы настроить способ запуска **Autochk** при запуске.
> -   Для предотвращения запуска программы **Autochk** на определенном томе или нескольких томах можно использовать средство **chkntfs** с параметром **/x** .
> -   Используйте программу командной строки **chkntfs. exe** с параметром **/t** , чтобы изменить задержку в Autochk с 0 секунд на 3 дня (259 200 с). Однако длительная задержка означает, что компьютер не будет запускаться до тех пор, пока не истечет время или пока не будет нажата клавиша для отмены **Autochk**.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Команду](chkdsk.md)

[Chkntfs](chkntfs.md)

[Устранение неполадок дисков и файловых систем](https://go.microsoft.com/fwlink/?LinkId=4527)