---
title: list shadows
description: Справочная статья по команде List Shadows, в которой перечислены постоянные и существующие непостоянные теневые копии, которые находятся в системе.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fe568423-00ae-4ede-a1e7-07977cb50ad1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fcf1946f5b2424eb7aa13af51bd6ff13c43349c1
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931797"
---
# <a name="list-shadows"></a>list shadows

Список постоянных и существующих непостоянных теневых копий, имеющихся в системе.

## <a name="syntax"></a>Синтаксис

```
list shadows {all | set <setID> | id <shadowID>}
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ---------- | ---------- |
| все | Список всех теневых копий. |
| параметр`<setID>` | Выводит список теневых копий, принадлежащих указанному ИДЕНТИФИКАТОРу набора теневых копий. |
| удостоверения`<shadowID>` | Отображает все теневые копии с указанным ИДЕНТИФИКАТОРом теневой копии. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)