---
title: битсадмин жетмаксдовнлоадтиме
description: Раздел команд Windows для **битсадмин жетмаксдовнлоадтиме** — получает время ожидания загрузки в секундах.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdce64f6-7125-489d-be3c-4af1dfc8c46a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 39a19f86e97c1a525b5beb0c5f3b23dff349cb19
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381585"
---
# <a name="bitsadmin-getmaxdownloadtime"></a>битсадмин жетмаксдовнлоадтиме

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Возвращает время ожидания загрузки в секундах.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetMaxDownloadtime <Job> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

-   N\/A

## <a name="BKMK_examples"></a>Примеров
В следующем примере возвращается максимальное время загрузки для задания с именем *мидовнлоаджоб* в секундах.

```
C:\>bitsadmin /GetMaxDownloadtime myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)


