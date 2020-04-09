---
title: ver
description: Раздел команд Windows для ver, в котором отображается номер версии операционной системы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5a9c6cd4-b67d-4b30-8c56-5f9798eafd2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d0d0676dcfa6546e4bbf74c4c58a24f51744d00f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830197"
---
# <a name="ver"></a>ver



Отображает номер версии операционной системы.

Эта команда поддерживается в командной строке Windows (cmd. exe), но не в PowerShell.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
ver
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/?|Отображает справку в командной строке.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы получить номер версии операционной системы из командной оболочки (cmd. exe), введите:

```
ver
```

Команда ver не работает в PowerShell. Чтобы получить версию ОС из PowerShell, введите:

```powershell
$PSVersionTable.BuildVersion
````


## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
