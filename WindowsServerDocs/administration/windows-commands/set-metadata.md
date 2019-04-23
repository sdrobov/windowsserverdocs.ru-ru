---
title: Метаданные набора
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 67e6f60a-b42a-451a-95cf-b22ace7d50c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 82d2cd9ba447a0ea261f91dc01c11e45dfc0aa9b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59835995"
---
# <a name="set-metadata"></a>Метаданные набора



Задает имя и расположение файла метаданных создания тени, используется для передачи теневые копии с одного компьютера на другой. При использовании без параметров, **задать метаданные** отображает справку в командной строке.

## <a name="syntax"></a>Синтаксис

```
set metadata [<Drive>:][<Path>]<MetaData.cab>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[\<Диска >:] [<Path>]|Указывает расположение для создания файла метаданных.|
|\<MetaData.cab >|Указывает имя CAB-файл для хранения метаданных создания тени.|

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)