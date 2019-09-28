---
title: bitsadmin getfilestransferred
description: Раздел команд Windows для **битсадмин жетфилестрансферред** — получает количество файлов, переданных для указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e282815c-938b-4ac0-a09d-9baafb656dcb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d02d9d7bc216a5ad7ca922e716c368f64c4b9a44
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381598"
---
# <a name="bitsadmin-getfilestransferred"></a>bitsadmin getfilestransferred



Возвращает количество файлов, переданных для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetFilesTransferred <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается число файлов, передаваемых в задании с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetFilesTransferred myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)