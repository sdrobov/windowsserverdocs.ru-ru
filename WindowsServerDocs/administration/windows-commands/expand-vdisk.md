---
title: развернуть виртуальный диск
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ae547b4-3813-4b86-bacd-bc273c028a2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8fb5d7b58b7aa4bc9557086c73020820cfa04284
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377295"
---
# <a name="expand-vdisk"></a>развернуть виртуальный диск

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Расширение виртуального жесткого диска (VHD) до указанного размера.
> [!NOTE]
> Эта команда применима только к Windows 7 и Windows Server 2008 R2.
> ## <a name="syntax"></a>Синтаксис
> ```
> expand vdisk maximum=<n>
> ```
> ## <a name="parameters"></a>Параметры
> 
> |  Параметр  |                      Описание                      |
> |-------------|-------------------------------------------------------|
> | максимум = <n> | Указывает новый размер виртуального жесткого диска в мегабайтах (МБ). |
> 
> ## <a name="remarks"></a>Примечания
> - Для выполнения этой операции необходимо выбрать и отсоединить виртуальный жесткий диск. Используйте команду **SELECT VDISK** , чтобы выбрать том и переместить фокус на него.
>   ## <a name="BKMK_Examples"></a>Примеров
>   Чтобы расширить выбранный виртуальный жесткий диск до 20 ГБ, введите:
>   ```
>   expand vdisk maximum=20000
>   ```
>   ## <a name="additional-references"></a>Дополнительные ссылки
> - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
> - [подключить виртуальный диск](attach-vdisk.md)
> - [Compact VDISK](compact-vdisk.md)

-   [Отсоединить виртуальный диск](detach-vdisk.md)
-   [подробные сведения VDISK](detail-vdisk.md)
-   [Слияние VDISK](merge-vdisk.md)
-   [выбрать виртуальный диск](select-vdisk.md)
-   [list_1](list_1.md)
