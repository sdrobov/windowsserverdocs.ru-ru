---
title: Использование команды Get-Имажеграуп
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: d6531a3b69840a0a4910b2effdd3e349b76edf2c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363120"
---
# <a name="using-the-get-imagegroup-command"></a>Использование команды Get-Имажеграуп

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения о группе образов и содержащихся в ней изображениях.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-ImageGroumediaGroup:<Image group name> [/Server:<Server name>] [/detailed]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
Медиаграуп: <Image group name>|Указывает имя группы образов.|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|[/детаилед]|Возвращает метаданные изображения для каждого изображения. Если этот параметр не используется, поведение по умолчанию — возврат только имени, описания и имени файла изображения.|
## <a name="BKMK_examples"></a>Примеров
Чтобы просмотреть сведения о группе образов, введите:
```
wdsutil /Get-ImageGroumediaGroup:ImageGroup1
```
Чтобы просмотреть сведения, включая метаданные, введите:
```
wdsutil /verbose /Get-ImageGroumediaGroup:ImageGroup1 /Server:MyWDSServer /detailed
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды add-имажеграуп](using-the-add-imagegroup-command.md)
 с[помощью команды Get-Аллимажеграупс](using-the-get-allimagegroups-command.md)
[с помощью команды Remove-Имажеграуп](using-the-remove-imagegroup-command.md)
[: Set-имажеграуп](subcommand-set-imagegroup.md)
