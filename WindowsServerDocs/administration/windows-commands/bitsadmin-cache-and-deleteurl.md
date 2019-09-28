---
title: кэш битсадмин и делетеурл
description: Раздел команд Windows для **кэша битсадмин и делетеурл** — удаляет все записи кэша для данного URL-адреса.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 869d3bc0f011cc82aaea9b7468667964051e1c00
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382060"
---
# <a name="bitsadmin-cache-and-deleteurl"></a>кэш битсадмин и делетеурл



Удаляет все записи кэша для заданного URL-адреса.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /DeleteURL url
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|url|Универсальный указатель ресурсов, определяющий удаленный файл.|

## <a name="BKMK_examples"></a>Примеров

В следующем примере удаляются все записи кэша для https://www.microsoft.com/en/us/default.aspx.
```
C:\>bitsadmin /DeleteURL https://www.microsoft.com/en/us/default.aspx 
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)