---
ms.assetid: 835fc6f1-cc84-4189-b29a-dde90792469e
title: fsutil hardlink
ms.prod: windows-server-threshold
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 69474bd1817471176598afba508cd80c8fa1df8a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59840055"
---
# <a name="fsutil-hardlink"></a>fsutil hardlink
>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Создает жесткую связь между существующий файл и новый файл.

## <a name="syntax"></a>Синтаксис

```
fsutil hardlink create <NewFileName> <ExistingFileName>
fsutil hardlink list <Filename>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|создание|Устанавливает жесткая связь между существующего файла и файла NTFS. (Жесткая связь NTFS аналогична жесткую связь POSIX).|
|\<Этому параметру >|Указывает файл, который вы хотите создать жесткую связь для.|
|\<ExistingFileName >|Указывает файл, который вы хотите создать жесткую связь из.|
|list|Перечисляет жестких связей, чтобы *Filename*.<br /><br />Этот параметр применяется к:  Windows Server 2008 R2 и Windows 7.|

## <a name="remarks"></a>Примечания

-   Жесткая связь представляет запись каталога для файла. Каждый файл может считаться иметь по крайней мере один жесткой связи. На томах NTFS каждый файл может иметь несколько жестких связей, поэтому один файл может отображаться во многих каталогах (или даже в том же каталоге, с разными именами). Так как все ссылки ссылаться на тот же файл, программы можно открыть любую из ссылок и измените файл. Файл удаляется из файловой системы, только в том случае, после удаления всех ссылок на него. После создания жесткой связи, программы могут использовать его как имя файла.

#### <a name="additional-references"></a>Дополнительная справка
[Ключ синтаксиса командной строки](Command-Line-Syntax-Key.md)

[fsutil](Fsutil.md)


