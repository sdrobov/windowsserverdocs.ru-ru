---
title: nslookup lserver
description: Справочная статья по команде nslookup лсервер, которая изменяет первоначальный сервер на указанный домен службы доменных имен (DNS).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aee5ea0b-bb17-4c14-bde7-2f7a91f2f22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f8d40a39abb6f96e900aee6dc029963ed7c0486
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931270"
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
