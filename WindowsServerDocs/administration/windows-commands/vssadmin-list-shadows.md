---
title: Vssadmin List Shadows
description: Описание команды vssadmin List Shadows.
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 05/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: 49bee3deac463b68fda94097bb183bcbf1c89810
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362590"
---
# <a name="vssadmin-list-shadows"></a>Vssadmin List Shadows

>Область применения: Windows 10, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Список всех существующих теневых копий указанного тома. Если эта команда используется без параметров, она отображает все теневые копии томов на компьютере в порядке, указанном в **наборе теневых копий**.

## <a name="syntax"></a>Синтаксис

```PowerShell
vssadmin list shadows [/for=<ForVolumeSpec>] [/shadow=<ShadowID>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---|---|
|/фор =\<ForVolumeSpec >|Указывает, для какого тома будут перечислены теневые копии.|
|/Шадов =\<Шадовид >|Выводит список теневых копий, заданных параметром Шадовид. Чтобы получить идентификатор теневой копии, используйте команду **vssadmin List Shadows** . При вводе идентификатора теневой копии используйте следующий формат, где каждый *X* представляет шестнадцатеричный символ:<br><br>XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX|

## <a name="additional-references"></a>Дополнительная справка

* [Ключ синтаксиса командной строки](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc771080(v%3dws.11))
* [List](vssadmin.md)