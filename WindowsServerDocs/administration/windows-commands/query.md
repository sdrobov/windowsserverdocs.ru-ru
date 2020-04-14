---
title: query
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 675c5128-f3cf-4e8f-8a3f-b29ab2a8b6de
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8d89ae8c7c526bce396b2583abc1728456f7bcc3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836827"
---
# <a name="query"></a>query

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о процессах, сеансах и серверах узла сеансов удаленный рабочий стол.

> [!NOTE]
> В Windows Server 2008 R2 службы терминалов называются службами удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](https://technet.microsoft.com/library/hh831527) в библиотеке TechNet по Windows Server.

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
|[процесс запроса](query-process.md)|Отображает сведения о процессах, запущенных на сервере узла сеансов удаленных рабочих столов.|
|[сеанс запроса](query-session.md)|Отображает сведения о сеансах на сервере узла сеансов удаленных рабочих столов.|
|[термсервер запросов](query-termserver.md)|Отображает список всех серверов узлов сеансов удаленных рабочих столов в сети.|
|[запрос пользователя](query-user.md)|Отображает сведения о пользовательских сеансах на сервере узла сеансов удаленных рабочих столов.|

## <a name="additional-references"></a>Дополнительные материалы
- [Командная строка синтаксиса командной строки](command-line-syntax-key.md)
[службы удаленных рабочих столов (службы терминалов) Справочник по командам](remote-desktop-services-terminal-services-command-reference.md)
