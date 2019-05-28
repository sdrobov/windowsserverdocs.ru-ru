---
title: кэш bitsadmin и setexpirationtime
description: Раздел Windows команды для **bitsadmin кэша и setexpirationtime** -задает время истечения срока действия кэша.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 00ea6e4e-b707-4b31-88dd-b61a78565c8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8e896df0a88c0cfc4eec07aba4807f184e7abe32
ms.sourcegitcommit: b190fac4bfa5599751a60d3fc3b4c4a64dd9afd7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66008936"
---
>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

# <a name="bitsadmin-cache-and-setexpirationtime"></a>кэш bitsadmin и setexpirationtime
Задает время истечения срока действия кэша.
## <a name="syntax"></a>Синтаксис
```
bitsadmin /Cache /SetExpirationtime secs
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|сек|Количество секунд до истечения срока действия кэша.|
## <a name="BKMK_examples"></a>Примеры
Следующий пример кэша истекает через 60 секунд.
```
C:\>bitsadmin /Cache / SetExpirationtime 60
```
## <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
