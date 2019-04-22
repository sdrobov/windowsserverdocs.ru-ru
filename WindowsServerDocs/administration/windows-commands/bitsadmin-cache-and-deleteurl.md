---
title: кэш bitsadmin и deleteurl
description: Раздел Windows команды для **bitsadmin кэша и deleteurl** — удаляет все записи кэша для заданного URL-адреса.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e108b76b-fae9-4c16-bf4c-d74c9f025953
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a831c49e1461761cb7466b46e7a5ad8e037f4ec9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59816655"
---
# <a name="bitsadmin-cache-and-deleteurl"></a>кэш bitsadmin и deleteurl



Удаляет все записи кэша для заданного URL-адреса.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /DeleteURL url
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|url|URL-адрес, определяющий удаленный файл.|

## <a name="BKMK_examples"></a>Примеры

Следующий пример удаляет все записи кэша для https://www.microsoft.com/en/us/default.aspx
```
C:\>bitsadmin /DeleteURL https://www.microsoft.com/en/us/default.aspx 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)