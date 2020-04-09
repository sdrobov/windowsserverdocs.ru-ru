---
title: битсадмин util и версия
description: Команды Windows для битсадмин util и Version, в которых отображается версия службы BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 98f17328-dfbd-4cbb-93c1-b8d424bc3f0a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 087cc1033166ab93e7496caaa7335433cafd6249
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848837"
---
# <a name="bitsadmin-util-and-version"></a>битсадмин util и версия

Отображает версию службы BITS (например, 2,0).

**Битсадмин 1,5 и более ранних версий**: не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Util /Version [/Verbose]
```

## <a name="remarks"></a>Примечания

Параметр **verbose** выполняет следующие действия:
-   Отображает версию файла для каждой библиотеки DLL, связанной с BITS
-   Проверяет, можно ли запустить службу BITS
-   Отображение значений групповая политика BITS (только для Windows Vista)

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере показана версия службы BITS.
```
C:\>bitsadmin /Util /Version
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)