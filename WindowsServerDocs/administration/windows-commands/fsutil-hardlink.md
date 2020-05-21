---
title: fsutil hardlink
description: Справочный раздел команды fsutil hardlink, который создает жесткую связь между существующим файлом и новым файлом.
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: 835fc6f1-cc84-4189-b29a-dde90792469e
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: ef0f8347a73a2522f6c4b9298799ad2e3536c4c9
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2020
ms.locfileid: "83435929"
---
# <a name="fsutil-hardlink"></a>fsutil hardlink

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8

Создает жесткую связь между существующим файлом и новым файлом. Жесткая связь — это запись каталога для файла. Каждый файл можно считать по крайней мере одним жестким каналом.

На томах NTFS каждый файл может иметь несколько жестких связей, поэтому один файл может находиться во многих каталогах (или даже в одном каталоге с разными именами). Так как все ссылки ссылаются на один и тот же файл, программы могут открывать любую из ссылок и изменять файл. Файл удаляется из файловой системы только после удаления всех ссылок на него. После создания жесткой связи программы могут использовать ее, как любое другое имя файла.

## <a name="syntax"></a>Синтаксис

```
fsutil hardlink create <newfilename> <existingfilename>
fsutil hardlink list <filename>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| create | Устанавливает жесткую связь NTFS между существующим файлом и новым файлом. (Жесткая связь NTFS аналогична жесткой связи POSIX.) |
| \<невфиленаме> | Указывает файл, к которому нужно создать жесткую связь. |
| \<ексистингфиленаме> | Указывает файл, из которого требуется создать жесткую связь. |
| list | Список жестких ссылок на *имя файла*. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [fsutil](fsutil.md)
