---
title: Vssadmin изменение размера шадовстораже
description: Описание команды vssadmin Resize шадовстораже.
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 03/05/2020
ms.localizationpriority: medium
ms.openlocfilehash: 05e58498a59a9e87fc773428d7e5956ce3285b67
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720245"
---
# <a name="vssadmin-resize-shadowstorage"></a>Vssadmin изменение размера шадовстораже

> Область применения: Windows 10, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Изменяет максимальный объем дискового пространства, который можно использовать для хранения теневых копий.

Минимальный объем дискового пространства, который можно использовать для хранения теневых копий, можно указать с помощью значения реестра **миндиффареафилесизе** . Дополнительные сведения см. в разделе [миндиффареафилесизе](https://docs.microsoft.com/windows/win32/backup/registry-keys-for-backup-and-restore#mindiffareafilesize).

> [!WARNING]
> Изменение размера связи хранилища может привести к исчезновению теневых копий.

## <a name="syntax"></a>Синтаксис

```cmd
vssadmin resize shadowstorage /for=<ForVolumeSpec> /on=<OnVolumeSpec> [/maxsize=<MaxSizeSpec>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---|---|
`/for=<ForVolumeSpec>`  | Указывает том, для которого необходимо изменить размер пространства в хранилище.
`/on=<OnVolumeSpec>` | Указывает том хранилища.
`[/maxsize=<MaxSizeSpec>]` |  Указывает максимальный объем пространства, который может использоваться для хранения теневых копий. Если для/макссизе не указано значение, ограничение на объем хранилища, которое можно использовать, не ограничено.  <br> <br> Значение Макссизеспек должно быть не меньше 1 МБ и должно быть выражено в одном из следующих единиц: КБ, МБ, ГБ, ТБ, PB или EB. Если единица не указана, Макссизеспек использует байты по умолчанию.

## <a name="examples"></a>Примеры

```cmd
vssadmin Resize ShadowStorage /For=C: /On=D: /MaxSize=900MB
vssadmin Resize ShadowStorage /For=C: /On=D: /MaxSize=UNBOUNDED
vssadmin Resize ShadowStorage /For=C: /On=C: /MaxSize=20%
```

## <a name="additional-references"></a>Дополнительная справка

* [Ключ синтаксиса командной строки](https://docs.microsoft.com/windows-server/administration/windows-commands/command-line-syntax-key)
* [List](vssadmin.md)
