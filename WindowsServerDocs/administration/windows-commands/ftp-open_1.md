---
title: ftp open
description: Справочная статья по команде FTP Open, которая подключается к указанному FTP-серверу.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4b61926a-dc60-4b4c-96d3-64e5c91c18ba
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 888b8f917d82d72f47a737c2f0edc42451de7164
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925791"
---
# <a name="ftp-open"></a>ftp open

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
