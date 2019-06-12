---
title: Разверните виртуальный диск
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 8019ce62d6cf38c7430a789f68749444ac91ad48
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66439438"
---
# <a name="expand-vdisk"></a>Разверните виртуальный диск

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

размер, который можно указать при развертывании виртуального жесткого диска (VHD).
> [!NOTE]
> Эта команда применяется только к Windows 7 и Windows Server 2008 R2.
> ## <a name="syntax"></a>Синтаксис
> ```
> expand vdisk maximum=<n>
> ```
> ## <a name="parameters"></a>Параметры
> 
> |  Параметр  |                      Описание                      |
> |-------------|-------------------------------------------------------|
> | Максимальное =<n> | Указывает новый размер виртуального жесткого диска в мегабайтах (МБ). |
> 
> ## <a name="remarks"></a>Примечания
> - Виртуальный жесткий ДИСК должен быть выбран и отсоединить для выполнения данной операции. Используйте **выберите виртуальный диск** команду, чтобы выбрать том и перетянуть внимание к нему.
>   ## <a name="BKMK_Examples"></a>Примеры
>   Чтобы развернуть выбранный VHD-ФАЙЛ до 20 ГБ, введите:
>   ```
>   expand vdisk maximum=20000
>   ```
>   ## <a name="additional-references"></a>Дополнительные ссылки
> - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
> - [подключить виртуальный диск](attach-vdisk.md)
> - [сжать виртуальный диск](compact-vdisk.md)

-   [Отсоединить виртуальный диск](detach-vdisk.md)
-   [виртуальный диск данных](detail-vdisk.md)
-   [Слияние виртуальный диск](merge-vdisk.md)
-   [Выберите виртуальный диск](select-vdisk.md)
-   [list_1](list_1.md)
