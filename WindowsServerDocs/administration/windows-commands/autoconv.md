---
title: autoconv
description: Справочная статья по команде аутоконв, которая преобразует тома FAT и FAT32 в файловую систему NTFS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 17281e54-0b18-4e84-94ac-24586c82df4e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c6d54f413ab9d4f680f59294a3f01c1de02db222
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923561"
---
# <a name="autoconv"></a>autoconv

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Преобразует тома с файловой системой FAT и FAT32 в файловую систему NTFS, при этом существующие файлы и каталоги остаются без изменений при запуске после запуска **Autochk** . тома, преобразованные в файловую систему NTFS, не могут быть преобразованы обратно в FAT или FAT32.

> [!IMPORTANT]
> Невозможно запустить **аутоконв** из командной строки. Это может выполняться при запуске, если задано через **convert.exe**.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда Autochk](autochk.md)

- [преобразовать команду](convert.md)
