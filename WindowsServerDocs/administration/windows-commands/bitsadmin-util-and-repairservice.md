---
title: bitsadmin util и repairservice
description: Справочный раздел по команде битсадмин util and репаирсервице, который устраняет известные проблемы в различных версиях службы BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ac7baeb-4340-4186-bfcb-66478195378d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0104a3f2ace972821151bf5083f9b0795e427ff1
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707656"
---
# <a name="bitsadmin-util-and-repairservice"></a>bitsadmin util и repairservice

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
| /Force | Необязательный элемент. Удаляет и создает службу снова.|

> [!NOTE]
> Если служба BITS вновь создает службу, строка описания службы может быть задана как английская даже в локализованной системе.

## <a name="examples"></a>Примеры

Чтобы восстановить конфигурацию службы BITS, выполните следующие действия.

```
bitsadmin /util /repairservice
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [битсадмин util, команда](bitsadmin-util.md)

- [Команда битсадмин](bitsadmin.md)
