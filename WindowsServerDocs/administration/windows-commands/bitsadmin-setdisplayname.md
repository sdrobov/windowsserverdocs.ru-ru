---
title: bitsadmin setdisplayname
description: Раздел команд Windows для **битсадмин сетдисплайнаме** — задает отображаемое имя указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 13706c53-fb5f-4879-b5ca-82531361d6e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 10a5607eb26f8199ec415a4cec17d03015a26bcd
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380632"
---
# <a name="bitsadmin-setdisplayname"></a>bitsadmin setdisplayname



Задает отображаемое имя указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetDisplayName <Job> <DisplayName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|DisplayName|Текст, используемый для отображаемого имени указанного задания.|

## <a name="BKMK_examples"></a>Примеров

В следующем примере задается отображаемое имя для задания с именем *мидовнлоаджоб* в *myDownloadJob2*.
```
C:\>bitsadmin /SetDisplayName myDownloadJob "Download Music Job"
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)