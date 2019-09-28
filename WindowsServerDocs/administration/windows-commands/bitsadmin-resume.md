---
title: bitsadmin resume
description: Раздел команд Windows для **битсадмин Resume** . активирует новое или приостановленное задание в очереди на перемещение.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c7540a9-a11a-4910-923a-2a2a61cbf11d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1393e959980b72de09c546ced763a506d334b56c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380768"
---
# <a name="bitsadmin-resume"></a>bitsadmin resume



Активирует новое или приостановленное задание в очереди на перемещение.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Resume <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере возобновляется задание с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /Resume myDownloadJob
```
Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)