---
title: С помощью команды remove-ImageGroup
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b2c9813-5df2-4272-8449-26f3bb16f82b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: df6af7fbd19cc95dfbffa0a5c0e2a4b3e33fb82c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59877895"
---
# <a name="using-the-remove-imagegroup-command"></a>С помощью команды remove-ImageGroup

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет группу образов с сервера.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /remove-ImageGroumediaGroup:<Image group name> [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
mediaGroup:<Image group name>|Указывает имя группы образов для удаления|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеры
Чтобы удалить группу образов, введите одно из следующих:
```
wdsutil /remove-ImageGroumediaGroup:ImageGroup1
wdsutil /verbose /remove-ImageGroumediaGroup:"My Image Group" /Server:MyWDSServer 
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add-ImageGroup](using-the-add-imagegroup-command.md)
[с помощью команды get-AllImageGroups](using-the-get-allimagegroups-command.md) 
 [ С помощью команды get-ImageGroup](using-the-get-imagegroup-command.md)
[подкоманда: set-ImageGroup](subcommand-set-imagegroup.md)
