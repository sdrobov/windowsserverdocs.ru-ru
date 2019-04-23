---
title: С помощью команды get-ImageGroup
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fc25aca-a529-44ee-bc8e-96bc8affb458
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9dcb76155dc1044730673ed46a53cad57441a246
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862605"
---
# <a name="using-the-get-imagegroup-command"></a>С помощью команды get-ImageGroup

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения о группы образов и образы в нем.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-ImageGroumediaGroup:<Image group name> [/Server:<Server name>] [/detailed]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
mediaGroup:<Image group name>|Указывает имя группы образов.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|[/ подробные]|Возвращает метаданные изображения для каждого образа. Если этот параметр не используется, чтобы вернуть только имя образа, описание и имя файла является поведение по умолчанию.|
## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть сведения о группы образов, введите:
```
wdsutil /Get-ImageGroumediaGroup:ImageGroup1
```
Чтобы просмотреть сведения, включая метаданные, введите следующую команду:
```
wdsutil /verbose /Get-ImageGroumediaGroup:ImageGroup1 /Server:MyWDSServer /detailed
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add-ImageGroup](using-the-add-imagegroup-command.md)
[с помощью команды get-AllImageGroups](using-the-get-allimagegroups-command.md) 
 [ С помощью команды remove-ImageGroup](using-the-remove-imagegroup-command.md)
[подкоманда: set-ImageGroup](subcommand-set-imagegroup.md)
