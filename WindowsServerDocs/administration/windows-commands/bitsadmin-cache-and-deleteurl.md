---
title: кэш битсадмин и Делетеурл
description: Справочный раздел по битсадмин кэшу и команде Делетеурл, который удаляет все записи кэша для данного URL-адреса.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e108b76b-fae9-4c16-bf4c-d74c9f025953
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 075c48e5c8c205cbbf3fe476260ec7909edcc3e6
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718448"
---
# <a name="bitsadmin-cache-and-deleteurl"></a>кэш битсадмин и Делетеурл

Удаляет все записи кэша для заданного URL-адреса.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /deleteURL URL
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| URL-адрес | Универсальный указатель ресурсов, определяющий удаленный файл. |

## <a name="examples"></a>Примеры

Удаление всех записей кэша для `https://www.contoso.com/en/us/default.aspx`:

```
bitsadmin /deleteURL https://www.contoso.com/en/us/default.aspx 
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда кэша битсадмин](bitsadmin-cache.md)
