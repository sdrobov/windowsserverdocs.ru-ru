---
title: Vssadmin удалить тени
description: Описание команда vssadmin удалить тени.
ms.prod: windows-server-threshold
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 05/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: 71119174c7fc5929eb4e1982183ba0aed7eb1735
ms.sourcegitcommit: e0479b0114eac7f232e8b1e45eeede96ccd72b26
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2018
ms.locfileid: "2082544"
---
# <a name="vssadmin-delete-shadows"></a>Vssadmin удалить тени

>Применимо к: Windows 10, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Удаляет указанный том теневой копии.

## <a name="syntax"></a>Синтаксис

```PowerShell
vssadmin delete shadows /for=<ForVolumeSpec> [/oldest | /all | /shadow=<ShadowID>] [/quiet]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---|---|
|аудио- и для = \ < Копируемый_том >|Указывает, какие тома теневой копии будут удалены.|
|аудио- и старые|Удаляет только старые копии.|
|/ all|Удаляет все теневые копии указанного тома.|
|/ shadow = \ < Номер_теневой_копии >|Удаляет теневой копии, указанного идентификатором Номер_теневой_копии. Чтобы получить идентификатор теневой копии, используйте команду **теней vssadmin списка** . При вводе ID теневой копии, используйте следующий формат, где каждый *X* представляет шестнадцатеричных знаков:<br><br>XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX|
|/ quiet|Указывает, что команда не будет отображать сообщения во время выполнения.|

## <a name="remarks"></a>Комментарии

Теневые копии можно удалить только с типом-адреса.

## <a name="examples"></a>Примеры

Чтобы удалить старые теневую копию тома C, введите следующую команду:

```PowerShell
vssadmin delete shadows /for=c: /oldest
```

## <a name="additional-references"></a>Дополнительные справочные материалы

* [Клавиша синтаксис командной строки](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc771080(v%3dws.11))
* [Vssadmin](vssadmin.md)
* [Vssadmin списка тени](vssadmin-list-shadows.md)