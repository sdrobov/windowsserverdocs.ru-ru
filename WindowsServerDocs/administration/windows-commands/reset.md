---
title: сброс
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbdab44-199c-4e11-884f-e96804965c21
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0bd9b6735697cbcefdcf68dc3d4a53a6870a7a76
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59850965"
---
# <a name="reset"></a>сброс



Сбрасывает DiskShadow.exe до значений по умолчанию. **Сброс** особенно полезна в разделение комплексной DiskShadow операций, таких как **создать**, **импорта**, **резервного копирования**, или **восстановить**.

## <a name="syntax"></a>Синтаксис

```
reset
```

## <a name="remarks"></a>Примечания

-   При использовании **Сброс** команды, вы потеряете состояние с помощью команд такие как **добавить**, **задать**, **загрузить**, или **модулязаписи**. **Сброс** также освобождает интерфейсы IVssBackupComponent и теряет непостоянный теневые копии.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)