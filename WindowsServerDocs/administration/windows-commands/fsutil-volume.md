---
ms.assetid: 0397c204-b3f8-4fd8-b71d-b7efb117766d
title: тома fsutil
ms.prod: windows-server-threshold
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: a8576dce4be639a516f8898e78bb6db12c91e171
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882455"
---
# <a name="fsutil-volume"></a>тома fsutil
>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Отсоединяет том или запрашивает жесткими дисками, чтобы определить объем свободного места на жестком диске или файл, который использует определенному кластеру.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
fsutil volume [allocationreport] <VolumePath>
fsutil volume [diskfree] <VolumePath>
fsutil volume [dismount] <VolumePath>
fsutil volume [filelayout] <VolumePath> <fileid>
fsutil volume [list]
fsutil volume [querycluster] <VolumePath> <Cluster> [<Cluster>] … …
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|allocationreport|Отображает сведения об использовании хранилища на томе.|
|\<VolumePath >|Указывает букву диска (двоеточие).|
|diskfree|Запрашивает жесткими дисками, чтобы определить объем свободного места на нем.|
|отключить|Отсоединяет том.|
|filelayout|Отображает метаданные NTFS для заданного файла.|
|\<Идентификатор файла >|Указывает идентификатор файла.|
|list|Список всех томов в системе.|
|querycluster|Находит файл, который используется в указанном кластере. Можно указать несколько кластеров с **querycluster** параметра.<br /><br />Этот параметр применяется к:  Windows Server 2008 R2 и Windows 7.|
|\<кластера >|Указывает логический кластер (LCN).|

## <a name="BKMK_examples"></a>Примеры
Чтобы отобразить отчет об выделенные кластеры, введите следующую команду:

```
fsutil volume allocationreport C:
```

Для отсоединения тома на диске C, введите следующую команду:

```
fsutil volume dismount c:
```

Чтобы запросить объем свободного пространства тома на диске C, введите следующую команду:

```
fsutil volume diskfree c:
```

Чтобы отобразить все сведения об указанных файлов, введите следующую команду:

```
fsutil volume C: *
fsutil volume C:\Windows
fsutil volume C: 0x00040000000001bf
```

Чтобы получить список томов на диске, введите следующую команду:

```
fsutil volume list
```

Чтобы найти файлы, в которых используется кластеры, определяемое числа логический кластер 50 и 0x2000 на диске C, введите:

```
fsutil volume querycluster C: 50 0x2000
```

#### <a name="additional-references"></a>Дополнительная справка
[Ключ синтаксиса командной строки](Command-Line-Syntax-Key.md)

[fsutil](Fsutil.md)

[Как работает NTFS](https://go.microsoft.com/fwlink/?LinkId=183396)


