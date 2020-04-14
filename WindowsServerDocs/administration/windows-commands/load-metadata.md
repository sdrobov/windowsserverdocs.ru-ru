---
title: Загрузить метаданные
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2c535487-668b-44fc-babb-ff59cf7d190e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b8db98611fd78c6e30070901effafddd6e678c16
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841027"
---
# <a name="load-metadata"></a>Загрузить метаданные



Загружает файл metadata. cab перед импортом транспортной теневой копии или загружает метаданные модуля записи в случае восстановления. Если используется без параметров, при **загрузке метаданных** в командной строке отображается справка.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
load metadata [<Drive>:][<Path>]<MetaData.cab>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[\<диска >:] [<Path>]|Указывает расположение файла метаданных.|
|MetaData. cab|Указывает файл metadata. cab для загрузки.|

## <a name="remarks"></a>Примечания

-   С помощью команды **Import** можно импортировать транспортную теневую копию на основе метаданных, указанных в параметре **загрузить метаданные**.
-   Эта команда необходима перед командой **Begin Restore** , чтобы загрузить выбранные модули записи и компоненты для восстановления.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы загрузить файл метаданных с именем Metafile. cab из расположения по умолчанию, введите:
```
load metadata metafile.cab
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)