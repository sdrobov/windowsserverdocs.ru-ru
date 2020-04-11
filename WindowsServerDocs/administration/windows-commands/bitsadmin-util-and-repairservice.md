---
title: битсадмин util и репаирсервице
description: Команды Windows для **битсадмин util и репаирсервице**, которая устраняет известные проблемы в различных версиях службы BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ac7baeb-4340-4186-bfcb-66478195378d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 164a402e7cbfc0a9223a97f4246eac84f0797aed
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122517"
---
# <a name="bitsadmin-util-and-repairservice"></a>битсадмин util и репаирсервице

Если не удается запустить службу BITS, этот параметр пытается устранить ошибки, связанные с неправильной конфигурацией службы и зависимостями в службах Windows (например, LANManworkstation) и в сетевом каталоге. Этот параметр также создает выходные данные, указывающие, разрешены ли проблемы.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 1,5 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /util /repairservice [/force]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| /Force | Необязательно. Удаляет и создает службу снова.|

> [!NOTE]
> Если служба BITS вновь создает службу, строка описания службы может быть задана как английская даже в локализованной системе.

## <a name="examples"></a>Примеры

В следующем примере восстанавливается конфигурация службы BITS.

```
C:\>bitsadmin /util /repairservice
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)