---
title: bitsadmin util и repairservice
description: Раздел Windows команды для **bitsadmin util и repairservice** -команда используется для устранения известных проблем в различных версиях службы BITS.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: bc5101378a389c865f5753146b711be0d15c6785
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852095"
---
# <a name="bitsadmin-util-and-repairservice"></a>bitsadmin util и repairservice

Если бит не запускается, этот параметр можно используйте для устранения известных проблем в различных версиях BITS.

**BITSAdmin 1.5 и более ранних версий:** не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Util /RepairService [/Force]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Force|Необязательно — удаляет и воссоздает службы.|

## <a name="remarks"></a>Примечания

Этот параметр устраняет ошибки связаны с неверными службы конфигурации и зависимостей от службы Windows (например, LANManworkstation) и сетевому каталогу. Этот параметр создает выходные данные, указывает, если проблемы, устраненные.

> [!NOTE]
> Если бит воссоздает службы, строку описания службы может быть присвоено английский в локализованной системе.

> [!IMPORTANT]
> Эта команда не поддерживается в Windows Vista.

## <a name="BKMK_examples"></a>Примеры

В следующем примере исправляется конфигурация службы BITS.
```
C:\>bitsadmin /Util /RepairService
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)