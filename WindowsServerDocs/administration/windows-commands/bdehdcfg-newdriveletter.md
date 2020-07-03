---
title: bdehdcfg newdriveletter
description: Справочная статья по команде BdeHdCfg невдривелеттер, которая назначает новую букву диска части диска, используемой в качестве системного диска.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f1f200a0-6850-4f0d-9047-f9f982a590f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f210056f74e930ad39361c9fc0cbf05d6e1894f4
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923491"
---
# <a name="bdehdcfg-newdriveletter"></a>BdeHdCfg: невдривелеттер

Назначает новую букву диска части диска, используемой в качестве системного диска. Рекомендуется не назначать букву диска системному диску.

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge} -newdriveletter <drive_letter>
```

#### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ---------| ----------- |
| `<drive_letter>` | Определяет букву диска, которая будет назначена указанному целевому диску. |

## <a name="examples"></a>Примеры

Чтобы назначить диску по умолчанию букву диска, `P` сделайте следующее:

```
bdehdcfg -target default -newdriveletter P:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
