---
ms.assetid: 0397c204-b3f8-4fd8-b71d-b7efb117766d
title: Том fsutil
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: c4496cfec94823ae177bc6de4fac83dc977fb61d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376704"
---
# <a name="fsutil-volume"></a>Том fsutil
>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Отключает том или запрашивает жесткий диск, чтобы определить, какой объем свободного места в настоящее время доступен на жестком диске или какой файл используется в конкретном кластере.

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
|аллокатионрепорт|Отображает сведения о том, как хранилище используется на заданном томе.|
|@no__t 0VolumePath >|Указывает букву диска (с последующим двоеточием).|
|дискфри|Запрашивает жесткий диск, чтобы определить объем свободного места на нем.|
|отключить|Отключает том.|
|филелайаут|Отображает метаданные NTFS для заданного файла.|
|@no__t 0fileid >|Указывает идентификатор файла.|
|list|Список всех томов в системе.|
|куериклустер|Определяет, какой файл использует указанный кластер. Можно указать несколько кластеров с помощью параметра **куериклустер** .<br /><br />Этот параметр применяется к:  Windows Server 2008 R2 и Windows 7.|
|@no__t 0cluster >|Указывает номер логического кластера (LCN).|

## <a name="BKMK_examples"></a>Примеров
Чтобы отобразить отчет о распределенных кластерах, введите:

```
fsutil volume allocationreport C:
```

Чтобы отключить том на диске C, введите:

```
fsutil volume dismount c:
```

Чтобы запросить объем свободного пространства тома на диске C, введите:

```
fsutil volume diskfree c:
```

Чтобы отобразить все сведения о указанных файлах, введите:

```
fsutil volume C: *
fsutil volume C:\Windows
fsutil volume C: 0x00040000000001bf
```

Чтобы вывести список томов на диске, введите:

```
fsutil volume list
```

Чтобы найти файлы, использующие кластеры, указанные номерами логических кластеров 50 и 0x2000 на диске C, введите:

```
fsutil volume querycluster C: 50 0x2000
```

#### <a name="additional-references"></a>Дополнительная справка
[Условные обозначения синтаксиса команд командной строки](Command-Line-Syntax-Key.md)

[Fsutil](Fsutil.md)

[Как работает NTFS](https://go.microsoft.com/fwlink/?LinkId=183396)


