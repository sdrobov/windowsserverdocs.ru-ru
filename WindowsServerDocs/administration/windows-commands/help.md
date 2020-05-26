---
title: help
description: Справочный раздел для команды Help, в которой отображается список доступных команд или подробные справочные сведения об указанной команде.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c65b5ac3-711a-4368-95b8-ba82e2d00713
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9b73ef32b49b834a91f24e943749eb21398c8588
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83818664"
---
# <a name="help"></a>help

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает список доступных команд или подробные справочные сведения об указанной команде. Если используется без параметров, **Справочные** списки и краткое описание каждой системной команды.

## <a name="syntax"></a>Синтаксис

```
help [<command>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<command>` | Указывает команду, для которой отображаются подробные справочные сведения. |

### <a name="examples"></a>Примеры

Чтобы просмотреть сведения о команде **Robocopy** , введите:

```
help robocopy
```

Чтобы отобразить список всех команд, доступных в DiskPart, введите:

```
help
```

Чтобы просмотреть подробные справочные сведения о том, как использовать команду **создать секцию** в DiskPart, введите:

```
help create partition primary
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
