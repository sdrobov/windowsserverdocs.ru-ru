---
title: WBADMIN восстановления каталога
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 5876a44b178025baac7ee5901cdc32c1b5d33dad
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59851715"
---
# <a name="wbadmin-restore-catalog"></a>WBADMIN восстановления каталога



Восстановление каталога резервного копирования для локального компьютера из места хранения вами.

Восстановление каталога резервного копирования с помощью подкоманды, необходимо быть членом **операторы архива** группы или **Администраторы** группа, или должна была быть делегированы соответствующие разрешения. Кроме того, необходимо запустить **wbadmin** из командной строки с повышенными правами. (Чтобы открыть командную строку, щелкните правой кнопкой мыши **командной**, а затем нажмите кнопку **Запуск от имени администратора**.)

Примеры по использованию этого, см. в разделе [примеры](#BKMK_examples).

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
|-backupTarget|Указывает расположение каталога резервных копий системы, так как она была в точке после создания резервной копии.|
|-machine|Задает имя компьютера, на котором необходимо выполнить восстановление каталога резервных копий для. Используется, если там же, где хранятся резервные копии на нескольких компьютерах. Когда следует использовать **- backupTarget** указан.|
|-quiet|Запускает подкоманды без вывода сообщений для пользователя.|

## <a name="remarks"></a>Примечания

Если повреждена или утеряна расположение (диск, DVD-ДИСК или удаленная общая папка), где хранить резервные копии и не может использоваться для восстановления каталога резервных копий, использовать **wbadmin удалить каталог** удалить каталог поврежден. В этом случае следует создать новую резервную копию после удаления каталога резервного копирования.

## <a name="BKMK_examples"></a>Примеры

Чтобы восстановить каталог из резервной копии, хранящейся на диске d:, введите:
```
wbadmin restore catalog -backupTarget:d
```
Для восстановления из резервной копии в общей папке каталога \\ \\servername\share из server01, введите:
```
wbadmin restore catalog -backupTarget:\\servername\share -machine:server01
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [WBADMIN](wbadmin.md)
-   [Восстановление WBCatalog](https://technet.microsoft.com/library/jj902437.aspx) командлета