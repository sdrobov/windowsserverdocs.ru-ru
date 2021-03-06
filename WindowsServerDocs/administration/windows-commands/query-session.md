---
title: query session
description: Справочная статья по команде запроса Session, в которой отображаются сведения о сеансах на удаленный рабочий стол сервере узла сеансов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: abc0ace8-0b74-4b6e-a937-a78bb4b61a1f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 75cb8deb61ebfe3a4b0db665da4353339ee8d314
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86956506"
---
# <a name="query-session"></a>query session

Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о сеансах на сервере узла сеансов удаленный рабочий стол. Список включает сведения не только об активных сеансах, но и о других сеансах, которые выполняет сервер.

> [!NOTE]
> Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows Server](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11)).

## <a name="syntax"></a>Синтаксис

```
query session [<sessionname> | <username> | <sessionID>] [/server:<servername>] [/mode] [/flow] [/connect] [/counter]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
|--|--|
| `<sessionname>` | Указывает имя сеанса, с которым необходимо выполнить запрос. |
| `<username>` | Указывает имя пользователя, сеансы которого необходимо запросить. |
| `<sessionID>` | Указывает идентификатор сеанса, к которому необходимо выполнить запрос. |
| /server:`<servername>` | Определяет сервер узла сеансов удаленных рабочих столов для запроса. Значение по умолчанию — текущий сервер. |
| /Mode | Отображает текущие параметры линии. |
| /флов | Отображает текущие параметры управления потоком. |
| /коннект | Отображает текущие параметры подключения. |
| /Counter | Отображает сведения о текущих счетчиках, включая общее число созданных, отключенных и повторно подключенных сеансов. |
| /? | Отображение справки в командной строке. |

#### <a name="remarks"></a>Комментарии

- Пользователь всегда может запрашивать сеанс, в который в данный момент вошел пользователь. Чтобы запросить другие сеансы, пользователь должен иметь специальное разрешение на доступ.

- Если вы не укажете сеанс, используя параметры <*username*>, <*Sessionname*> или *SessionID* , в этом запросе будут отображаться сведения обо всех активных сеансах в системе.

- Когда **сеанс запроса** возвращает сведения, `(>)` перед текущим сеансом отображается символ "больше чем". Например:

    ```
    C:\>query session
        SESSIONNAME     USERNAME        ID STATE    TYPE    DEVICE
        console         Administrator1  0 active    wdcon
        >rdp-tcp#1      User1           1 active    wdtshare
        rdp-tcp                         2 listen    wdtshare
                                        4 idle
                                        5 idle
    ```

    Где:
  - **SESSIONNAME** указывает имя, назначенное сеансу.
  - **Username** указывает имя пользователя, подключенного к сеансу.
  - **State** предоставляет сведения о текущем состоянии сеанса.
  - **Тип** указывает тип сеанса.
  - **Устройство**, которое отсутствует для сеансов, подключенных к консоли или к сети, — это имя устройства, назначенное сеансу.
  - Все сеансы, в которых исходное состояние настроено как ОТКЛЮЧЕНное, не будут отображаться в списке **сеансов запросов** , пока они не будут включены.

### <a name="examples"></a>Примеры

Чтобы отобразить сведения обо всех активных сеансах на сервере *Server2*, введите:

```
query session /server:Server2
```

Чтобы отобразить сведения о *modeM02*активного сеанса, введите:

```
query session modeM02
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [команда запроса](query.md)

- [Справочник по командам служб удаленных рабочих столов (служб терминалов)](remote-desktop-services-terminal-services-command-reference.md)
