---
title: bitsadmin cancel
description: Раздел Windows команды для **bitsadmin отменить** — производится удаление задания из очереди передачи и удаляет все временные файлы, связанные с заданием.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7374b544-6a16-4d3e-872c-dcf4c02ad89d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0a4d1e2d6e4fd66cb525316f236d070fcd72d73f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814075"
---
# <a name="bitsadmin-cancel"></a>bitsadmin cancel

Удаляет задания из очереди передачи и удаляет все временные файлы, связанные с заданием.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /cancel <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

В следующем примере удаляется *myDownloadJob* задания из очереди передачи.
```
C:\>bitsadmin /cancel myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)