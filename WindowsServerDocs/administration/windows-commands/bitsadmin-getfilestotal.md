---
title: bitsadmin getfilestotal
description: Раздел команд Windows для **битсадмин жетфилестотал** — извлекает количество файлов в указанном задании.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5de113e-f29c-4cd3-9392-0e300018d516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e5c28d8e970bd7db896073bf8cddb168ffe9deff
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75946844"
---
# <a name="bitsadmin-getfilestotal"></a>bitsadmin getfilestotal



Извлекает количество файлов в указанном задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetFilesTotal <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается число файлов, включаемых в задание с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetFilesTotal myDownloadJob
```

## <a name="see-also"></a>См. также

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
