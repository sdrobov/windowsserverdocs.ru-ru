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
ms.openlocfilehash: 210196471123e9fc2456a2ee84b1949f9f883d90
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844297"
---
# <a name="fsutil-hardlink"></a>Fsutil hardlink
>Область применения: Windows Server (половина ежегодного канала), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Создает жесткую связь между существующим файлом и новым файлом.

## <a name="syntax"></a>Синтаксис

```
fsutil hardlink create <NewFileName> <ExistingFileName>
fsutil hardlink list <Filename>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|создание|Устанавливает жесткую связь NTFS между существующим файлом и новым файлом. (Жесткая связь NTFS аналогична жесткой связи POSIX.)|
|\<Невфиленаме >|Указывает файл, к которому нужно создать жесткую связь.|
|\<Ексистингфиленаме >|Указывает файл, из которого требуется создать жесткую связь.|
|list|Выводит жестких связей в *имя файла*.<p>Этот параметр применяется к: Windows Server 2008 R2 и Windows 7.|

## <a name="remarks"></a>Примечания

-   Жесткая связь — это запись каталога для файла. Каждый файл можно считать по крайней мере одним жестким каналом. На томах NTFS каждый файл может иметь несколько жестких связей, поэтому один файл может находиться во многих каталогах (или даже в одном каталоге с разными именами). Так как все ссылки ссылаются на один и тот же файл, программы могут открывать любую из ссылок и изменять файл. Файл удаляется из файловой системы только после удаления всех ссылок на него. После создания жесткой связи программы могут использовать ее, как любое другое имя файла.

## <a name="additional-references"></a>Дополнительные материалы
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Fsutil](Fsutil.md)


