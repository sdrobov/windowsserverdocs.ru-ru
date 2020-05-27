---
title: Переименование FTP
description: Справочный раздел для команды FTP Rename, которая переименовывает удаленные файлы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 977b7c95-6428-4980-80ec-79c3ae7e8c4d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a8d3ea25e48266db6a4a282f2ea395bd8b8d5fd9
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820314"
---
# <a name="ftp-rename"></a>Переименование FTP

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Переименовывает удаленные файлы.

## <a name="syntax"></a>Синтаксис

```
rename <filename> <newfilename>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<filename>` | Указывает файл, который требуется переименовать. |
| `<newfilename>` | Указывает новое имя файла. |

### <a name="examples"></a>Примеры

Чтобы переименовать удаленный файл *example. txt* в *example1. txt*, введите:

```
rename example.txt example1.txt
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Дополнительные рекомендации по FTP](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
