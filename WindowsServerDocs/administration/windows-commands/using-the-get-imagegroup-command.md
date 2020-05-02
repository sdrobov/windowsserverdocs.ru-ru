---
title: Get-Имажеграуп
description: Справочный раздел по Get-Имажеграуп, который извлекает сведения о группе образов и изображениях в ней.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0fc25aca-a529-44ee-bc8e-96bc8affb458
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 30a87085cb935f95a209ffdd78ecf2b9fb45dc15
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719901"
---
# <a name="get-imagegroup"></a>Get-Имажеграуп

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения о группе образов и содержащихся в ней изображениях.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-ImageGroumediaGroup:<Image group name> [/Server:<Server name>] [/detailed]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
Медиаграуп:<Image group name>|Указывает имя группы образов.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|[/детаилед]|Возвращает метаданные изображения для каждого изображения. Если этот параметр не используется, поведение по умолчанию — возврат только имени, описания и имени файла изображения.|
## <a name="examples"></a>Примеры
Чтобы просмотреть сведения о группе образов, введите:
```
wdsutil /Get-ImageGroumediaGroup:ImageGroup1
```
Чтобы просмотреть сведения, включая метаданные, введите:
```
wdsutil /verbose /Get-ImageGroumediaGroup:ImageGroup1 /Server:MyWDSServer /detailed
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ](command-line-syntax-key.md)
синтаксиса командной строки[с помощью команды Add-имажеграуп](using-the-add-imagegroup-command.md)
с помощью команды[Get-аллимажеграупс](using-the-get-allimagegroups-command.md)
с командой[Remove-имажеграуп](using-the-remove-imagegroup-command.md)
[: Set-имажеграуп](subcommand-set-imagegroup.md)
