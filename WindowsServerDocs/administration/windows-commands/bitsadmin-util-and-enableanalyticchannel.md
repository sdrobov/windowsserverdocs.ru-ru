---
title: bitsadmin util и enableanalyticchannel
description: Справочная статья по команде битсадмин util and енаблеаналитикчаннел, которая включает или отключает канал аналитики клиента службы BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0d7645aa-b91b-4ed7-b630-a1e1be6f6ae9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 515402f42dee54baa662f37718841f70b1cd2882
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927418"
---
# <a name="bitsadmin-util-and-enableanalyticchannel"></a>bitsadmin util и enableanalyticchannel

Включает или отключает аналитический канал клиента BITS.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /util /enableanalyticchannel TRUE|FALSE
```

| Параметр | Описание |
| --------- | ---------- |
| TRUE или FALSE | **Значение true** включает проверку содержимого для указанного файла, а **значение false** отключает его. |

## <a name="examples"></a>Примеры

Для включения или отключения аналитического канала клиента BITS.

```
bitsadmin /util / enableanalyticchannel TRUE
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [битсадмин util, команда](bitsadmin-util.md)

- [Команда битсадмин](bitsadmin.md)
