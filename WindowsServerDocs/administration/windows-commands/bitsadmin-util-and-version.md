---
title: битсадмин util и версия
description: Команды Windows для **битсадмин util и Version**, в которых отображается версия службы BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 98f17328-dfbd-4cbb-93c1-b8d424bc3f0a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2c2518eb7a8f15d9a592ed9a77dd67a6f8d8afac
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122469"
---
# <a name="bitsadmin-util-and-version"></a>битсадмин util и версия

Отображает версию службы BITS (например, 2,0).

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 1,5 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /util /version [/verbose]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| /verbose | Используйте этот параметр, чтобы отобразить версию файла для каждой библиотеки DLL, связанной с BITS, и проверить, может ли запускаться служба BITS.|

## <a name="examples"></a>Примеры

В следующем примере показана версия службы BITS.

```
C:\>bitsadmin /util /version
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)