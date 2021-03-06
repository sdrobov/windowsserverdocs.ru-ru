---
title: reset session
description: Справочная статья для * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4f029ecc-874e-415a-95a8-8b731bae35f9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 14ef7bdcb8490787b3fadff0cb842070f7a71446
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86956238"
---
# <a name="reset-session"></a>reset session

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Позволяет сбросить (удалить) сеанс на сервере узла сеансов удаленный рабочий стол (на узле сеансов удаленных рабочих столов).


> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](/previous-versions/orphan-topics/ws.11/hh831527(v=ws.11)) в библиотеке TechNet по Windows Server.

## <a name="syntax"></a>Синтаксис
```
reset session {<SessionName> | <SessionID>} [/server:<ServerName>] [/v]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|\<SessionName>|Указывает имя сеанса, который требуется сбросить. Чтобы определить имя сеанса, используйте команду **запроса сеанса** .|
|\<SessionID>|Указывает идентификатор сеанса для сброса.|
|/server:\<ServerName>|Указывает сервер терминалов, содержащий сеанс, который требуется сбросить. В противном случае используется текущий сервер узла сеансов удаленных рабочих столов.|
|/v|Отображает сведения о выполняемых действиях.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Комментарии
-   Вы всегда можете сбросить собственные сеансы, но для сброса сеанса другого пользователя необходимо иметь разрешение «Полный доступ».
-   Имейте в виду, что сброс сеанса пользователя без предупреждения пользователь может привести к утрате данных в сеансе.
-   Сброс сеанса следует выполнять только в том случае, если он неисправен или перестал отвечать на запросы.
-   Параметр **/Server** требуется только при использовании параметра **сбросить сеанс** с удаленного сервера.

## <a name="examples"></a>Примеры
- Чтобы сбросить сеанс с назначенным RDP-TCP # 6, введите:
  ```
  reset session rdp-tcp#6
  ```
- Чтобы сбросить сеанс, использующий сеанс с ИДЕНТИФИКАТОРом 3, введите:
  ```
  reset session 3
  ```

## <a name="additional-references"></a>Дополнительные ссылки
- Ключ синтаксиса [командной строки](command-line-syntax-key.md) 
 [Справочник по командам служб терминалов службы удаленных рабочих столов](remote-desktop-services-terminal-services-command-reference.md)
