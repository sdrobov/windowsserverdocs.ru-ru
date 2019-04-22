---
title: Dfsutil
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef5093a4-0d24-4b21-9d04-59933ad98e2c
robots: noindex,nofollow
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 245f8fb2e6419d22da3e2e76eebd9f801ab90664
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821485"
---
# <a name="dfsutil"></a>Dfsutil

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Команды dfsutil управляет пространств имен DFS, серверов и клиентов. Dfsutil команды используют исходное терминология распределенной файловой системы, с обновленной терминологии пространств имен DFS, предоставляется как объяснение для большинства команд.

Примеры использования этой команды см. в разделе 

## <a name="syntax"></a>Синтаксис

```
command </parameter> </param2>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|[Dfsutil корневой](dfsutil-root.md)|Отображает, создает, удаляет, импортирует, экспортирует корневые пространства имен.|
|[Dfsutil ссылку](dfsutil-link.md)|Отображает, создает, удаляет или перемещение папки \(ссылки\).|
|[Dfsutil целевой объект](dfsutil-target.md)|Отображает, создать, удалить сервер папки целевой объект или пространства имен.|
|[Dfsutil свойство](dfsutil-property.md)|Отображение или изменение сервера на целевой объект или пространство имен папок.|
|[Dfsutil клиента](dfsutil-client.md)|Отображает или изменяет ключи клиента сведения или реестра.|
|[Dfsutil сервера](dfsutil-server.md)|Отображает или изменяет конфигурацию пространства имен.|
|[Dfsutil Diag](dfsutil-diag.md)|Выполнить диагностику или просмотр dfsdirs\/dfspath.|
|[Dfsutil домена](dfsutil-domain.md)|Отображает все домена\-на основе пространства имен в домене.|
|[Dfsutil кэша](dfsutil-cache.md)|Отображает или очищает кэш клиента.|
|[Dfsutil oldcli](dfsutil-oldcli.md)|Использовать dfsutil \/oldcli команду, чтобы использовать исходный dfsutil синтаксиса.|

## <a name="remarks-optional-section"></a>"Примечания" <optional section>
Если указать объект \(например сервер пространства имен\) в конце команды, большинство команд отобразится информация об объекте без дополнительных параметров или команды. Например при использовании dfsutil команды Root, после добавления корневого пространства имен в команду, чтобы просмотреть сведения о корневой.

## <a name="BKMK_Examples"></a>Примеры
<Here is where you put a detailed description of your example.>

```
This /is /the /example /of /calling /command /with /parameters
```

<Here is where you put a detailed description of another example.>

```
This /is /a:different /example
```

## <a name="additional-references"></a>Дополнительные ссылки

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)


