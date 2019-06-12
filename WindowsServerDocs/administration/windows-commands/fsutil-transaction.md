---
ms.assetid: f2eefaaf-2817-4ac7-abac-d2b65fa971dc
title: транзакции fsutil
ms.prod: windows-server-threshold
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: c225c99919a2558559b1ec7a47b61d716e199a73
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438999"
---
# <a name="fsutil-transaction"></a>транзакции fsutil
>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows 2008, Windows Vista

Управляет транзакциями NTFS.

Примеры для использования этой команды, см. в разделе [примеры](#BKMK_examples) .

## <a name="syntax"></a>Синтаксис

```
fsutil transaction [commit] <GUID>
fsutil transaction [fileinfo] <Filename>
fsutil transaction [list]
fsutil transaction [query] [{Files|All}] <GUID>
fsutil transaction [rollback] <GUID>
```

### <a name="parameters"></a>Параметры

| Параметр  |                                                                                                                                                     Описание                                                                                                                                                     |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   фиксация   |                                                                                                                      Помечает конец успешно явного или неявного указанную транзакцию.                                                                                                                      |
|   <GUID>   |                                                                                                                               Указывает значение идентификатора GUID, представляющий транзакцию.                                                                                                                               |
|  FileInfo  |                                                                                                                              Отображает сведения о транзакциях для указанного файла.                                                                                                                               |
| <Filename> |                                                                                                                                         Указывает полный путь и имя файла.                                                                                                                                          |
|    list    |                                                                                                                                 Список текущих выполняемых транзакций.                                                                                                                                  |
|   запрос    | Отображает сведения для данной транзакции.<br /><br />Если **файлы запросов транзакций fsutil** указан, сведения о файле отображается только для данной транзакции.<br />Если **транзакции fsutil запросы ко всем** указан, будут отображены все сведения для операции. |
|  Откат  |                                                                                                                                Выполняет откат указанной транзакции на начало.                                                                                                                                 |

### <a name="remarks"></a>Примечания

-   Транзакционная NTFS впервые появился в Windows Server 2008.

### <a name="BKMK_examples"></a>Примеры
Чтобы отобразить сведения о транзакциях для c:\test.txt файл, введите следующую команду:

```
fsutil transaction fileinfo c:\test.txt  
```

### <a name="additional-references"></a>Дополнительная справка
[Условные обозначения синтаксиса команд командной строки](Command-Line-Syntax-Key.md)

[fsutil](Fsutil.md)

[Транзакционная NTFS](https://go.microsoft.com/fwlink/?LinkID=165402)


