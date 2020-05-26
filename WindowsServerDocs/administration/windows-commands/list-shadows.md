---
title: перечислить тени
description: Справочный раздел для команды List Shadows, в которой перечислены постоянные и существующие непостоянные теневые копии, которые находятся в системе.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fe568423-00ae-4ede-a1e7-07977cb50ad1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9e0261a25c7a70a0c8690d578cadc9e73ff9a62e
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817174"
---
# <a name="list-shadows"></a>перечислить тени

Список постоянных и существующих непостоянных теневых копий, имеющихся в системе.

## <a name="syntax"></a>Синтаксис

```
list shadows {all | set <setID> | id <shadowID>}
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ---------- | ---------- |
| all | Список всех теневых копий. |
| параметр`<setID>` | Выводит список теневых копий, принадлежащих указанному ИДЕНТИФИКАТОРу набора теневых копий. |
| удостоверения`<shadowID>` | Отображает все теневые копии с указанным ИДЕНТИФИКАТОРом теневой копии. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)