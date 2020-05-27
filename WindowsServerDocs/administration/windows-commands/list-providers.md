---
title: список поставщиков
description: Справочный раздел для команды list providers, в которой перечислены поставщики теневого копирования, которые в настоящее время зарегистрированы в системе.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 844b4036-c0b9-449d-8347-7d58ef9bf16d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 98615dfa92c24b91babb55ae3545065834887e5d
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817244"
---
# <a name="list-providers"></a>список поставщиков

Перечисляет поставщики теневого копирования, которые в настоящее время зарегистрированы в системе.

## <a name="syntax"></a>Синтаксис

```
list providers
```

### <a name="examples"></a>Примеры

Чтобы получить список зарегистрированных в данный момент поставщиков теневых копий, введите:

```
list providers
```

Выходные данные, аналогичные показанным ниже.

```
* ProviderID: {b5946137-7b9f-4925-af80-51abd60b20d5}
        Type: [1] VSS_PROV_SYSTEM
        Name: Microsoft Software Shadow Copy provider 1.0
        Version: 1.0.0.7
        CLSID: {65ee1dba-8ff4-4a58-ac1c-3470ee2f376a}
1 provider registered.
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)