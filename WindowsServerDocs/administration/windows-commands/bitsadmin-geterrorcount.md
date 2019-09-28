---
title: bitsadmin geterrorcount
description: Раздел команд Windows для **битсадмин жетерроркаунт** — извлекает количество раз, когда указанное задание создало временную ошибку.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8840ae78-52b0-4c7e-b592-0547359a237e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2e5aa64c0e080e946e84c0bf804527bb00cad70a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381617"
---
# <a name="bitsadmin-geterrorcount"></a>bitsadmin geterrorcount



Извлекает число раз, когда указанное задание создало временную ошибку.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetErrorCount <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается информация о количестве ошибок для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetErrorCount myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)