---
ms.assetid: f2eefaaf-2817-4ac7-abac-d2b65fa971dc
title: Транзакция fsutil
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: aa6692dbb8af1ec832650971c6723c060fc2cd56
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844017"
---
# <a name="fsutil-transaction"></a>Транзакция fsutil
>Область применения: Windows Server (половина ежегодного канала), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows 2008, Windows Vista

Управляет транзакциями NTFS.

Примеры использования этой команды см. в разделе [примеры](#BKMK_examples) .

## <a name="syntax"></a>Синтаксис

```
fsutil transaction [commit] <GUID>
fsutil transaction [fileinfo] <Filename>
fsutil transaction [list]
fsutil transaction [query] [{Files|All}] <GUID>
fsutil transaction [rollback] <GUID>
```

#### <a name="parameters"></a>Параметры

| Параметр  |                                                                                                                                                     Описание                                                                                                                                                     |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   фиксация   |                                                                                                                      Помечает конец успешной явной или явно указанной транзакции.                                                                                                                      |
|   <GUID>   |                                                                                                                               Указывает значение GUID, представляющее транзакцию.                                                                                                                               |
|  FileInfo  |                                                                                                                              Отображает сведения о транзакциях для указанного файла.                                                                                                                               |
| <Filename> |                                                                                                                                         Указывает полный путь и имя файла.                                                                                                                                          |
|    list    |                                                                                                                                 Отображает список выполняющихся в данный момент транзакций.                                                                                                                                  |
|   query    | Отображает сведения для указанной транзакции.<p>— Если указаны **файлы запросов транзакции fsutil** , то сведения о файле будут отображаться только для указанной транзакции.<br />— Если указан параметр **fsutil Transaction Query** , будут отображены все сведения о транзакции. |
|  откат;  |                                                                                                                                Выполняет откат указанной транзакции к началу.                                                                                                                                 |

### <a name="remarks"></a>Примечания

-   Транзакционная NTFS появилась в Windows Server 2008.

### <a name="examples"></a><a name="BKMK_examples"></a>Примеров
Чтобы отобразить сведения о транзакциях для файла к:\тест.ткст, введите:

```
fsutil transaction fileinfo c:\test.txt  
```

### <a name="additional-references"></a>Дополнительная справка
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Fsutil](Fsutil.md)

[Транзакционная NTFS](https://go.microsoft.com/fwlink/?LinkID=165402)


