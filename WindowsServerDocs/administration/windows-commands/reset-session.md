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
ms.openlocfilehash: 07ebe7220ec2624dd0dee5e5302be9c98fbd7fa0
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933103"
---
# <a name="reset-session"></a>reset session

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Позволяет сбросить (удалить) сеанс на сервере узла сеансов удаленный рабочий стол (на узле сеансов удаленных рабочих столов).


> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](https://technet.microsoft.com/library/hh831527) в библиотеке TechNet по Windows Server.

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
