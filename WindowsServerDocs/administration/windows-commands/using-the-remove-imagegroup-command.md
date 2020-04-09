---
title: Remove-Имажеграуп
description: Раздел команд Windows для Remove-Имажеграуп, который удаляет группу образов с сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5b2c9813-5df2-4272-8449-26f3bb16f82b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d8406959037a958ea6d61b8e8145317635955e6d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830357"
---
# <a name="using-the-remove-imagegroup-command"></a>Использование команды Remove-Имажеграуп

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы удалить группу образов, введите одно из следующих действий.
```
wdsutil /remove-ImageGroumediaGroup:ImageGroup1
wdsutil /verbose /remove-ImageGroumediaGroup:My Image Group /Server:MyWDSServer 
```
## <a name="additional-references"></a>Дополнительные материалы
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
[Использование команды Add-Имажеграуп](using-the-add-imagegroup-command.md)  
[Использование команды Get-Аллимажеграупс](using-the-get-allimagegroups-command.md)  
[Использование команды Get-Имажеграуп](using-the-get-imagegroup-command.md)  
[Подкоманда: Set-Имажеграуп](subcommand-set-imagegroup.md)  
