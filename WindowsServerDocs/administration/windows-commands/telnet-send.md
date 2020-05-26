---
title: Отправка Telnet
description: Справочный раздел по Telnet Send, который отправляет команды Telnet на сервер Telnet.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c217abc-1182-466e-914c-1ff16755021b vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5dd4bf9828c4b71e7b2291dfd5d453c43679e059
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83821074"
---
# <a name="telnet-send"></a>Telnet: send

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отправляет команды Telnet на сервер Telnet.

## <a name="syntax"></a>Синтаксис
```
sen[d] {ao | ayt | brk | esc | ip | synch | <string>} [?]
```
#### <a name="parameters"></a>Параметры

| Параметр |                     Описание                      |
|-----------|------------------------------------------------------|
|    AO     |       Отправляет выходные данные команды Telnet Abort.        |
|    айт    |       Отправляет команду Telnet.       |
|    брк    |            Отправляет команду Telnet БРК.            |
|    ESC    |      Отправляет текущий escape-символ Telnet.      |
|    см     |     Отправляет процесс прерывания команды Telnet.     |
|   Синхронизация   |           Отправка команды Telnet Synch.           |
| <string>  | Отправляет любую строку, введенную на сервер Telnet. |
|     ?     |     Отображает справку, связанную с этой командой.      |

## <a name="examples"></a>Примеры
Отправьте их на сервер Telnet.
```
sen ayt
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
