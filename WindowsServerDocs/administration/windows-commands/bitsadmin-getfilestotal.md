---
title: bitsadmin getfilestotal
description: Раздел Windows команды для **bitsadmin getfilestotal** -извлекает число файлов в указанное задание.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 21240cfa1f0fa1f8e8fc3d2acf83f5df80812816
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59857465"
---
# <a name="bitsadmin-getfilestotal"></a>bitsadmin getfilestotal



Возвращает число файлов в указанное задание.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetFilesTotal <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается число файлов, которые включены в задание с именем *myDownloadJob*.
```
C:\>bitsadmin /GetFilesTotal myDownloadJob
```

##

[Синтаксис командной строки Key](command-line-syntax-key.md) см. также