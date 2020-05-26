---
title: FTP-размещение
description: Справочный раздел для команды FTP-вставки, который копирует локальный файл на удаленный компьютер с использованием текущего типа перемещения файлов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 95cc1e3f-523d-4374-98b8-16e6c276b2ca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/30/2020
ms.openlocfilehash: aee76b95ac538868122d5137958723326575eb18
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820374"
---
# <a name="ftp-put"></a>FTP-размещение

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует локальный файл на удаленный компьютер, используя текущий тип перемещения файлов.

> [!NOTE]
> Эта команда совпадает с [командой FTP Send](ftp-send_1.md).

## <a name="syntax"></a>Синтаксис

```
put <localfile> [<remotefile>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<localfile>` | Указывает локальный файл для копирования. |
| `[<remotefile>]` | Указывает имя, используемое на удаленном компьютере. Если не указать *ремотефиле*, файл будет давать имя *локальный_файл* .|

### <a name="examples"></a>Примеры

Чтобы скопировать локальный файл *Test. txt* и присвоить ему имя *test1. txt* на удаленном компьютере, введите:

```
put test.txt test1.txt
```

Чтобы скопировать локальный файл *Program. exe* на удаленный компьютер, введите:

```
put program.exe
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда FTP ASCII](ftp-ascii.md)

- [Двоичная команда FTP](ftp-binary.md)

- [Дополнительные рекомендации по FTP](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
