---
title: bitsadmin setnotifycmdline
description: Раздел Windows команды для ***-bitsadmin setnotifycmdlineSets команду командной строки, который будет выполняться после завершения задания передачи данных, или когда задание переходит в состояние.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 415ae6ef-8549-48b2-9693-2368a6e24075
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f1cea4e99cbaaf3881c6f436bdb932090ad6b006
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59859075"
---
# <a name="bitsadmin-setnotifycmdline"></a>bitsadmin setnotifycmdline

Задает команду командной строки, который будет выполняться после завершения задания передачи данных, или когда задание переходит в состояние.

**БИТЫ 1.2 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetNotifyCmdLine <Job> <ProgramName> [ProgramParameters]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|ProgramName|Имя команды для выполнения после завершения задания.|
|ProgramParameters|Параметры, которые вы хотите передать *ProgramName*.|

## <a name="remarks"></a>Примечания

Можно указать значение NULL для *ProgramName* и *ProgramParameters*. Если *ProgramName* имеет значение NULL, *ProgramParameters* должен иметь значение NULL.

> [!IMPORTANT]
> Если *ProgramParameters* не NULL, то первый параметр в *ProgramParameters* должно соответствовать *ProgramName*.

## <a name="BKMK_examples"></a>Примеры

В следующем примере задается команда командной строки, используемые службой для запуска блокнота, когда задание с именем *myDownloadJob* завершения.
```
C:\>bitsadmin /SetNotifyCmdLine myDownloadJob c:\winnt\system32\notepad.exe NULL
```
```
C:\>bitsadmin /SetNotifyCmdLine myDownloadJob c:\winnt\system32\notepad.exe "notepad c:\eula.txt"
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)