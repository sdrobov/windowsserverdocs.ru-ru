---
title: Набор подкоманд-Имажеграуп
description: Раздел команд Windows для подкоманды set-Имажеграуп, которая изменяет атрибуты группы образов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4d86946a-e261-4d41-8b0c-1ab0ba2e3430
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 966e3c10d9bcc13568f5fec4e1efd1ad46a121b0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833917"
---
# <a name="subcommand-set-imagegroup"></a>Подкоманда: Set-Имажеграуп

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет атрибуты группы образов.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Set-ImageGroumediaGroup:<Image group name> [/Server:<Server name>] [/Name:<New image group name>] [/Security:<SDDL>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
Медиаграуп:<Image group name>|Указывает имя группы образов.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если не указано, будет использоваться локальный сервер.|
|[/Name:<New image group name>]|Указывает новое имя группы образов.|
|[/Секурити:<SDDL>]|Указывает новый дескриптор безопасности группы образов в формате языка определения дескрипторов безопасности (SDDL).|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы задать имя для группы образов, введите:
```
wdsutil /Set-ImageGroumediaGroup:ImageGroup1 /Name:New Image Group Name
```
Чтобы указать различные параметры для группы образов, введите:
```
wdsutil /verbose /Set-ImageGroumediaGroup:ImageGroup1 /Server:MyWDSServer /Name:New Image Group Name 
/Security:O:BAG:S-1-5-21-2176941838-3499754553-4071289181-513 D:AI(A;ID;FA;;;SY)(A;OICIIOID;GA;;;SY)(A;ID;FA;;;BA)(A;OICIIOID;GA;;;BA) (A;ID;0x1200a9;;;AU)(A;OICIIOID;GXGR;;;AU)
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[помощью команды Add-Имажеграуп](using-the-add-imagegroup-command.md) ,
[помощью команды Get-аллимажеграупс](using-the-get-allimagegroups-command.md) ,
[с помощью команды Get-имажеграуп,](using-the-get-imagegroup-command.md)
[с помощью команды Remove-имажеграуп](using-the-remove-imagegroup-command.md) .
