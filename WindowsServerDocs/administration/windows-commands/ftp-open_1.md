---
title: Открытие FTP
description: Справочный раздел по команде FTP Open, который подключается к указанному FTP-серверу.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4b61926a-dc60-4b4c-96d3-64e5c91c18ba
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 63e428164ece405a6a83041edd46ffe332b13c3a
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820404"
---
# <a name="ftp-open"></a>Открытие FTP

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Подключается к указанному FTP-серверу.

## <a name="syntax"></a>Синтаксис

```
open <computer> [<port>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<computer>` | Указывает удаленный компьютер, к которому вы пытаетесь подключиться. Можно использовать IP-адрес или имя компьютера (в этом случае должен быть доступен DNS-сервер или файл Hosts). |
| `[<port>]` | Указывает номер порта TCP, используемый для подключения к FTP-серверу. По умолчанию используется TCP-порт 21. |

### <a name="examples"></a>Примеры

Чтобы подключиться к FTP-серверу по адресу *FTP.Microsoft.com*, введите:

```
open ftp.microsoft.com
```

Чтобы подключиться к FTP-серверу по адресу *FTP.Microsoft.com* , который прослушивает TCP-порт *755*, введите:

```
open ftp.microsoft.com 755
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Дополнительные рекомендации по FTP](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
