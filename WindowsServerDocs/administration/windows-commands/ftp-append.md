---
title: Добавление в FTP
description: Справочный раздел по команде FTP Append, который добавляет локальный файл в файл на удаленном компьютере с использованием текущего параметра типа файла.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c1a133c-31dc-41a4-9eb9-258efd79804d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7d1b6ab4a6ae0c1654d4335d24f135b2893bdcb7
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83819144"
---
# <a name="ftp-append"></a>Добавление в FTP

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет локальный файл в файл на удаленном компьютере, используя текущий параметр типа файла.

## <a name="syntax"></a>Синтаксис

```
append <localfile> [remotefile]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<localfile>` | Указывает локальный файл для добавления. |
| [ремотефиле] | Указывает файл на удаленном компьютере, к которому <localfile> добавляется. Если этот параметр не используется, вместо `<localfile>` имени удаленного файла используется имя. |

### <a name="examples"></a>Примеры

Чтобы добавить *file1. txt* в *file2. txt* на удаленном компьютере, введите:

```
append file1.txt file2.txt
```

Для добавления локального файла *file1. txt* в файл с именем *file1. txt* на удаленном компьютере.

```
append file1.txt
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Дополнительные рекомендации по FTP](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
