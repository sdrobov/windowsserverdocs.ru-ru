---
title: nslookup lserver
description: Справочный раздел команды nslookup лсервер, которая изменяет первоначальный сервер на указанный домен службы доменных имен (DNS).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aee5ea0b-bb17-4c14-bde7-2f7a91f2f22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 868142f251d62ebc3efd7913aded8e22aa077bd3
ms.sourcegitcommit: 99d548141428c964facf666c10b6709d80fbb215
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2020
ms.locfileid: "84721602"
---
# <a name="nslookup-lserver"></a>nslookup lserver

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет первоначальный сервер на указанный домен службы доменных имен (DNS).

Эта команда использует исходный сервер для поиска сведений об указанном домене DSN. Если необходимо выполнить поиск данных с использованием текущего сервера по умолчанию, используйте команду [nslookup Server](nslookup-server.md) .

## <a name="syntax"></a>Синтаксис

```
lserver <DNSdomain>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<DNSdomain>` | Указывает домен DNS для первоначального сервера. |
| /? | Отображение справки в командной строке. |
| /help | Отображение справки в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [nslookup server](nslookup-server.md)
