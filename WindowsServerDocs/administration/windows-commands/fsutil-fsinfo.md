---
ms.assetid: 7787a72e-a26b-415f-b700-a32806803478
title: Fsutil fsinfo
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 56e27c386451c561de8f62e523e2d1e59a8ce84c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844307"
---
# <a name="fsutil-fsinfo"></a>Fsutil fsinfo
>Область применения: Windows Server (половина ежегодного канала), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Выводит список всех дисков, запрашивает тип диска, сведения о томе, запрашивает информацию о томе, связанную с NTFS, или запрашивает статистику файловой системы.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
fsutil fsinfo [drives]
fsutil fsinfo [drivetype] <VolumePath>
fsutil fsinfo [ntfsinfo] <RootPath>
fsutil fsinfo [statistics] <VolumePath>
fsutil fsinfo [volumeinfo] <RootPath>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|диски|Список всех дисков компьютера.|
|DriveType|Запрашивает диск и перечисляет его тип, например дисковод компакт-дисков.|
|NTFSInfo|Содержит сведения о томе NTFS для указанного тома, например число секторов, общее количество кластеров, свободные кластеры, а также начало и конец зоны MFT.|
|секторинфо|Выводит сведения о размере сектора оборудования и его выравнивании.|
|статистика|Отображает статистику файловой системы для указанного тома, например метаданные, файл журнала и операции чтения и записи MFT.|
|волумеинфо|Выводит сведения для указанного тома, например файловую систему, и указывает, поддерживает ли том имена файлов с учетом регистра, Юникод в именах файлов, квоты дисков или является томом DirectAccess (DAX).|
|< "VolumePath" >|Указывает букву диска (с последующим двоеточием).|
|< "Рутпаснаме" >|Указывает букву диска (с последующим двоеточием) корневого диска.|

## <a name="examples"></a><a name="BKMK_examples"></a>Примеров
Чтобы вывести список всех дисков компьютера, введите:

```
fsutil fsinfo drives
```

Выходные данные, аналогичные приведенным ниже, отображаются:

```
Drives: A:\ C:\ D:\ E:\       
```

Чтобы запросить тип диска C, введите:

```
fsutil fsinfo drivetype c:
```

Возможные результаты запроса:

```
Unknown Drive
No such Root Directory
Removable Drive, for example floppy
Fixed Drive
Remote/Network Drive
CD-ROM Drive
Ram Disk
```

Чтобы запросить сведения о томе для тома E, введите:

```
fsinfo volumeinfo e:\
```

Выходные данные, аналогичные приведенным ниже, отображаются:

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

Чтобы запросить диск F для сведений о томе NTFS, введите:

```
fsutil fsinfo ntfsinfo f:
```

Выходные данные, аналогичные приведенным ниже, отображаются:

```
NTFS Volume Serial Number : 0xe660d46a60d442cb
Number Sectors :            0x00000000010ea04f
Total Clusters :            0x000000000021d409
.
.
.
Mft Zone End   :            0x0000000000004700       
```

Чтобы запросить базовое оборудование файловой системы для сведений о секторе, введите:

```
fsinfo sectorinfo d:
```

Выходные данные, аналогичные приведенным ниже, отображаются:

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

Чтобы запросить статистику файловой системы для диска E, введите:

```
fsinfo statistics e:
```

Выходные данные, аналогичные приведенным ниже, отображаются:

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

## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[fsutil](Fsutil.md)


