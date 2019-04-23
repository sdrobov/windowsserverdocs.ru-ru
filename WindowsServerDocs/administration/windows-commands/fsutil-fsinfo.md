---
ms.assetid: 7787a72e-a26b-415f-b700-a32806803478
title: fsutil fsinfo
ms.prod: windows-server-threshold
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 434dfde2286538367fb96d168b06983cb4357067
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873045"
---
# <a name="fsutil-fsinfo"></a>fsutil fsinfo
>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Список всех дисков, запрашивает тип диска, запрашивает сведения о томе, запрашивает сведения о томе NTFS конкретных или статистику файловой системы.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
fsutil fsinfo [drives]
fsutil fsinfo [drivetype] <VolumePath>
fsutil fsinfo [ntfsinfo] <RootPath>
fsutil fsinfo [statistics] <VolumePath>
fsutil fsinfo [volumeinfo] <RootPath>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|диски|Список всех дисков на компьютере.|
|DriveType|Запрашивает диска и выводит его тип, например дисковод компакт-дисков.|
|NTFSInfo|Перечисляет сведения NTFS для указанного тома, например число секторов, общее число кластеров, свободные кластеры и начало и конец зоны MFT.|
|sectorinfo|Выводит сведения о размер сектора оборудования и выравнивание.|
|Статистика|Перечисляет статистику файловой системы для указанного тома, такие как метаданные, файл журнала и таблицы MFT операций чтения и записи.|
|volumeinfo|Выводит сведения для указанного тома, например файловой системы и ли том поддерживает имена файлов с учетом регистра, символ Юникода в именах файлов, дисковые квоты, или — это том DirectAccess (DAX).|
|< «VolumePath» >|Указывает букву диска (двоеточие).|
|< «RootPathname» >|Указывает букву диска (двоеточие) корневого диска.|

## <a name="BKMK_examples"></a>Примеры
Чтобы получить список всех дисков на компьютере, введите следующую команду:

```
fsutil fsinfo drives
```

Результат, аналогичный приведенному появится следующее:

```
Drives: A:\ C:\ D:\ E:\       
```

Чтобы запросить тип диска для диска C, введите следующую команду:

```
fsutil fsinfo drivetype c:
```

Возможные результаты запроса включают:

```
Unknown Drive
No such Root Directory
Removable Drive, for example floppy
Fixed Drive
Remote/Network Drive
CD-ROM Drive
Ram Disk
```

Чтобы запросить сведения о томе для тома E, введите следующую команду:

```
fsinfo volumeinfo e:\
```

Результат, аналогичный приведенному появится следующее:

```
Volume Name :Volume
Serial Number : 0xd0b634d9
Max Component Length : 255
File System Name : NTFS
.
.
.
Supports Named Streams
Is DAX Volume
```

Запрос диск F NTFS конкретных сведений о томах введите следующую команду:

```
fsutil fsinfo ntfsinfo f:
```

Результат, аналогичный приведенному появится следующее:

```
NTFS Volume Serial Number : 0xe660d46a60d442cb
Number Sectors :            0x00000000010ea04f
Total Clusters :            0x000000000021d409
.
.
.
Mft Zone End   :            0x0000000000004700       
```

Чтобы запросить файловой системы базового оборудования сектора сведения, введите следующую команду:

```
fsinfo sectorinfo d:
```

Результат, аналогичный приведенному появится следующее:

```
D:\>fsutil fsinfo sectorinfo d:
LogicalBytesPerSector :                                 4096
PhysicalBytesPerSectorForAtomicity :                    4096
.
.
.
Trim Not Supported
DAX capable
```

Чтобы запросить статистику файловой системы для диска E, введите следующую команду:

```
fsinfo statistics e:
```

Результат, аналогичный приведенному появится следующее:

```
File System Type :     NTFS
Version :              1
UserFileReads :        75021
UserFileReadBytes :    1305244512
.
.
.
LogFileWriteBytes :    180936704       
```

#### <a name="additional-references"></a>Дополнительная справка
[Синтаксис командной строки Key](Command-Line-Syntax-Key.md)
[Fsutil](Fsutil.md)


