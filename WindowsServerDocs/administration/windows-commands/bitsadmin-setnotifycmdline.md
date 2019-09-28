---
title: bitsadmin setnotifycmdline
description: Раздел команд Windows для * * * *-битсадмин Сетнотификмдлинесетс команда командной строки, которая будет выполняться, когда задание завершает передачу данных или когда задание переходит в состояние.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 7a307fe552e7d8ec5852de953a3a439cb02246ec
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380478"
---
# <a name="bitsadmin-setnotifycmdline"></a>bitsadmin setnotifycmdline

Задает команду командной строки, которая будет запускаться, когда задание завершает передачу данных или когда задание переходит в состояние.

**BITS 1,2 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetNotifyCmdLine <Job> <ProgramName> [ProgramParameters]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|ProgramName|Имя команды, выполняемой по завершении задания.|
|програмпараметерс|Параметры, которые необходимо передать в *ProgramName*.|

## <a name="remarks"></a>Примечания

Для *ProgramName* и *програмпараметерс*можно указать значение null. Если *ProgramName* имеет значение null, *програмпараметерс* должен иметь значение null.

> [!IMPORTANT]
> Если *програмпараметерс* не равен null, то первый параметр в *Програмпараметерс* должен соответствовать *ProgramName*.

## <a name="BKMK_examples"></a>Примеров

В следующем примере задается команда командной строки, используемая службой для запуска программы «Блокнот» при завершении задания с именем *мидовнлоаджоб* .
```
C:\>bitsadmin /SetNotifyCmdLine myDownloadJob c:\winnt\system32\notepad.exe NULL
```
```
C:\>bitsadmin /SetNotifyCmdLine myDownloadJob c:\winnt\system32\notepad.exe "notepad c:\eula.txt"
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)