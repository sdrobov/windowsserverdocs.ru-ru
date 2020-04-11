---
title: битсадмин util и жетиепрокси
description: Раздел команд Windows для **битсадмин util и жетиепрокси**, который получает сведения об использовании прокси-сервера для данной учетной записи службы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6d50c7e3-f4eb-4ca5-9f0c-4ed396087db6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 22b24c4f9c0941c88c70b488a82de47c7901bd8b
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122468"
---
# <a name="bitsadmin-util-and-getieproxy"></a>битсадмин util и жетиепрокси

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Возвращает сведения об использовании прокси-сервера для данной учетной записи службы. Эта команда показывает значение для каждого использования прокси-сервера, а не только использование прокси-сервера, указанного для учетной записи службы. Дополнительные сведения о настройке использования прокси-сервера для конкретных учетных записей служб см. в описании команды [битсадмин util и сетиепрокси](bitsadmin-util-and-setieproxy.md) .

## <a name="syntax"></a>Синтаксис

```
bitsadmin /util /getieproxy <account> [/conn <connectionname>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ---------- |
| учетная запись | Указывает учетную запись службы, параметры прокси которой необходимо получить. Возможные значения:<ul><li>ЛОКАЛЬ</li><li>   NETWORKSERVICE</li><li>LocalService.</li></ul> |
| connectionName | Необязательно. Используется с параметром **/conn** для указания используемого подключения модема. Если параметр **/conn** не указан, служба BITS использует подключение по локальной сети. |

## <a name="examples"></a>Примеры

В следующем примере показано использование прокси-сервера для учетной записи сетевой службы.

```
C:\>bitsadmin /util /getieproxy NETWORKSERVICE
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
