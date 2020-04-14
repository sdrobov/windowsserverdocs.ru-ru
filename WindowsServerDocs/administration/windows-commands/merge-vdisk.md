---
title: Слияние VDISK
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5865bb08-89a3-406c-8328-0ef8868d03e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1315b82510ae356f80d5b519c0676d0d156ab9fd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839627"
---
# <a name="merge-vdisk"></a>Слияние VDISK

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Объединяет разностный виртуальный жесткий диск (VHD) с соответствующим ему родительским VHD. Родительский виртуальный жесткий диск будет изменен для включения изменений из разностного виртуального жесткого диска.
> [!NOTE]
> Эта команда применима только к Windows 7 и Windows Server 2008 R2.
> ## <a name="syntax"></a>Синтаксис
> ```
> merge vdisk depth=<n>
> ```
> #### <a name="parameters"></a>Параметры
> 
> | Параметр |                                                                                    Описание                                                                                    |
> |-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
> | Depth =<n> | Указывает число родительских VHD-файлов, объединяемых вместе. Например, **Depth = 1** указывает, что разностный виртуальный жесткий диск будет объединен с одним уровнем разностной цепочки. |
> 
> ## <a name="remarks"></a>Примечания
> - Для выполнения этой операции необходимо выбрать и отсоединить виртуальный жесткий диск. Используйте команду **SELECT VDISK** , чтобы выбрать виртуальный жесткий диск и переместить фокус на него.
> - Этот параметр изменяет родительский виртуальный жесткий диск. В результате другие разностные виртуальные жесткие диски, зависящие от родительского, станут недействительными.
>   ## <a name="examples"></a><a name=BKMK_Examples></a>Примеров
>   Чтобы объединить разностный виртуальный жесткий диск с его родительским VHD, введите:
>   ```
>   merge vdisk depth=1
>   ```
>   ## <a name="additional-references"></a>Дополнительные материалы
> - - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
> - [подключить виртуальный диск](attach-vdisk.md)
> - [Compact VDISK](compact-vdisk.md)

-   [подробные сведения VDISK](detail-vdisk.md)
-   [Отсоединить виртуальный диск](detach-vdisk.md)
-   [развернуть виртуальный диск](expand-vdisk.md)
-   [выбрать виртуальный диск](select-vdisk.md)
-   [list_1](list_1.md)
