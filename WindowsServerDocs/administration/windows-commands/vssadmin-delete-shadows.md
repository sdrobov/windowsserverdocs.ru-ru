---
title: Vssadmin удаление теней
description: Описание команды vssadmin Delete Shadows.
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 05/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: 84135624377f589417c7524c40375ed8470d3269
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86954797"
---
# <a name="vssadmin-delete-shadows"></a>Vssadmin удаление теней

> Область применения: Windows 10, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Удаляет теневые копии указанного тома.

## <a name="syntax"></a>Синтаксис

```PowerShell
vssadmin delete shadows /for=<ForVolumeSpec> [/oldest | /all | /shadow=<ShadowID>] [/quiet]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---|---|
|/фор =\<ForVolumeSpec>|Указывает, какой из теневых копий тома будет удален.|
|/олдест|Удаляет только самую старую теневую копию.|
|/all|Удаляет все заданные теневые копии тома.|
|/Шадов =\<ShadowID>|Удаляет теневую копию, указанную параметром Шадовид. Чтобы получить идентификатор теневой копии, используйте команду **vssadmin List Shadows** . При вводе идентификатора теневой копии используйте следующий формат, где каждый *X* представляет шестнадцатеричный символ:<br><br>XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX|
|/quiet|Указывает, что команда не будет отображать сообщения во время выполнения.|

## <a name="remarks"></a>Комментарии

Удалять можно только теневые копии с типом, доступным для клиента.

## <a name="examples"></a>Примеры

Чтобы удалить самую старую теневую копию тома C, введите следующую команду:

```PowerShell
vssadmin delete shadows /for=c: /oldest
```

## <a name="additional-references"></a>Дополнительные ссылки

* [Ключ синтаксиса командной строки](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc771080(v%3dws.11))
* [List](vssadmin.md)
* [Vssadmin List Shadows](vssadmin-list-shadows.md)
