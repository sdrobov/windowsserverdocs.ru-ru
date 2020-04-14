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
ms.openlocfilehash: ecd579a313fe1cad1b8a5b4a622aaaec2d6a6d63
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843137"
---
# <a name="ftp-put"></a>FTP: размещение

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
  ## <a name="examples"></a><a name="BKMK_Examples"></a>Примеров
  Скопируйте локальный файл **Test. txt** и назовите его **test1. txt** на удаленном компьютере.
  ```
  put test.txt test1.txt
  ```
  Скопируйте локальный файл **Program. exe** на удаленный компьютер.
  ```
  put program.exe
  ```
  ## <a name="additional-references"></a>Дополнительные материалы
- [FTP: ASCII](ftp-ascii.md)
- [FTP: двоичный формат](ftp-binary.md)
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
