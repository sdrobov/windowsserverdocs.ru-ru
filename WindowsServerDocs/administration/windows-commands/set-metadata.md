---
title: Задание метаданных
description: Раздел команд Windows для Set metadata, который задает имя и расположение файла метаданных теневого копирования, используемого для перемещения теневых копий с одного компьютера на другой.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 67e6f60a-b42a-451a-95cf-b22ace7d50c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b5bd728650cf163f98a82ff1e6f88755c4cc1aea
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834527"
---
# <a name="set-metadata"></a>Задание метаданных

Задает имя и расположение файла метаданных теневого копирования, используемого для перемещения теневых копий с одного компьютера на другой. Если используется без параметров, **параметр SET Metadata** отображает справку в командной строке.

## <a name="syntax"></a>Синтаксис

```
set metadata [<Drive>:][<Path>]<MetaData.cab>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[\<диска >:] [<Path>]|Указывает расположение для создания файла метаданных.|
|\<> MetaData. cab|Указывает имя CAB-файла для хранения метаданных создания теневой копии.|

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)