---
title: Compact VDISK
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 40ca0820-67de-4160-b62a-e9bf63fe2790
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7efd40fa4b822636eda9f4082b5f561b452d3846
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379301"
---
# <a name="compact-vdisk"></a>Compact VDISK

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Уменьшает физический размер динамически расширяемого файла виртуального жесткого диска (VHD). Этот параметр полезен, так как при добавлении файлов динамически расширяемые виртуальные жесткие диски увеличиваются в размере, но при удалении файлов автоматическое уменьшение размера не уменьшается.
> [!NOTE]
> Эта команда применима только к Windows 7 и Windows Server 2008 R2.
> ## <a name="syntax"></a>Синтаксис
> ```
> compact vdisk
> ```
> ## <a name="remarks"></a>Примечания
> - Для выполнения этой операции необходимо выбрать динамически расширяемый виртуальный жесткий диск. Используйте команду **SELECT VDISK** , чтобы выбрать виртуальный жесткий диск и переместить фокус на него.
> - Можно сжимать только динамически расширяемые виртуальные жесткие диски, которые отсоединяются или присоединяются как доступные только для чтения.
>   ## <a name="BKMK_Examples"></a>Примеров
>   Чтобы сжать динамически расширяемый виртуальный жесткий диск, введите:
>   ```
>   compact vdisk
>   ```
>   ## <a name="additional-references"></a>Дополнительные ссылки
> - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
> - [подключить виртуальный диск](attach-vdisk.md)

-   [подробные сведения VDISK](detail-vdisk.md)
-   [Отсоединить виртуальный диск](detach-vdisk.md)
-   [развернуть виртуальный диск](expand-vdisk.md)
-   [Слияние VDISK](merge-vdisk.md)
-   [выбрать виртуальный диск](select-vdisk.md)
-   [list_1](list_1.md)
