---
title: Подкоманды ImageGroup набора
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d86946a-e261-4d41-8b0c-1ab0ba2e3430
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d0c7ba47148ba6f8295ab720dd0118759ac9346c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59822985"
---
# <a name="subcommand-set-imagegroup"></a>Подкоманда: set-ImageGroup

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет атрибуты группы образов.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Set-ImageGroumediaGroup:<Image group name> [/Server:<Server name>] [/Name:<New image group name>] [/Security:<SDDL>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
mediaGroup:<Image group name>|Указывает имя группы образов.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если не указан, будет использоваться локальный сервер.|
|[/ Name:<New image group name>]|Указывает новое имя группы образов.|
|[/ Безопасности:<SDDL>]|Указывает новый дескриптор безопасности, группы образов, в формате языка (SDDL язык) для определения дескриптора безопасности.|
## <a name="BKMK_examples"></a>Примеры
Чтобы задать имя для группы образов, введите:
```
wdsutil /Set-ImageGroumediaGroup:ImageGroup1 /Name:"New Image Group Name"
```
Чтобы задать различные параметры для группы образов, введите:
```
wdsutil /verbose /Set-ImageGroumediaGroup:ImageGroup1 /Server:MyWDSServer /Name:"New Image Group Name" 
/Security:"O:BAG:S-1-5-21-2176941838-3499754553-4071289181-513 D:AI(A;ID;FA;;;SY)(A;OICIIOID;GA;;;SY)(A;ID;FA;;;BA)(A;OICIIOID;GA;;;BA) (A;ID;0x1200a9;;;AU)(A;OICIIOID;GXGR;;;AU)"
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add-ImageGroup](using-the-add-imagegroup-command.md)
[с помощью команды get-AllImageGroups](using-the-get-allimagegroups-command.md) 
 [ С помощью команды get-ImageGroup](using-the-get-imagegroup-command.md)
[с помощью команды remove-ImageGroup](using-the-remove-imagegroup-command.md)
