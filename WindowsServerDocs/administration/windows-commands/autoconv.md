---
title: autoconv
description: Раздел Windows команды для **autoconv** — преобразует файл таблицы размещения (Fat), и тома Fat32 в NTFS файловая система.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 1d135da085558f12a51c8febfd72aa805e1d12f1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59872495"
---
# <a name="autoconv"></a>autoconv

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Преобразует файл таблицы размещения (Fat) и тома Fat32 в файловой системе NTFS, изменения существующих файлов и каталогов содержимого во время запуска после **autochk** выполняется. тома, преобразованные в файловую систему NTFS не удается преобразовать обратно в Fat или Fat32.
## <a name="remarks"></a>Примечания
Не удается запустить **autoconv** в командной строке. Это будет выполняться только во время запуска, если задать с помощью **convert.exe**.
## <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[autochk](autochk.md)
[преобразовать](convert.md)
[работа с файловыми системами](https://go.microsoft.com/fwlink/?LinkId=4509)
