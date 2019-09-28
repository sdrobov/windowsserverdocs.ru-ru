---
ms.assetid: 835fc6f1-cc84-4189-b29a-dde90792469e
title: Fsutil hardlink
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: de9a04850555b11a42d74826685c249bea15710c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376885"
---
# <a name="fsutil-hardlink"></a>Fsutil hardlink
>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Создает жесткую связь между существующим файлом и новым файлом.

## <a name="syntax"></a>Синтаксис

```
fsutil hardlink create <NewFileName> <ExistingFileName>
fsutil hardlink list <Filename>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|create|Устанавливает жесткую связь NTFS между существующим файлом и новым файлом. (Жесткая связь NTFS аналогична жесткой связи POSIX.)|
|@no__t 0NewFileName >|Указывает файл, к которому нужно создать жесткую связь.|
|@no__t 0ExistingFileName >|Указывает файл, из которого требуется создать жесткую связь.|
|list|Выводит жестких связей в *имя файла*.<br /><br />Этот параметр применяется к:  Windows Server 2008 R2 и Windows 7.|

## <a name="remarks"></a>Примечания

-   Жесткая связь — это запись каталога для файла. Каждый файл можно считать по крайней мере одним жестким каналом. На томах NTFS каждый файл может иметь несколько жестких связей, поэтому один файл может находиться во многих каталогах (или даже в одном каталоге с разными именами). Так как все ссылки ссылаются на один и тот же файл, программы могут открывать любую из ссылок и изменять файл. Файл удаляется из файловой системы только после удаления всех ссылок на него. После создания жесткой связи программы могут использовать ее, как любое другое имя файла.

#### <a name="additional-references"></a>Дополнительная справка
[Условные обозначения синтаксиса команд командной строки](Command-Line-Syntax-Key.md)

[Fsutil](Fsutil.md)


