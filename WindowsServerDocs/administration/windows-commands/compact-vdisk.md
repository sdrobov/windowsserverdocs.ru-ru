---
title: сжать виртуальный диск
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: c4a95354bf041777e43a9eac5f16e693b02c185c
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434302"
---
# <a name="compact-vdisk"></a>сжать виртуальный диск

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Уменьшает размер физического файла динамически расширяемый виртуальный жесткий диск (VHD). Этот параметр полезен, так как динамически Расширяемые виртуальные жесткие диски, увеличение размера, как добавить файлы, но при этом не уменьшается автоматически в размер при удалении файлов.
> [!NOTE]
> Эта команда применяется только к Windows 7 и Windows Server 2008 R2.
> ## <a name="syntax"></a>Синтаксис
> ```
> compact vdisk
> ```
> ## <a name="remarks"></a>Примечания
> - Для успешного выполнения этой операции необходимо выбрать динамически расширяемый виртуальный жесткий ДИСК. Используйте **выберите виртуальный диск** команду, чтобы выбрать виртуальный жесткий ДИСК и перетянуть внимание к нему.
> - Можно только сжатие, динамически Расширяемые виртуальные жесткие диски, отсоединена или же только для чтения.
>   ## <a name="BKMK_Examples"></a>Примеры
>   Чтобы сжать динамически расширяемый виртуальный жесткий ДИСК, введите:
>   ```
>   compact vdisk
>   ```
>   ## <a name="additional-references"></a>Дополнительные ссылки
> - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
> - [подключить виртуальный диск](attach-vdisk.md)

-   [виртуальный диск данных](detail-vdisk.md)
-   [Отсоединить виртуальный диск](detach-vdisk.md)
-   [Разверните виртуальный диск](expand-vdisk.md)
-   [Слияние виртуальный диск](merge-vdisk.md)
-   [Выберите виртуальный диск](select-vdisk.md)
-   [list_1](list_1.md)
