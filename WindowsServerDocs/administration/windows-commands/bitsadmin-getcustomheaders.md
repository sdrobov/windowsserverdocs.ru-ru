---
title: битсадмин жеткустомхеадерс
description: Раздел команд Windows для **битсадмин жеткустомхеадерс** — извлекает из задания пользовательские заголовки HTTP.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f0d38d3-e865-4474-81e8-773d65c3d1cc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 039669fca42803ff22eb4e3d13dfdef5f0a06f93
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381658"
---
# <a name="bitsadmin-getcustomheaders"></a>битсадмин жеткустомхеадерс



Извлекает из задания пользовательские заголовки HTTP.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetCustomHeaders <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере показано получение пользовательских заголовков для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetCustomHeaders myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)