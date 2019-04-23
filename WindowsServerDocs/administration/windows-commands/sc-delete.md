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
ms.openlocfilehash: b60127cf957a30d147c9992c74c01e37e5b8bf89
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59871925"
---
# <a name="sc-delete"></a>SC delete



Удаляет раздел службы из реестра. Если служба выполняется или другой процесс имеет открытый дескриптор к службе, служба помечена для удаления.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

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

## <a name="BKMK_examples"></a>Примеры

Для удаления раздела реестра службы **NewServ** из реестра на локальном компьютере, введите:
```
sc delete newserv
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)