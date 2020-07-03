---
title: Remove-Имажеграуп
description: Справочная статья по Remove-Имажеграуп, которая удаляет группу образов с сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5b2c9813-5df2-4272-8449-26f3bb16f82b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3d11a24152250786e600332c5eea0a6ffebc4848
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933330"
---
# <a name="using-the-remove-imagegroup-command"></a>Использование команды Remove-Имажеграуп

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет группу образов с сервера.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /remove-ImageGroumediaGroup:<Image group name> [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
Медиаграуп:<Image group name>|Указывает имя удаляемой группы образов|
|[/Server: <Server name> ]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a>Примеры
Чтобы удалить группу образов, введите одно из следующих действий.
```
wdsutil /remove-ImageGroumediaGroup:ImageGroup1
wdsutil /verbose /remove-ImageGroumediaGroup:My Image Group /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные ссылки
- Ключ синтаксиса [командной строки](command-line-syntax-key.md) 
 [Использование команды](using-the-add-imagegroup-command.md) 
 Add-имажеграуп [Использование команды](using-the-get-allimagegroups-command.md) 
 Get-аллимажеграупс [Использование команды](using-the-get-imagegroup-command.md) 
 Get-имажеграуп [Подкоманда: Set-имажеграуп](subcommand-set-imagegroup.md)
