---
title: logman query
description: Справочный раздел по команде Logman Query, который запрашивает свойства группы сборщиков данных или группы сборщика данных.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1116a0f0-5415-4369-a045-12f79f8f66de
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f37b78023fd12c1d58234cdecdb69af8a1c6002d
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222818"
---
# <a name="logman-query"></a>logman query

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запрашивает свойства группы сборщиков данных или сборщика данных.

## <a name="syntax"></a>Синтаксис

```
logman query [providers|Data Collector Set name] [options]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| -s`<computer name>` | Выполните команду на указанном удаленном компьютере. |
| -config`<value>` | Указывает файл параметров, содержащий параметры команды. |
| [-n]`<name>` | Имя целевого объекта. |
| -ETS | Отправляет команды в сеансы трассировки событий напрямую без сохранения или планирования. |
| /? | Отображает контекстную справку. |

### <a name="examples"></a>Примеры

Чтобы вывести список всех наборов сборщиков данных, настроенных в целевой системе, введите:

```
logman query
```

Чтобы получить список сборщиков данных, содержащихся в группе сборщиков данных с именем *perf_log*, введите:

```
logman query perf_log
```

Чтобы получить список всех доступных поставщиков сборщиков данных в целевой системе, введите:

```
logman query providers
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [команда logman](logman.md)
