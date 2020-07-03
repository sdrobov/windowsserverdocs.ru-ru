---
title: telnet open
description: Справочная статья по Telnet Open, которая подключается к серверу Telnet.
ms.prod: windows-server
ms.technology: manage-windows-commands
s.topic: article
ms.assetid: e30ad68c-2366-4754-ac36-311a2392902a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f3b27088d464e62b24479eaa87f44b91f7d95d12
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935334"
---
# <a name="telnet-open"></a>Telnet: открыть

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Подключается к серверу Telnet.

## <a name="syntax"></a>Синтаксис
```
o[pen] <hostname> [<Port>]
```
#### <a name="parameters"></a>Параметры

| Параметр  |                                        Описание                                         |
|------------|--------------------------------------------------------------------------------------------|
| <hostname> |                         Указывает имя или IP-адрес компьютера.                         |
|  [<Port>]  | Указывает TCP-порт, который прослушивает сервер Telnet. Значение по умолчанию — TCP-порт 23. |

## <a name="examples"></a>Примеры
Подключитесь к серверу Telnet по адресу telnet.microsoft.com.
```
o telnet.microsoft.com
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
