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
ms.openlocfilehash: 45545b4e12d31c293ead5b18b83efd50d7bc37bb
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66439649"
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
&lt;Здесь будут размещаться подробное описание вашего примера.&gt;

```
This /is /the /example /of /calling /command /with /parameters
```

&lt;Здесь будут размещаться подробное описание еще один пример.&gt;

```
This /is /a:different /example
```

## <a name="additional-references"></a>Дополнительные ссылки

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)


