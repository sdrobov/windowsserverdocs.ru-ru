---
title: dfsdiag testreferral
description: Справочная статья по команде дфсдиаг тестреферрал, которая проверяет ссылки на распределенная файловая система (DFS).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 877c60dc-e993-4bd5-87dd-e892e3f98a1a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8ee88e6f9d75dc32bd7fd5dac4c14c72f3bbac02
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928693"
---
# <a name="dfsdiag-testreferral"></a>dfsdiag testreferral

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет ссылки на распределенная файловая система (DFS), выполняя следующие тесты:

- Если вы используете параметр **дфспас*** без аргументов, команда проверяет, что список ссылок включает все доверенные домены.

- При указании домена команда выполняет проверку работоспособности контроллеров домена ( `dfsdiag /testdcs` ) и проверяет связи сайтов и кэш домена локального узла.

- Если указать домен, \Сисвол или \НЕТЛОГОН, команда выполняет те же проверки работоспособности контроллера домена, а также проверку того, что срок **жизни (TTL)** ссылок SYSVOL или Netlogon соответствует значению по умолчанию 900 секунд.

- Если указать корень пространства имен, команда выполняет те же проверки работоспособности контроллера домена, а также выполняет проверку конфигурации DFS ( `dfsdiag /testdfsconfig` ) и проверку целостности пространства имен ( `dfsdiag /testdfsintegrity` ).

- Если указана папка DFS (ссылка), команда выполняет те же проверки работоспособности корневого пространства имен, что и проверка конфигурации сайта для целевых объектов папок (дфсдиаг/тестситес) и проверяет связь сайта с локальным узлом.

## <a name="syntax"></a>Синтаксис

```
dfsdiag /testreferral /DFSpath:<DFS path to get referrals> [/full]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| /Дфспас:`<path to get referrals>` | Может применяться один из перечисленных ниже типов.<ul><li>**Пусто:** Проверяет только доверенные домены.</li><li>`\\Domain:`Проверяет только ссылки на контроллеры домена.</li><li>`\\Domain\SYSvol:`Проверяет только ссылки SYSvol.</li><li>`\\Domain\NETLOGON:`Проверяет только ссылки NETLOGON.</li><li>`\\<domain or server>\<namespace root>:`Проверяет только корневые ссылки пространства имен.</li><li>`\\<domain or server>\<namespace root>\<DFS folder>:`Проверяет только ссылки на папку DFS (Link).</li></ul> |
| /Full | Применимо только к доменным и корневым ссылкам. Проверяет согласованность сведений о связи сайтов между реестром и доменными службами Active Directory (AD DS). |

## <a name="examples"></a>Примеры

Чтобы проверить ссылки распределенная файловая система (DFS) в *contoso. ком\минамеспаце*, введите:

```
dfsdiag /testreferral /DFSpath:\\contoso.com\MyNamespace
```

Чтобы проверить ссылки распределенная файловая система (DFS) во всех доверенных доменах, введите:

```
dfsdiag /testreferral /DFSpath:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда дфсдиаг](dfsdiag.md)
