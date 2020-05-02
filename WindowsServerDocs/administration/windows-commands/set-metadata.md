---
title: Задание метаданных
description: Справочный раздел по набору метаданных, который задает имя и расположение файла метаданных теневого копирования, используемого для перемещения теневых копий с одного компьютера на другой.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 67e6f60a-b42a-451a-95cf-b22ace7d50c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 683e54a7efc072d8709d6257771ba6bc5bde206e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721915"
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
|[\<Диск>:] [<Path>]|Указывает расположение для создания файла метаданных.|
|\<> MetaData. cab|Указывает имя CAB-файла для хранения метаданных создания теневой копии.|

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)