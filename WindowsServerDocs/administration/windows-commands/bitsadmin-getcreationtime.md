---
title: bitsadmin getcreationtime
description: Раздел команд Windows для **битсадмин жеткреатионтиме** — получение времени создания для указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: be409cb5-ce72-41d9-aafa-edd4e230fd14
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2ea92133c90e20e37e5d281116e91bf1f109e83f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381691"
---
# <a name="bitsadmin-getcreationtime"></a>bitsadmin getcreationtime



Извлекает время создания для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetCreationTime <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается время создания задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetCreationTime myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)