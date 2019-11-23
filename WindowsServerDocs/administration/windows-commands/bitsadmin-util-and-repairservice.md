---
title: битсадмин util и репаирсервице
description: Раздел команд Windows для **битсадмин util и репаирсервице** -Command, используемый для устранения известных проблем с различными ВЕРСИЯМИ службы BITS.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2ac7baeb-4340-4186-bfcb-66478195378d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0ab06ac9c784cfa438eb285c28f0e661cf4b8302
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380278"
---
# <a name="bitsadmin-util-and-repairservice"></a>битсадмин util и репаирсервице

Если не удается запустить службу BITS, используйте этот параметр для устранения известных проблем с различными версиями BITS.

**Битсадмин 1,5 и более ранних версий:**  не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Util /RepairService [/Force]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Force|Необязательно — удаляет и повторно создает службу.|

## <a name="remarks"></a>Замечания

Этот параметр разрешает ошибки, связанные с неправильной конфигурацией службы и зависимостями в службах Windows (например, LANManworkstation) и в сетевом каталоге. Этот параметр создает выходные данные, которые указывают, разрешены ли проблемы.

> [!NOTE]
> Если служба BITS повторно создает службу, в локализованной системе в качестве строки описания службы может быть задан английский язык.

> [!IMPORTANT]
> Эта команда не поддерживается в Windows Vista.

## <a name="BKMK_examples"></a>Примеров

В следующем примере восстанавливается конфигурация службы BITS.
```
C:\>bitsadmin /Util /RepairService
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)