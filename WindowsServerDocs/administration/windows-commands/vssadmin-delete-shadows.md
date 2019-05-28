---
title: Vssadmin delete shadows
description: Описание команды shadows vssadmin delete.
ms.prod: windows-server-threshold
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 05/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: 83074017e4ae412cf0aec654f6ab5901ad8039e2
ms.sourcegitcommit: 2977c707a299929c6ab0d1e0adab2e1c644b8306
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63706618"
---
# <a name="vssadmin-delete-shadows"></a>Vssadmin delete shadows

>Относится к: Windows 10, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Удаляет указанного тома теневых копий.

## <a name="syntax"></a>Синтаксис

```PowerShell
vssadmin delete shadows /for=<ForVolumeSpec> [/oldest | /all | /shadow=<ShadowID>] [/quiet]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---|---|
|/for=\<ForVolumeSpec>|Указывает, какие тома теневой копии будут удалены.|
|/ старой|Удаляет только самая старая теневая копия.|
|/ all|Удаляет все теневых копий указанного тома.|
|/shadow=\<ShadowID>|Удаляет заданные Номер_теневой_копии теневую копию. Чтобы получить идентификатор теневой копии, используйте **vssadmin list shadows** команды. Когда пользователь вводит идентификатор теневой копии, используйте следующий формат, где каждый *X* представляет шестнадцатеричный символ:<br><br>XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX|
|/ quiet|Указывает, что команда не будет отображать сообщения во время выполнения.|

## <a name="remarks"></a>Примечания

Теневые копии можно удалить только с типом доступно клиентам.

## <a name="examples"></a>Примеры

Чтобы удалить самая старая теневая копия тома C, введите следующую команду:

```PowerShell
vssadmin delete shadows /for=c: /oldest
```

## <a name="additional-references"></a>Дополнительная справка

* [Ключ синтаксиса командной строки](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc771080(v%3dws.11))
* [vssadmin](vssadmin.md)
* [Vssadmin list shadows](vssadmin-list-shadows.md)