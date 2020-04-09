---
title: развернуть виртуальный диск
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ae547b4-3813-4b86-bacd-bc273c028a2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 272714372a35f7f205b5a2e70cb2f2669b3a0634
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844897"
---
# <a name="expand-vdisk"></a>развернуть виртуальный диск

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
>   ## <a name="examples"></a><a name=BKMK_Examples></a>Примеров
>   Чтобы расширить выбранный виртуальный жесткий диск до 20 ГБ, введите:
>   ```
>   expand vdisk maximum=20000
>   ```
>   ## <a name="additional-references"></a>Дополнительные материалы
> - - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
> - [подключить виртуальный диск](attach-vdisk.md)
> - [Compact VDISK](compact-vdisk.md)

-   [Отсоединить виртуальный диск](detach-vdisk.md)
-   [подробные сведения VDISK](detail-vdisk.md)
-   [Слияние VDISK](merge-vdisk.md)
-   [выбрать виртуальный диск](select-vdisk.md)
-   [list_1](list_1.md)
