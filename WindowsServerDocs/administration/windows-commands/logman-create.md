---
title: logman create
description: Справочный раздел по команде Logman Create, который создает счетчик, трассировку, сборщик данных конфигурации или API.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 972f0126-7bc4-4b14-9265-062864f3ffd4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c4a68be098f868cdd9cd48c1e7c68fc183fa1fab
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222955"
---
# <a name="logman-create"></a>logman create

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает счетчик, трассировку, сборщик данных конфигурации или API.

## <a name="syntax"></a>Синтаксис

```
logman create <counter | trace | alert | cfg | api> <[-n] <name>> [options]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| [переlogman создать счетчик](logman-create-counter.md) | Создает сборщик данных счетчика. |
| [создать трассировку Logman](logman-create-trace.md) | Создает сборщик данных трассировки. |
| [создать оповещение Logman](logman-create-alert.md) | Создает сборщик данных предупреждений. |
| [Logman Create cfg](logman-create-cfg.md) | Создает сборщик данных конфигурации. |
| [Создание API Logman](logman-create-api.md) | Создает сборщик данных трассировки API. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [команда logman](logman.md)