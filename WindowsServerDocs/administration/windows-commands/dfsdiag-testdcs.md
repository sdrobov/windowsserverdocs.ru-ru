---
title: дфсдиаг тестдкс
description: Справочный раздел по команде дфсдиаг тестдкс, который проверяет конфигурацию контроллеров домена в указанном домене.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: abb915ab-23eb-45d7-9a2e-b6b9a5756a70
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0bbe47474f99edb1626e61a372b02090d3a45ee3
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "82993004"
---
# <a name="dfsdiag-testdcs"></a>дфсдиаг тестдкс

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию контроллеров домена, выполняя следующие тесты на каждом контроллере домена в указанном домене:

- Проверяет, запущена ли служба пространства имен распределенная файловая система (DFS), и имеет ли ее тип запуска значение " **автоматически**".

- Проверяет поддержку ссылок на веб-сайт для NETLOGON и SYSvol.

- Проверяет согласованность связи сайтов по имени узла и IP-адресу.

## <a name="syntax"></a>Синтаксис

```
dfsdiag /testdcs [/domain:<domain_name>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| /Domain`<domain_name>` | Имя проверяемого домена. Это необязательный параметр. Значение по умолчанию — локальный домен, к которому присоединен локальный узел. |

## <a name="examples"></a>Примеры

Чтобы проверить конфигурацию контроллеров домена в домене *contoso.com* , введите:

```
dfsdiag /testdcs /domain:contoso.com
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда дфсдиаг](dfsdiag.md)
