---
title: Vssadmin list shadows
description: Описание vssadmin list shadows команды.
ms.prod: windows-server-threshold
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 05/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: 3601986a51e8c5b362a28c686ed132eda8e4b640
ms.sourcegitcommit: 2977c707a299929c6ab0d1e0adab2e1c644b8306
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63706565"
---
# <a name="vssadmin-list-shadows"></a>Vssadmin list shadows

>Относится к: Windows 10, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Перечислены все существующие теневые копии указанного тома. При использовании этой команды без параметров, она отображает все теневые копии тома на компьютере в том порядке, в соответствии с требованиями **набор теневого копирования**.

## <a name="syntax"></a>Синтаксис

```PowerShell
vssadmin list shadows [/for=<ForVolumeSpec>] [/shadow=<ShadowID>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---|---|
|/for=\<ForVolumeSpec>|Указывает, будут указаны теневые копии томов.|
|/shadow=\<ShadowID>|Список определяемое Номер_теневой_копии теневой копии. Чтобы получить идентификатор теневой копии, используйте **vssadmin list shadows** команды. Введите идентификатор теневой копии, используя следующий формат, где каждый *X* представляет шестнадцатеричный символ:<br><br>XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX|

## <a name="additional-references"></a>Дополнительная справка

* [Ключ синтаксиса командной строки](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc771080(v%3dws.11))
* [vssadmin](vssadmin.md)