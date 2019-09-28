---
title: ver
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: e48b3b1061edf793c88693b3353753c6a4cedcfc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362724"
---
# <a name="ver"></a>ver



Отображает номер версии операционной системы.

Эта команда поддерживается в командной строке Windows (cmd. exe), но не в PowerShell.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
ver
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/?|Отображение справки в командной строке.|

## <a name="BKMK_examples"></a>Примеров

Чтобы получить номер версии операционной системы из командной оболочки (cmd. exe), введите:

```
ver
```

Команда ver не работает в PowerShell. Чтобы получить версию ОС из PowerShell, введите:

```powershell
$PSVersionTable.BuildVersion
````


#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
