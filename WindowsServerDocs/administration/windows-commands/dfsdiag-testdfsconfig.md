---
title: дфсдиаг тестдфсконфиг
description: Справочный раздел по дфсдиаг тестдфсконфиг, который проверяет конфигурацию пространства имен распределенная файловая система (DFS).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 106aeeb9-ea79-4e6e-829c-eca06309bab2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2d9490f35c2d509c83d9008aa87627bd3c55a875
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992995"
---
# <a name="dfsdiag-testdfsconfig"></a>дфсдиаг тестдфсконфиг

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию пространства имен распределенная файловая система (DFS), выполняя следующие действия.

- Проверяет, что служба пространства имен DFS запущена и для нее задан тип запуска **автоматически** на всех серверах пространства имен.

- Проверяет, является ли конфигурация реестра DFS согласованной между серверами пространства имен.

- Проверяет следующие зависимости на серверах кластеризованного пространства имен:

  - Зависимость корневого ресурса пространства имен от ресурса сетевого имени.

  - Зависимость ресурса сетевого имени от ресурса IP-адреса.

  - Зависимость корневого ресурса пространства имен от ресурса физического диска.

## <a name="syntax"></a>Синтаксис

```
dfsdiag /testdfsconfig /DFSroot:<namespace>
```

#### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| /Дфсрут:`<namespace>` | Пространство имен (корень DFS) для диагностики. |

## <a name="examples"></a>Примеры

Чтобы проверить конфигурацию пространств имен распределенная файловая система (DFS) в *contoso. ком\минамеспаце*, введите:

```
dfsdiag /testdfsconfig /DFSroot:\contoso.com\MyNamespace
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда дфсдиаг](dfsdiag.md)
