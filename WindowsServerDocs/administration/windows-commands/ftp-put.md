---
title: FTP-размещение
description: Раздел команд Windows для FTP-вставки
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95cc1e3f-523d-4374-98b8-16e6c276b2ca vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/30/2020
ms.openlocfilehash: 019a81364dbedb443a3a23d5c5a6f8db1496d83d
ms.sourcegitcommit: 479ad84a0d6c7c7b8308122b8bac8308cb36fe9b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391717"
---
# <a name="ftp-put"></a>FTP: размещение

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальный файл на удаленный компьютер, используя текущий тип перемещения файлов.
## <a name="syntax"></a>Синтаксис
```
put <LocalFile> [<remoteFile>]
```
### <a name="parameters"></a>Параметры

|    Параметр     |                    Описание                    |
|------------------|---------------------------------------------------|
|   `<LocalFile>`  |         Указывает локальный файл для копирования.         |
| `[<remoteFile>]` | Указывает имя, используемое на удаленном компьютере. |

## <a name="remarks"></a>Примечания
- Команда **размещения** идентична команде **Send** .
- Если *ремотефиле* не указан, файлу присваивается имя *локальный_файл* .
  ## <a name="examples"></a><a name="BKMK_Examples"></a>Примеров
  Скопируйте локальный файл **Test. txt** и назовите его **test1. txt** на удаленном компьютере.
  ```
  put test.txt test1.txt
  ```
  Скопируйте локальный файл **Program. exe** на удаленный компьютер.
  ```
  put program.exe
  ```
  ## <a name="additional-references"></a>Дополнительные ссылки
- [FTP: ASCII](ftp-ascii.md)
- [FTP: двоичный формат](ftp-binary.md)
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
