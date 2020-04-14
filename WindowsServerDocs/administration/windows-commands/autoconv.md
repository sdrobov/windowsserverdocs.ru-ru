---
title: autoconv
description: Раздел команд Windows для **аутоконв**, который преобразует тома FAT и FAT32 в файловую систему NTFS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 17281e54-0b18-4e84-94ac-24586c82df4e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fe0e388a1d4fd79567ef0562197e3181bbbc46f4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851117"
---
# <a name="autoconv"></a>autoconv

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Преобразует тома с файловой системой FAT и FAT32 в файловую систему NTFS, при этом существующие файлы и каталоги остаются без изменений при запуске после запуска **Autochk** . тома, преобразованные в файловую систему NTFS, не могут быть преобразованы обратно в FAT или FAT32.

## <a name="remarks"></a>Примечания

Невозможно запустить **аутоконв** в командной строке. Это будет выполняться при запуске, если задано с помощью **Convert. exe**.

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [autochk](autochk.md)

- [convert](convert.md)

- [Работа с файловыми системами](https://go.microsoft.com/fwlink/?LinkId=4509)
