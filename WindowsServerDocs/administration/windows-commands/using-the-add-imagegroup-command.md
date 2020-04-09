---
title: Add-Имажеграуп
description: Раздел команд Windows для Add-Имажеграуп, который добавляет группу образов на сервер служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6ca88671-51de-4924-b969-88f3dfd84270
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f12ed27ca1a809ec34dbefbc4ff7288ff194a83e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831897"
---
# <a name="add-imagegroup"></a>Add-Имажеграуп

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет группу образов на сервер служб развертывания Windows.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /add-ImageGroumediaGroup:<Image group name> [/Server:<Server name>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
Медиаграуп:<Image group name>|Указывает имя добавляемой группы образов.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы добавить группу образов, введите одно из следующих действий.
```
wdsutil /add-ImageGroumediaGroup:ImageGroup2
wdsutil /verbose /add-ImageGroumediaGroup:My Image Group /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды Get-Аллимажеграупс](using-the-get-allimagegroups-command.md) ,
[помощью команды Get-имажеграуп](using-the-get-imagegroup-command.md) ,
[с помощью команды Remove-имажеграуп,](using-the-remove-imagegroup-command.md)
[подкоманде: Set-имажеграуп](subcommand-set-imagegroup.md)
