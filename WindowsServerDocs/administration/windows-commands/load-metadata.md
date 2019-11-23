---
title: Загрузить метаданные
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c535487-668b-44fc-babb-ff59cf7d190e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 025f75743d61889c4b987e9a2a575d1c599f04c1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374623"
---
# <a name="load-metadata"></a>Загрузить метаданные



Загружает файл metadata. cab перед импортом транспортной теневой копии или загружает метаданные модуля записи в случае восстановления. Если используется без параметров, при **загрузке метаданных** в командной строке отображается справка.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
load metadata [<Drive>:][<Path>]<MetaData.cab>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[\<диска >:] [<Path>]|Указывает расположение файла метаданных.|
|MetaData. cab|Указывает файл metadata. cab для загрузки.|

## <a name="remarks"></a>Замечания

-   С помощью команды **Import** можно импортировать транспортную теневую копию на основе метаданных, указанных в параметре **загрузить метаданные**.
-   Эта команда необходима перед командой **Begin Restore** , чтобы загрузить выбранные модули записи и компоненты для восстановления.

## <a name="BKMK_examples"></a>Примеров

Чтобы загрузить файл метаданных с именем Metafile. cab из расположения по умолчанию, введите:
```
load metadata metafile.cab
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)