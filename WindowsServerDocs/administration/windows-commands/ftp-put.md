---
title: FTP-размещение
description: Раздел команд Windows для FTP-вставки
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 95cc1e3f-523d-4374-98b8-16e6c276b2ca vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/30/2020
ms.openlocfilehash: d86ba8418f4c43c26f3745a9f70e676ca790c640
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725169"
---
# <a name="ftp-put"></a>FTP: размещение

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальный файл на удаленный компьютер, используя текущий тип перемещения файлов.
## <a name="syntax"></a>Синтаксис
```
put <LocalFile> [<remoteFile>]
```
#### <a name="parameters"></a>Параметры

|    Параметр     |                    Описание                    |
|------------------|---------------------------------------------------|
|   `<LocalFile>`  |         Указывает локальный файл для копирования.         |
| `[<remoteFile>]` | Указывает имя, используемое на удаленном компьютере. |

## <a name="remarks"></a>Примечания
- Команда **размещения** идентична команде **Send** .
- Если *ремотефиле* не указан, файлу присваивается имя *локальный_файл* .
  ## <a name="examples"></a>Примеры
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
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
