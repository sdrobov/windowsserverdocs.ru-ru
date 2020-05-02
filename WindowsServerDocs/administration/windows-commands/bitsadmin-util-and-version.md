---
title: bitsadmin util и version
description: Справочный раздел по команде битсадмин util and Version, которая отображает версию службы BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 98f17328-dfbd-4cbb-93c1-b8d424bc3f0a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 20c3db6e6fcd5ef3d00287f36c9f9624ab5224dd
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707594"
---
# <a name="bitsadmin-util-and-version"></a>bitsadmin util и version

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

Для вывода версии службы BITS.

```
bitsadmin /util /version
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [битсадмин util, команда](bitsadmin-util.md)

- [Команда битсадмин](bitsadmin.md)
