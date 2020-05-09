---
title: дфсдиаг тестситес
description: Справочный раздел по дфсдиаг тестситес, который проверяет конфигурацию сайтов доменных служб Active Directory (AD DS) путем проверки того, что серверы, действующие в качестве целевых объектов сервера пространства имен или папки (ссылки), имеют одинаковые связи сайтов на всех контроллерах домена.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39a0d415-7eb7-4a26-861b-7ff00c45dcda
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 54eb7c7ec44d7cd4872960ca29cd3146b710f472
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992854"
---
# <a name="dfsdiag-testsites"></a>дфсдиаг тестситес

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию сайтов доменных служб Active Directory (AD DS), убедившись, что серверы, действующие как серверы пространства имен или целевые объекты папки (ссылки), имеют одинаковые связи сайтов на всех контроллерах домена.

## <a name="syntax"></a>Синтаксис

```
dfsdiag /testsites </machine:<server name>| /DFSpath:<namespace root or DFS folder> [/recurse]> [/full]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `/machine:<server name>` | Имя сервера, на котором необходимо проверить связь сайта. |
| `/DFSpath:<namespace root or DFS folder>` | Корневая папка пространства имен или распределенная файловая система (DFS) (ссылка) с целевыми объектами, для которых необходимо проверить связь сайта. |
| /Recurse | Перечисляет и проверяет связи сайтов для всех целевых объектов папки в указанном корне пространства имен. |
| /Full | Проверяет, что AD DS и реестр сервера содержат одинаковые сведения о взаимосвязи сайтов. |

## <a name="examples"></a>Примеры

Чтобы проверить связи сайтов в *мачине\мисервер*, введите:

```
dfsdiag /testsites /machine:MyServer
```

Чтобы проверить папку распределенная файловая система (DFS), чтобы проверить связь сайта, а также убедиться, что AD DS и реестр сервера содержат одинаковые сведения о связи сайта, введите:

```
dfsdiag /TestSites /DFSpath:\\contoso.com\namespace1\folder1 /full
```

Чтобы проверить корень пространства имен для проверки связи сайта, а также перечисления и проверки связей сайтов для всех целевых объектов папки в указанном корне пространства имен, а также проверки того, что AD DS и реестр сервера содержат одинаковые сведения о связи сайта, введите:

```
dfsdiag /testsites /DFSpath:\\contoso.com\namespace2 /recurse /full
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда дфсдиаг](dfsdiag.md)
