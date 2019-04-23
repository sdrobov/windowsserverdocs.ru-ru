---
title: WBADMIN get элементов
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 27d08ce3-6e06-4260-b264-fc1bde132d09
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: eeb7c29ff552f968b4785612f626a86baf154ad7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842885"
---
# <a name="wbadmin-get-items"></a>WBADMIN get элементов



Список элементов, включенных в определенной резервной копии.

По использованию этого, необходимо быть членом **операторы архива** группы или **Администраторы** группа, или должна была быть делегированы соответствующие разрешения. Кроме того, необходимо запустить **wbadmin** из командной строки с повышенными правами. (Чтобы открыть командную строку, щелкните правой кнопкой мыши **командной** и нажмите кнопку **Запуск от имени администратора**.)

Примеры по использованию этого, см. в разделе [примеры](#BKMK_examples).

## <a name="syntax"></a>Синтаксис

```
wbadmin get items
-version:<VersionIdentifier>
[-backupTarget:{<BackupDestinationVolume> | <NetworkSharePath>}]
[-machine:<BackupMachineName>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-версии|Указывает версию резервной копии в мм/дд/гггг-формате чч: мм. Если вы не знаете сведения о версии, введите **wbadmin получить версии**.|
|-backupTarget|Задает место хранения, содержащий резервные копии, для которых требуется просмотреть сведения. Использование для получения списка резервных копий, хранящихся в этом целевом расположении. Расположение целевого объекта архивации может быть на локальном диске или удаленная общая папка. Если **wbadmin получить элементы**выполняется на том же компьютере, где была создана резервная копия, этот параметр не требуется. Тем не менее этот параметр необходим для получения сведений о резервной копии, созданной с другого компьютера.|
|-machine|Задает имя компьютера, на котором вы хотите сведения об архивации для. Полезно, когда в том же расположении будут заархивированы нескольких компьютеров. Когда следует использовать **- backupTarget** указан.|

## <a name="BKMK_examples"></a>Примеры

Для вывода списка элементов из резервной копии, выполненного на 31 марта 2013 в 9:00, тип:
```
wbadmin get items -version:03/31/2013-09:00
```
Для вывода списка элементов из резервной копии server01, который выполнялся 30 апреля 2013 г. в 9:00 и сохранена в \\ \\servername\share, тип:
```
wbadmin get items -version:04/30/2013-09:00 -backupTarget:\\servername\share -machine:server01
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [WBADMIN](wbadmin.md)
-   [Get-WBBackupSet](https://technet.microsoft.com/library/jj902473.aspx) командлета