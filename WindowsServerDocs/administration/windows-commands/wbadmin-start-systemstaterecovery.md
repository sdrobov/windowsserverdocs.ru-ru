---
title: Wbadmin start systemstaterecovery
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 208b1be9-3452-4aba-bb49-46bc587fca96
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4282da2011c39daec0315a7f3836d5517f29debb
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440202"
---
# <a name="wbadmin-start-systemstaterecovery"></a>Wbadmin start systemstaterecovery



Выполняет восстановление состояния системы в расположение, а также из резервной копии, можно указать.

> [!NOTE]
> Система архивации данных Windows Server не архивировать или восстановить кустов реестра пользователя (HKEY_CURRENT_USER) в процессе резервного копирования состояния системы или восстановления состояния системы.

Для выполнения восстановления состояния системы с помощью подкоманды, необходимо быть членом **операторы архива** группы или **Администраторы** группа, или должна была быть делегированы соответствующие разрешения. Кроме того, необходимо запустить **wbadmin** из командной строки с повышенными правами. (Чтобы открыть командную строку, щелкните правой кнопкой мыши **командной**, а затем нажмите кнопку **Запуск от имени администратора**.)

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

Синтаксис для Windows Server 2008:
```
wbadmin start systemstaterecovery
-version:<VersionIdentifier>
-showsummary
[-backupTarget:{<BackupDestinationVolume> | <NetworkSharePath>}]
[-machine:<BackupMachineName>]
[-recoveryTarget:<TargetPathForRecovery>]
[-authsysvol]
[-quiet]
```
Синтаксис для Windows Server 2008 R2 или более поздней версии:
```
wbadmin start systemstaterecovery
-version:<VersionIdentifier>
-showsummary
[-backupTarget:{<BackupDestinationVolume> | <NetworkSharePath>}]
[-machine:<BackupMachineName>]
[-recoveryTarget:<TargetPathForRecovery>]
[-authsysvol]
[-autoReboot]
[-quiet]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-версии|Задает идентификатор версии для резервного копирования для восстановления в мм/дд/гггг-формате чч: мм. Если вы не знаете идентификатор версии, введите **wbadmin получить версии**.|
|-showsummary|Сообщает сводку последнего восстановления состояния системы (после перезагрузки, необходимые для завершения операции). Этот параметр не может сопровождаться других параметров.|
|-backupTarget|Задает место хранения, содержащий резервные копии, которые вы хотите восстановить. Этот параметр полезен в тех случаях, когда место хранения отличается от обычно хранения резервных копий этого компьютера.|
|-machine|Задает имя компьютера, на котором вы хотите восстановить. Этот параметр полезен в тех случаях, когда в том же расположении будут заархивированы нескольких компьютеров. Когда следует использовать **- backupTarget** указан параметр.|
|-recoveryTarget|Указывает каталог для восстановления. Этот параметр полезен, если резервная копия восстанавливается в альтернативное расположение.|
|-authsysvol|При использовании выполняет принудительное восстановление SYSVOL (системный том общий каталог).|
|-autoReboot|Указывает перезапустить систему в конце операции восстановления состояния системы. Этот параметр допустим только для восстановления в исходное расположение. Мы не рекомендуем использовать этот параметр, если необходимо выполнить действия после операции восстановления.|
|-quiet|Запускает подкоманды без вывода сообщений для пользователя.|

## <a name="BKMK_examples"></a>Примеры

- Чтобы выполнить восстановление состояния системы из резервной копии с 03/31/2013, в 9:00, введите следующую команду:  
  ```
  wbadmin start systemstaterecovery -version:03/31/2013-09:00
  ```  
- Для выполнения восстановления состояния системы из резервной копии из 04/30/2013, в 9:00 который хранится в общем ресурсе \\ \\servername\share для server01, введите:  
  ```
  wbadmin start systemstaterecovery -version:04/30/2013-09:00 -backupTarget:\\servername\share -machine:server01
  ```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [WBADMIN](wbadmin.md)
-   [Start-WBSystemStateRecovery](https://technet.microsoft.com/library/jj902449.aspx) командлета