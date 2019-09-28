---
title: bitsadmin setreplyfilename
description: Раздел команд Windows для **битсадмин сетреплифиленаме** . Укажите путь к файлу, содержащему ответ сервера.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c26d3342-0533-40b1-a13e-e09678232b25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a490b5bc565549d096b6f43f42758f77570fcb26
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380423"
---
# <a name="bitsadmin-setreplyfilename"></a>bitsadmin setreplyfilename

Укажите путь к файлу, содержащему ответ сервера.

**BITS 1,2 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetReplyFileName <Job> <Path>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Path|Расположение для размещения ответа сервера|

## <a name="remarks"></a>Примечания

Допустимо только для заданий отправки и ответа.

## <a name="BKMK_examples"></a>Примеров

В следующем примере задается имя файла ответа пасфор задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /SetReplyFileName myDownloadJob c:\reply
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)