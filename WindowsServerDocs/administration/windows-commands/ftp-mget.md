---
title: MGET FTP
description: Справочный раздел по команде FTP mget, который копирует удаленные файлы на локальный компьютер, используя текущий тип перемещения файлов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6c85ae96-ec51-48a9-a227-7f02c7332c69
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 93d562fcdaec0d6609e7be8b3543cd55bb910238
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820434"
---
# <a name="ftp-mget"></a>MGET FTP

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует удаленные файлы на локальный компьютер, используя текущий тип перемещения файлов.

## <a name="syntax"></a>Синтаксис

```
mget <remotefile>[ ]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<remotefile>` | Указывает удаленные файлы, которые необходимо скопировать на локальный компьютер. |

### <a name="examples"></a>Примеры

Чтобы скопировать удаленные файлы *a. exe* и *b. exe* на локальный компьютер, используя текущий тип перемещения файлов, введите:

```
mget a.exe b.exe
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда FTP ASCII](ftp-ascii.md)

- [Двоичная команда FTP](ftp-binary.md)

- [Дополнительные рекомендации по FTP](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
