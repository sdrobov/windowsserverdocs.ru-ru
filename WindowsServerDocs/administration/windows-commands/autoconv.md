---
title: autoconv
description: 'Раздел команд Windows для **аутоконв** : Преобразование томов FAT и FAT32 в файловую систему NTFS.'
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17281e54-0b18-4e84-94ac-24586c82df4e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bf36be6bcf3dd8f6c61c6ab0d8780ed77dd8903a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383450"
---
# <a name="autoconv"></a>autoconv

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Преобразует тома с файловой системой FAT и FAT32 в файловую систему NTFS, при этом существующие файлы и каталоги остаются без изменений при запуске после запуска **Autochk** . тома, преобразованные в файловую систему NTFS, не могут быть преобразованы обратно в FAT или FAT32.
## <a name="remarks"></a>Примечания
Невозможно запустить **аутоконв** в командной строке. Это будет выполняться при запуске, если задано с помощью **Convert. exe**.
## <a name="additional-references"></a>Дополнительные ссылки
[Синтаксис командной строки](command-line-syntax-key.md)
[Autochk](autochk.md)
[Convert](convert.md)
[Работа с файловыми системами](https://go.microsoft.com/fwlink/?LinkId=4509)
