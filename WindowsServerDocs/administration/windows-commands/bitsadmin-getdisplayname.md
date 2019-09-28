---
title: bitsadmin getdisplayname
description: Раздел команд Windows для **битсадмин-DisplayName** — извлекает отображаемое имя указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5c0e76c-4cc6-42d8-ac30-30bf3dc11b9b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 229bd245f9e810fc6aeb856bbfba253b9ab8a9f0
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381627"
---
# <a name="bitsadmin-getdisplayname"></a>bitsadmin getdisplayname



Извлекает отображаемое имя указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetDisplayName <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается отображаемое имя для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetDisplayName myDownloadJob
```
Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)