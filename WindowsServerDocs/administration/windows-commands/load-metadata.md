---
title: Загрузить метаданные
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: b52b5040fc8c834b04cad83ca4b0cfab103fdc43
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59871335"
---
# <a name="load-metadata"></a>Загрузить метаданные



Загружает метаданные CAB-файл перед импортом переносимой теневой копии или загружает метаданные модуля записи в случае восстановления. При использовании без параметров, **загрузить метаданные** отображает справку в командной строке.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
load metadata [<Drive>:][<Path>]<MetaData.cab>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[\<Диска >:] [<Path>]|Указывает расположение файла метаданных.|
|MetaData.cab|Указывает метаданные CAB-файл для загрузки.|

## <a name="remarks"></a>Примечания

-   Можно использовать **импорта** команду, чтобы импортировать переносимой теневой копии на основе метаданных, определяемое **загрузить метаданные**.
-   Эта команда необходима перед **начать восстановление** команду, чтобы загрузить выбранные записи и компоненты для восстановления.

## <a name="BKMK_examples"></a>Примеры

Чтобы загрузить файл метаданных с именем metafile.cab из расположения по умолчанию, введите следующую команду:
```
load metadata metafile.cab
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)