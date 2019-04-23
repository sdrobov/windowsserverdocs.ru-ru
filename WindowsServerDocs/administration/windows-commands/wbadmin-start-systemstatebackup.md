---
title: Wbadmin start systemstatebackup
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 998366c1-0a64-45e6-9ed3-4c3f5b8406f0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 591ff7caa554a892bda0bc0e888bd89a87d8b0ef
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863555"
---
# <a name="wbadmin-start-systemstatebackup"></a>Wbadmin start systemstatebackup



Создает резервную копию состояния системы на локальном компьютере и сохраняет его в указанном месте.

> [!NOTE]
> Система архивации данных Windows Server не архивировать или восстановить кустов реестра пользователя (HKEY_CURRENT_USER) в процессе резервного копирования состояния системы или восстановления состояния системы.

Чтобы выполнить архивацию состояния системы с помощью подкоманды, необходимо быть членом **операторы архива** группы или **Администраторы** группа, или должна была быть делегированы соответствующие разрешения. Кроме того, необходимо запустить **wbadmin** из командной строки с повышенными правами. (Чтобы открыть командную строку, щелкните правой кнопкой мыши **командной**, а затем нажмите кнопку **Запуск от имени администратора**.)

Примеры по использованию этого, см. в разделе [примеры](#BKMK_examples).

## <a name="syntax"></a>Синтаксис

```
wbadmin start systemstatebackup
-backupTarget:<VolumeName>
[-quiet]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-backupTarget|Указывает расположение, где будут храниться резервная копия. Место хранения требуется буква диска или тома на основе GUID формата: \\ \\? \Volume {*GUID*}.</br>Резервную копию состояния системы в общую сетевую папку на компьютере под управлением Windows Server 2008 не поддерживается. Если сервер работает под управлением Windows Server 2008 R2 или более поздней версии можно использовать команду **- backuptarget:\\\\servername\sharedFolder\**  для хранения резервных копий состояния системы.|
|-quiet|Запускает подкоманды без вывода сообщений для пользователя.|

## <a name="remarks"></a>Примечания

Сведения о сохранении резервной копии состояния системы на том, который, в свою очередь, содержит файлы состояния системы, см. в статье 944530 в базе знаний Майкрософт ([https://go.microsoft.com/fwlink/?LinkId=110439](https://go.microsoft.com/fwlink/?LinkId=110439)).

## <a name="BKMK_examples"></a>Примеры

Чтобы создать резервную копию состояния системы и сохраните его на томе f, введите следующую команду:
```
wbadmin start systemstatebackup -backupTarget:f:
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [WBADMIN](wbadmin.md)
-   [Start-WBBackup](https://technet.microsoft.com/library/jj902459.aspx) командлета