---
title: bitsadmin getfilestransferred
description: Раздел Windows команды для **bitsadmin getfilestransferred** -извлекает количество файлов, переданных для указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 5df7f2abfdad6780878b1f00da44c772eecf9fba
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59822265"
---
# <a name="bitsadmin-getfilestransferred"></a>bitsadmin getfilestransferred



Возвращает число файлов, переданных для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetFilesTransferred <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается число файлов, передаваемых в задании с именем *myDownloadJob*.
```
C:\>bitsadmin /GetFilesTransferred myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)