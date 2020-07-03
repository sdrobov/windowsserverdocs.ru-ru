---
title: fsutil hardlink
description: Справочная статья по команде fsutil hardlink, которая создает жесткую связь между существующим файлом и новым файлом.
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: 835fc6f1-cc84-4189-b29a-dde90792469e
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: b4cbc3912339464a061c027234d0d22b2d73ea09
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932284"
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
| \<newfilename> | Указывает файл, к которому нужно создать жесткую связь. |
| \<existingfilename> | Указывает файл, из которого требуется создать жесткую связь. |
| list | Список жестких ссылок на *имя файла*. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [fsutil](fsutil.md)
