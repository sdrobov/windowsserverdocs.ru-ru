---
title: Remove-Имажеграуп
description: Справочный раздел по Remove-Имажеграуп, который удаляет группу образов с сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5b2c9813-5df2-4272-8449-26f3bb16f82b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f814d83a32a8c739e7462bc77251cf3f3f4fe20e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720354"
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
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a>Примеры
Чтобы удалить группу образов, введите одно из следующих действий.
```
wdsutil /remove-ImageGroumediaGroup:ImageGroup1
wdsutil /verbose /remove-ImageGroumediaGroup:My Image Group /Server:MyWDSServer 
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
[Использование команды Add-Имажеграуп](using-the-add-imagegroup-command.md)  
[Использование команды Get-Аллимажеграупс](using-the-get-allimagegroups-command.md)  
[Использование команды Get-Имажеграуп](using-the-get-imagegroup-command.md)  
[Подкоманда: Set-Имажеграуп](subcommand-set-imagegroup.md)  
