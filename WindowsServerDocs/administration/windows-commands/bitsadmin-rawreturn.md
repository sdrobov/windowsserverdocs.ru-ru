---
title: bitsadmin rawreturn
description: Раздел Windows команды для **bitsadmin rawreturn** -возвращает данные для синтаксического анализа.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bbe97130-26f6-4cdd-84f1-baf530ce38b7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4e12c8e621021d35ac618b4592515fe38c36be0e
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434890"
---
# <a name="bitsadmin-rawreturn"></a>bitsadmin rawreturn

Возвращает данные для синтаксического анализа.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /RawReturn
```

## <a name="remarks"></a>Примечания

Символы новой строки полосковых линий и форматирование выходных данных.

Как правило, эта команда используется в сочетании с **создать** и **получить\\** * коммутаторов для получения только значения. Необходимо указать этот параметр перед другими параметрами.

## <a name="BKMK_examples"></a>Примеры

Следующий пример извлекает необработанные данные для состояния задания с именем *myDownloadJob*.
```
C:\>bitsadmin /RawReturn /GetState myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)