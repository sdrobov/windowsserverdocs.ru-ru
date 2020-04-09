---
title: autochk
description: Команды Windows для **Autochk**, запускаемые при запуске компьютера и до Windows Server, начиная с проверки логической целостности файловой системы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8787e6a3-f023-4ea5-b2d1-61c6876d8aff
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 30ccdbb6aad6e116988ae9c782e3ff359642453e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851127"
---
# <a name="autochk"></a>autochk

Запускается при запуске компьютера и до Windows Server&reg; 2008 R2, начиная с проверки логической целостности файловой системы.

**Autochk. exe** — это версия **chkdsk** , которая работает только на дисках NTFS и только до запуска Windows Server 2008 R2. Программу **Autochk** нельзя запускать непосредственно из командной строки. Вместо этого **Autochk** запускается в следующих ситуациях:

- При попытке запустить **chkdsk** на загрузочном томе.

- Если **chkdsk** не может получить монопольное использование тома.

- Если том помечен как "грязный".

## <a name="remarks"></a>Примечания

> [!WARNING]
> Программу командной строки **Autochk** нельзя запустить непосредственно из командной строки. Вместо этого используйте программу командной строки **chkntfs** , чтобы настроить способ запуска **Autochk** при запуске.
> -  Для предотвращения запуска программы **Autochk** на определенном томе или нескольких томах можно использовать средство **chkntfs** с параметром **/x** .
>
> - Используйте программу командной строки **chkntfs. exe** с параметром **/t** , чтобы изменить задержку в Autochk с 0 секунд на 3 дня (259 200 с). Однако длительная задержка означает, что компьютер не будет запускаться до тех пор, пока не истечет время или пока не будет нажата клавиша для отмены **Autochk**.

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команду](chkdsk.md)

- [Chkntfs](chkntfs.md)

- [Устранение неполадок дисков и файловых систем](https://go.microsoft.com/fwlink/?LinkId=4527)