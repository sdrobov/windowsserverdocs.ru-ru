---
title: битсадмин сеткустомхеадерс
description: Раздел команд Windows для **битсадмин сеткустомхеадерс** . Добавление настраиваемого заголовка HTTP к запросу Get.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed926410-80d0-46ed-9a90-f752c164bb9a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 45e3a5178df69b84618966ca0fcd9cc1e6d0e449
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380642"
---
# <a name="bitsadmin-setcustomheaders"></a>битсадмин сеткустомхеадерс



Добавьте настраиваемый заголовок HTTP в запрос GET.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetCustomHeaders <Job> <Header1> <Header2> <. . .>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Header1 Header2 . . .|Пользовательские заголовки для задания|

## <a name="remarks"></a>Примечания

-   Этот параметр используется для добавления пользовательского заголовка HTTP к запросу GET, отправляемому на HTTP-сервер.

## <a name="BKMK_examples"></a>Примеров

В следующем примере добавляется пользовательский заголовок HTTP для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin / SetCustomHeaders myDownloadJob "Accept-encoding:deflate/gzip"
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)