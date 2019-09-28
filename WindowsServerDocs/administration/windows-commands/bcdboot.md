---
title: bcdboot
description: Раздел команд Windows для **BCDboot** — Быстрая настройка системного раздела или восстановление среды загрузки, расположенной в системном разделе.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: a1c0f505180a503617335cc9575fea3d346bbe02
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383438"
---
# <a name="bcdboot"></a>bcdboot



Позволяет быстро настроить системный раздел или восстановить среду загрузки, расположенную в системном разделе. Системный раздел настраивается путем копирования простого набора файлов данные конфигурации загрузки (BCD) в существующий пустой раздел.

Дополнительные сведения о BCDboot, включая сведения о том, где найти BCDboot и примеры использования этой команды, см. в разделе [Параметры командной строки BCDboot](https://technet.microsoft.com/library/hh824874.aspx) .

## <a name="syntax"></a>Синтаксис

```
bcdboot <source> [/l] [/s]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|источник|Указывает расположение каталога Windows, используемого в качестве источника для копирования файлов среды загрузки.|
|/l|Задает языковой стандарт. Язык по умолчанию — английский (США).|
|/s|Указывает букву тома системного раздела. По умолчанию используется системный раздел, определяемый встроенным по.|

## <a name="BKMK_examples"></a>Примеров

Дополнительные примеры использования этой команды см. в разделе [Параметры командной строки BCDboot](https://technet.microsoft.com/library/hh824874.aspx) .

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)