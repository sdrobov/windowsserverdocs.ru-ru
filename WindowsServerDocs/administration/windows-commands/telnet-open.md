---
title: открыть Telnet
description: Справочный раздел по Telnet Open, который подключается к серверу Telnet.
ms.prod: windows-server
ms.technology: manage-windows-commands
s.topic: article
ms.assetid: e30ad68c-2366-4754-ac36-311a2392902a vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed2c00b44143942ba1ccb77eec17ca975f23b498
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83821324"
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
