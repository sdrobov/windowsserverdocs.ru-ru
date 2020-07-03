---
title: bitsadmin takeownership
description: Справочная статья по команде битсадмин такеовнершип, которая позволяет пользователю с правами администратора становиться владельцем указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ea0ce7cb-440a-498f-a3ef-8368fa43e399
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bc406d1d5f7c9553082f85f3315ab7622f6bc7db
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927463"
---
# <a name="bitsadmin-takeownership"></a>bitsadmin takeownership

Позволяет пользователю с правами администратора становиться владельцем указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /takeownership <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ---------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы стать владельцем задания с именем *мидовнлоаджоб*, сделайте следующее:

```
bitsadmin /takeownership myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
