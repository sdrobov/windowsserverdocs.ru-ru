---
title: bitsadmin getnotifyinterface
description: Раздел Windows команды для **bitsadmin getnotifyinterface** -определяет, если другая программа зарегистрировал интерфейс обратного вызова COM для указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 40bf9dd8-b167-406a-80a6-a5a6f1b8cf7f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8316721a20cc477f9e8e15fc57b5d1c861da3ff4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868045"
---
# <a name="bitsadmin-getnotifyinterface"></a>bitsadmin getnotifyinterface

Определяет, зарегистрирован ли другая программа интерфейс обратного вызова COM (интерфейс уведомлений) для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetNotifyInterface <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Отображает ЗАРЕГИСТРИРОВАННЫЕ или не ЗАРЕГИСТРИРОВАН.

> [!NOTE]
> Это не позволяет указать программу, зарегистрировать интерфейс обратного вызова.

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается интерфейс уведомлений для задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetNotifyInterface myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)