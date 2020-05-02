---
title: развернуть виртуальный диск
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ae547b4-3813-4b86-bacd-bc273c028a2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c2380045de45397888777f58e3420c75bb6915ae
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725695"
---
# <a name="expand-vdisk"></a>развернуть виртуальный диск

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Расширение виртуального жесткого диска (VHD) до указанного размера.
> [!NOTE]
> Эта команда применима только к Windows 7 и Windows Server 2008 R2.
> ## <a name="syntax"></a>Синтаксис
> ```
> expand vdisk maximum=<n>
> ```
> ### <a name="parameters"></a>Параметры
> 
> |  Параметр  |                      Описание                      |
> |-------------|-------------------------------------------------------|
> | максимум =<n> | Указывает новый размер виртуального жесткого диска в мегабайтах (МБ). |
> 
> ## <a name="remarks"></a>Примечания
> - Для выполнения этой операции необходимо выбрать и отсоединить виртуальный жесткий диск. Используйте команду **SELECT VDISK** , чтобы выбрать том и переместить фокус на него.
>   ## <a name="examples"></a>Примеры
>   Чтобы расширить выбранный виртуальный жесткий диск до 20 ГБ, введите:
>   ```
>   expand vdisk maximum=20000
>   ```
>   ## <a name="additional-references"></a>Дополнительные ссылки
> - - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
> - [подключить виртуальный диск](attach-vdisk.md)
> - [Compact VDISK](compact-vdisk.md)

-   [Отсоединить виртуальный диск](detach-vdisk.md)
-   [подробные сведения VDISK](detail-vdisk.md)
-   [Слияние VDISK](merge-vdisk.md)
-   [выбрать виртуальный диск](select-vdisk.md)
-   [list_1](list_1.md)
