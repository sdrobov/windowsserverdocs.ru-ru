---
title: ver
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a9c6cd4-b67d-4b30-8c56-5f9798eafd2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 384a5e8adb6c8304033f7dc645184ff2b674ae39
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59887175"
---
# <a name="ver"></a>ver



Отображает номер версии операционной системы.

Эта команда поддерживается в Windows командную строку (Cmd.exe), но не в PowerShell.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
ver
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/?|Отображение справки в командной строке.|

## <a name="BKMK_examples"></a>Примеры

Чтобы получить номер версии операционной системы из командной оболочки (cmd.exe), введите следующую команду:

```
ver
```

Команда ver не работает в PowerShell. Чтобы получить версию операционной системы с помощью PowerShell, введите:

```powershell
$PSVersionTable.BuildVersion
````


#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
