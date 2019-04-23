---
title: bitsadmin getpriority
description: Раздел Windows команды для **bitsadmin getpriority** -получает приоритет указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 6be2461ed87b75144367b1bd74376381e4674b66
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59841445"
---
# <a name="bitsadmin-getpriority"></a>bitsadmin getpriority

Получает приоритет указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetPriority <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Приоритет имеет значение **переднего ПЛАНА**, **высокой**, **ОБЫЧНЫЙ**, **НИЗКИМ**, или **Неизвестный**.

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается приоритет задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetPriority myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
