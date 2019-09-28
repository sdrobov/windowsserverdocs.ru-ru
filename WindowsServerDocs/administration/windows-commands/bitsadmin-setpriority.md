---
title: bitsadmin setpriority
description: Раздел команд Windows для **битсадмин SetPriority** — задает приоритет указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90788363-01a2-4d7c-a560-a3eba45b5e9e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 60564350928f917ca1861684e042304d5d380426
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380438"
---
# <a name="bitsadmin-setpriority"></a>bitsadmin setpriority



Задает приоритет указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetPriority <Job> <Priority>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Priority|Принимает одно из следующих значений:</br>— ПЕРЕДНИЙ ПЛАН</br>-ВЫСОКИЙ</br>— ОБЫЧНАЯ</br>-НИЗКИЙ УРОВЕНЬ|

## <a name="BKMK_examples"></a>Примеров

В следующем примере задается приоритет для задания с именем *мидовнлоаджоб* в значение Обычная.
```
C:\>bitsadmin /SetPriority myDownloadJob NORMAL
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)