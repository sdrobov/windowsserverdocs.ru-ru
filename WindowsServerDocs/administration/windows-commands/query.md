---
title: запрос
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 675c5128-f3cf-4e8f-8a3f-b29ab2a8b6de
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ebe10bb78a6a901871a75e8533b3389c38060666
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863155"
---
# <a name="query"></a>запрос

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о процессах, сеансы и серверы узла сеансов удаленных рабочих столов (узел сеансов удаленных рабочих Столов).

> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы найти новые возможности в последней версии, см. в разделе [какие возможности служб удаленных рабочих столов в Windows Server 2012](https://technet.microsoft.com/library/hh831527) в технической библиотеке Windows Server.

## <a name="syntax"></a>Синтаксис
```
query process
query session
query termserver
query user
```

## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[процесс обработки запроса](query-process.md)|Отображает сведения о процессах, запущенных на сервере узла сеансов удаленных рабочих столов.|
|[запрос сеанса](query-session.md)|Отображает сведения о сеансах на сервере узла сеансов удаленных рабочих столов.|
|[termserver запроса](query-termserver.md)|Отображение списка всех серверов узла сеансов удаленных рабочих столов в сети.|
|[запрос пользователя](query-user.md)|Отображает сведения о пользовательских сеансах на сервере узла сеансов удаленных рабочих столов.|

#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксис командной строки Key](command-line-syntax-key.md)
[служб удаленных рабочих столов &#40;служб терминалов&#41; описанием команды](remote-desktop-services-terminal-services-command-reference.md)
