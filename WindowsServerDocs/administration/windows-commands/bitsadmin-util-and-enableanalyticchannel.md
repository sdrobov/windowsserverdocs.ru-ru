---
title: битсадмин util и енаблеаналитикчаннел
description: Команды Windows для **битсадмин util и енаблеаналитикчаннел**, которые включают или отключают канал аналитики клиента службы BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0d7645aa-b91b-4ed7-b630-a1e1be6f6ae9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f8ff1f835415979036fdc0f8aa637fe693e57d46
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122683"
---
# <a name="bitsadmin-util-and-enableanalyticchannel"></a>битсадмин util и енаблеаналитикчаннел

Включает или отключает аналитический канал клиента BITS.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /util /enableanalyticchannel TRUE|FALSE
```

| Параметр | Описание |
| --------- | ---------- |
| TRUE или FALSE | **Значение true** включает проверку содержимого для указанного файла, а **значение false** отключает его. |

## <a name="examples"></a>Примеры

В следующем примере включается канал аналитики клиента BITS.

```
C:\>bitsadmin /util / enableanalyticchannel TRUE
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)