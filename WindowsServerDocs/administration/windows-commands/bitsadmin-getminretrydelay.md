---
title: bitsadmin getminretrydelay
description: Раздел Windows команды для **bitsadmin getminretrydelay** -извлекает продолжительность времени в секундах время ожидания после возникновения временных ошибок перед попыткой передачи файла.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2a6df9faab8340994ad9219a863ad8e50186ccd1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59832205"
---
# <a name="bitsadmin-getminretrydelay"></a>bitsadmin getminretrydelay



Возвращает продолжительность времени в секундах время ожидания после возникновения временных ошибок перед попыткой передачи файла.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetMinRetryDelay <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается задержки повтора минимальное задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetMinRetryDelay myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)