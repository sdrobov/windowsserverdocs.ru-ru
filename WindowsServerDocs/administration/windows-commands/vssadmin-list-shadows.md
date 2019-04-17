---
title: Vssadmin списка тени
description: Описание списка vssadmin скрывает команду.
ms.prod: windows-server-threshold
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 05/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: 07da36da1473563c3236a4fafc3ceae06259981a
ms.sourcegitcommit: e0479b0114eac7f232e8b1e45eeede96ccd72b26
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2018
ms.locfileid: "2082635"
---
# <a name="vssadmin-list-shadows"></a>Vssadmin списка тени

>Применимо к: Windows 10, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Список всех существующих теневая копия указанного тома. При выполнении команды без параметров, отображает все теневые копии на компьютере, в том порядке, зависит от **Задать теневой копии**.

## <a name="syntax"></a>Синтаксис

```PowerShell
vssadmin list shadows [/for=<ForVolumeSpec>] [/shadow=<ShadowID>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---|---|
|аудио- и для = \ < Копируемый_том >|Указывает, будут отображены теневые копии для томов.|
|/ shadow = \ < Номер_теневой_копии >|Список теневой копии, указанного идентификатором Номер_теневой_копии. Чтобы получить идентификатор теневой копии, используйте команду **теней vssadmin списка** . При вводе ID теневой копии, используйте следующий формат, где каждый *X* представляет шестнадцатеричных знаков:<br><br>XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX|

## <a name="additional-references"></a>Дополнительные справочные материалы

* [Клавиша синтаксис командной строки](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc771080(v%3dws.11))
* [Vssadmin](vssadmin.md)