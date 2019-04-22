---
title: bcdboot
description: Раздел Windows команды для **bcdboot** — быстро настроить системный раздел или восстановления среды загрузки, расположенной в системном разделе.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e62a250e-08e9-47f6-89d1-e6002560ab57
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 78838dd6567ad886948df8ac21425a8f9b596d5f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825885"
---
# <a name="bcdboot"></a>bcdboot



Можно быстро настроить системный раздел или для восстановления среды загрузки, расположенной в системном разделе. Системный раздел устанавливается путем копирования простого набора файлов данных конфигурации загрузки (BCD) в существующую пустую секцию.

Дополнительные сведения о BCDboot, включая сведения о том, где можно найти BCDboot и примеры использования этой команды, см. в разделе [параметры командной строки BCDboot](https://technet.microsoft.com/library/hh824874.aspx) раздела.

## <a name="syntax"></a>Синтаксис

```
bcdboot <source> [/l] [/s]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|источник|Указывает расположение каталога Windows для использования в качестве источника для копирования файлов среды загрузки.|
|/l|Задает языковой стандарт. Локаль по умолчанию является английский (США).|
|/s|Указывает букву тома системного раздела. По умолчанию используется системный раздел, идентифицируемый встроенного по.|

## <a name="BKMK_examples"></a>Примеры

Дополнительные примеры использования этой команды, см. в разделе [параметры командной строки BCDboot](https://technet.microsoft.com/library/hh824874.aspx) раздела.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)