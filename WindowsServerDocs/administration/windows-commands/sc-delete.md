---
title: SC delete
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fe94fb3-e4d1-47b5-b999-39995ecbb644
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 68af5f118b2cc9d7941abddccd2a1bc7fde4c6d0
ms.sourcegitcommit: 8ba2c4de3bafa487a46c13c40e4a488bf95b6c33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2019
ms.locfileid: "66222937"
---
# <a name="sc-delete"></a>SC delete



Удаляет раздел службы из реестра. Если служба выполняется или другой процесс имеет открытый дескриптор к службе, служба помечена для удаления.

В разделе [Примеры](#examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
sc [<ServerName>] delete [<ServiceName>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя_сервера >|Указывает имя удаленного сервера, на котором расположена служба. Имя следует использовать формат соглашения об универсальных именах (UNC) (например, \\ \\myserver). Этот параметр не указан его для локального запуска SC.exe.|
|\<ServiceName >|Указывает имя службы, возвращенное **getkeyname** операции.|
|?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Используйте **Установка и удаление программ** на **панели управления** удаления DHCP, DNS или любые другие службы, встроенных в операционную систему. Обратите внимание, что **Установка и удаление программ** не удаляется только подраздел реестра для службы, но будет также удалить службу и удалить все ярлыки к нему.

## <a name="examples"></a>Примеры

Для удаления раздела реестра службы **NewServ** из реестра на локальном компьютере, введите:
```
sc delete newserv
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)