---
title: Wbadmin Restore Catalog
description: Команда Windows для команды Wbadmin Recover Catalog, которая восстанавливает каталог резервных копий для локального компьютера из указанного места хранения.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ce1e24a0-821d-4353-b09d-8f82c5c4ad56
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0ce9182e4e405b1538277db25f06b6a49d7240f9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80829707"
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

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-backupTarget|Указывает расположение каталога резервных копий системы в том виде, в котором он находился в момент создания резервной копии.|
|-Machine|Указывает имя компьютера, для которого требуется восстановить каталог резервных копий. Используется при хранении резервных копий на нескольких компьютерах в одном и том же месте. Следует использовать, если указан **-backupTarget** .|
|-quiet|Выполняет подкоманду без запросов пользователю.|

## <a name="remarks"></a>Примечания

Если расположение (диск, DVD или удаленная общая папка), где хранятся резервные копии, повреждено или утеряно и не может использоваться для восстановления каталога резервного копирования, используйте **Wbadmin Delete Catalog** , чтобы удалить поврежденный каталог. В этом случае следует создать новую резервную копию после удаления каталога резервного копирования.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы восстановить каталог из резервной копии, хранящейся на диске d:, введите:
```
wbadmin restore catalog -backupTarget:d
```
Чтобы восстановить каталог из резервной копии, хранящейся в общей папке \\\\сервернаме\шаре Server01, введите:
```
wbadmin restore catalog -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>Дополнительные материалы

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
-   Командлет [RESTORE-вбкаталог](https://technet.microsoft.com/library/jj902437.aspx)