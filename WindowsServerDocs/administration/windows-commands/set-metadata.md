---
title: Задание метаданных
description: Справочная статья по заданию метаданных, которая задает имя и расположение файла метаданных теневого копирования, используемого для перемещения теневых копий с одного компьютера на другой.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 67e6f60a-b42a-451a-95cf-b22ace7d50c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 50c9ceebf072db2e7cefada1601accc97b5d0f7f
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85937093"
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
|[\<Drive>:][<Path>]|Указывает расположение для создания файла метаданных.|
|\<MetaData.cab>|Указывает имя CAB-файла для хранения метаданных создания теневой копии.|

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)