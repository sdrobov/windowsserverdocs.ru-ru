---
title: bitsadmin setdescription
description: Раздел команд Windows для **битсадмин SetDescription** — задает описание указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1e46a5dd-4637-4a2e-b88f-d3f85b177db8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d140ee9d575828a1a4d536073e468c9b4e56799f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380927"
---
# <a name="bitsadmin-setdescription"></a>bitsadmin setdescription



Задает описание указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetDescription <Job> <Description>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Описание|Текст, используемый для описания задания.|

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается описание задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /SetDescription myDownloadJob "Music Downloads"
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)