---
title: С помощью команды get-MulticastTransmission
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b733737b-1e81-43d4-a058-d6985a613bef
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fdbb9283285bcf56cd83c18ea076e3d36a51b966
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59823235"
---
# <a name="using-the-get-multicasttransmission-command"></a>С помощью команды get-MulticastTransmission

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о многоадресной передачи для указанного изображения.
## <a name="syntax"></a>Синтаксис
**Windows Server 2008**
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image group name>] 
[/Filename:<File name>] [/Show:Clients]
```
**Windows Server 2008 R2** для передачи образа загрузки:
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name>
    [/Server:<Server name>]
    [/details:Clients]
  mediatype:Boot
    /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```
для передачи образа установки:
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name>
         [/Server:<Server name>]
         [/details:Clients]
       mediatype:Install
    mediaGroup:<Image Group>]
     [/Filename:<File name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
мультимедиа:<Image name>|Отображает многоадресной передачи, связанный с этим изображением.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, используется локальный сервер.|
MediaType:install|Задает тип изображения. Обратите внимание, что этот параметр должен быть установлен в **установить**.|
|\mediaGroup:<Image group name>]|Указывает группу образов, содержащий изображение. Если указано имя группы не образа и только один образ группа существует на сервере, будет использоваться этой группы образов. Если на сервере существует более одной группы образов, необходимо использовать этот параметр, чтобы указать группу образов.|
|/ Архитектура: {x86 &#124; ia64 &#124; x64}|Задает архитектуру загрузочного образа, который связан с передачей. Так как это может быть то же имя образа для загрузочных образов в различных архитектур, следует указать архитектуры, чтобы убедиться, что используется правильное изображение.|
|[/ Filename:<File name>]|Указывает файл, содержащий изображение. Если изображение не может быть однозначно идентифицируется по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|[/ Show: клиенты]<br /><br />или диспетчер конфигурации служб<br /><br />[/ сведения: клиенты]|Отображает сведения о клиентских компьютерах, подключенных к многоадресной передачи.|
## <a name="BKMK_examples"></a>Примеры
**Windows Server 2008** для просмотра сведений о передачи для образ с именем Vista с Office, введите одно из следующих:
```
wdsutil /Get-MulticastTransmissiomedia:"Vista with Officemediatype:Install
wdsutil /Get-MulticastTransmission /Server:MyWDSServemedia:"Vista with Officemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim /Show:Clients
```
**Windows Server 2008 R2** для просмотра сведений о передачи для образ с именем Vista с Office, введите одно из следующих:
```
wdsutil /Get-MulticastTransmissiomedia:"Vista with Office"
 /Imagetype:Install
```
```
wdsutil /Get-MulticastTransmission /Server:MyWDSServemedia:"Vista with Officemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim /details:Clients
```
```
wdsutil /Get-MulticastTransmission /Server:MyWDSServemedia:"X64 Boot Imagemediatype:Boot /Architecture:x64 /Filename:boot.wim /details:Clients
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды get-AllMulticastTransmissions](using-the-get-allmulticasttransmissions-command.md)
[с помощью команды новый MulticastTransmission](using-the-new-multicasttransmission-command.md) 
 [С помощью команды remove-MulticastTransmission](using-the-remove-multicasttransmission-command.md)
[подкоманда: start-MulticastTransmission](subcommand-start-multicasttransmission.md)
