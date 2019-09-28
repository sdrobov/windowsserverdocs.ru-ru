---
title: Wbadmin Restore Catalog
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ce1e24a0-821d-4353-b09d-8f82c5c4ad56
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b0d646440ca9b30f9fa30fb1ac3ff08458b8e44d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362330"
---
# <a name="wbadmin-restore-catalog"></a>Wbadmin Restore Catalog



Восстанавливает каталог резервных копий для локального компьютера из указанного места хранения.

Чтобы восстановить каталог резервных копий с помощью этой подкоманды, необходимо быть членом группы " **Операторы архива** " или " **Администраторы** ", либо вам должны быть делегированы соответствующие разрешения. Кроме того, необходимо запустить программу **Wbadmin** из командной строки с повышенными привилегиями. (Чтобы открыть командную строку с повышенными привилегиями, щелкните правой кнопкой мыши пункт **Командная строка**и выберите команду **Запуск от имени администратора**.)

Примеры использования этой подкоманды см. в разделе [примеры](#BKMK_examples).

## <a name="syntax"></a>Синтаксис

```
wbadmin restore catalog
-backupTarget:{<BackupDestinationVolume> | <NetworkShareHostingBackup>}
[-machine:<BackupMachineName>]
[-quiet]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-backupTarget|Указывает расположение каталога резервных копий системы в том виде, в котором он находился в момент создания резервной копии.|
|-Machine|Указывает имя компьютера, для которого требуется восстановить каталог резервных копий. Используется при хранении резервных копий на нескольких компьютерах в одном и том же месте. Следует использовать, если указан **-backupTarget** .|
|-quiet|Выполняет подкоманду без запросов пользователю.|

## <a name="remarks"></a>Примечания

Если расположение (диск, DVD или удаленная общая папка), где хранятся резервные копии, повреждено или утеряно и не может использоваться для восстановления каталога резервного копирования, используйте **Wbadmin Delete Catalog** , чтобы удалить поврежденный каталог. В этом случае следует создать новую резервную копию после удаления каталога резервного копирования.

## <a name="BKMK_examples"></a>Примеров

Чтобы восстановить каталог из резервной копии, хранящейся на диске d:, введите:
```
wbadmin restore catalog -backupTarget:d
```
Чтобы восстановить каталог из резервной копии, хранящейся в общей папке \\ @ no__t-1servername\share Server01, введите:
```
wbadmin restore catalog -backupTarget:\\servername\share -machine:server01
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
-   Командлет [RESTORE-вбкаталог](https://technet.microsoft.com/library/jj902437.aspx)