---
title: query
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 675c5128-f3cf-4e8f-8a3f-b29ab2a8b6de
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1dcea0fa4ea91de56e81c51bf9fe87ec7e3a49fa
ms.sourcegitcommit: 4894649cc47dfa535306cc334871f81155198f76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2020
ms.locfileid: "84254717"
---
# <a name="query"></a>query

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о процессах, сеансах и серверах узла сеансов удаленный рабочий стол.

> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows Server](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn283323(v=ws.11)) в документация Майкрософт библиотеке Windows Server.

## <a name="syntax"></a>Синтаксис

```
query process
query session
query termserver
query user
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|[обработка запросов](query-process.md)|Отображает сведения о процессах, запущенных на сервере узла сеансов удаленных рабочих столов.|
|[сеанс запроса](query-session.md)|Отображает сведения о сеансах на сервере узла сеансов удаленных рабочих столов.|
|[термсервер запросов](query-termserver.md)|Отображает список всех серверов узлов сеансов удаленных рабочих столов в сети.|
|[запрос пользователя](query-user.md)|Отображает сведения о пользовательских сеансах на сервере узла сеансов удаленных рабочих столов.|

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
- [Справочник по командам служб удаленных рабочих столов (служб терминалов)](remote-desktop-services-terminal-services-command-reference.md)
