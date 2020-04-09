---
title: bitsadmin setnotifycmdline
description: Раздел команд Windows для битсадмин сетнотификмдлине, который задает команду командной строки, которая будет запускаться, когда задание завершает передачу данных или когда задание переходит в состояние.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 415ae6ef-8549-48b2-9693-2368a6e24075
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 761a7003e44e8dc15cb2dd2f1ce5a1a23be53286
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849337"
---
# <a name="bitsadmin-setnotifycmdline"></a>bitsadmin setnotifycmdline

Задает команду командной строки, которая будет запускаться, когда задание завершает передачу данных или когда задание переходит в состояние.

**BITS 1,2 и более ранних версий**: не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetNotifyCmdLine <Job> <ProgramName> [ProgramParameters]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|ProgramName|Имя команды, выполняемой по завершении задания.|
|програмпараметерс|Параметры, которые необходимо передать в *ProgramName*.|

## <a name="remarks"></a>Примечания

Для *ProgramName* и *програмпараметерс*можно указать значение null. Если *ProgramName* имеет значение null, *програмпараметерс* должен иметь значение null.

> [!IMPORTANT]
> Если *програмпараметерс* не равен null, то первый параметр в *Програмпараметерс* должен соответствовать *ProgramName*.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере задается команда командной строки, используемая службой для запуска программы «Блокнот» при завершении задания с именем *мидовнлоаджоб* .
```
C:\>bitsadmin /SetNotifyCmdLine myDownloadJob c:\winnt\system32\notepad.exe NULL
```
```
C:\>bitsadmin /SetNotifyCmdLine myDownloadJob c:\winnt\system32\notepad.exe notepad c:\eula.txt
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)