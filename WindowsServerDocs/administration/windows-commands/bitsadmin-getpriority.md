---
title: битсадмин
description: Раздел команд Windows для **битсадмин предшествовал** . получение приоритета указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 0b8914f27c690aa9bb9cbf30430b3edf55f2eb92
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381430"
---
# <a name="bitsadmin-getpriority"></a>битсадмин

Возвращает приоритет указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetPriority <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Приоритет имеет значение " **основной**", " **высокий**", " **нормальный**", " **низкий**" или " **неизвестный**".

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается приоритет задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetPriority myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
