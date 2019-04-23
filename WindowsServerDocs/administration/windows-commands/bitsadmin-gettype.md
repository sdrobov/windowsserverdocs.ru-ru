---
title: bitsadmin gettype
description: Раздел Windows команды для **bitsadmin gettype** -извлекает тип задания указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bec16f04-3e95-4587-889e-3de6ad03c9c8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ff0118f14acbf4e9f37c02e660bd9c7f6e8d0f70
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879435"
---
# <a name="bitsadmin-gettype"></a>bitsadmin gettype



Возвращает тип задания указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetType <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Тип можно загрузить, отправить, отправки-ОТВЕТА или UNKNOWN.

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается тип задания для задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetType myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)