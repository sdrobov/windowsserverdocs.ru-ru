---
title: Подкоманды start-MulticastTransmission
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1b2d459-1ece-49d4-997c-9d206c463b61
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d7e3e59a0907caf2769d5df00aeaf00589ab450d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842685"
---
# <a name="subcommand-start-multicasttransmission"></a>Подкоманда: start-MulticastTransmission

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запуск передачи образа рассылкой по расписанию.
## <a name="syntax"></a>Синтаксис
**Windows Server 2008**
```
wdsutil /start-MulticastTransmissiomedia:<Image name> [/Server:<Server namemediatype:InstallmediaGroup:<Image group name>] [/Filename:<File name>]
```
**Windows Server 2008 R2** для загрузочных образов:
```
wdsutil [Options] /start-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Boot
        /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```
для образов установки:
```
wdsutil [Options] /start-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Install
       mediaGroup:<Image Group>]
        [/Filename:<File name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
мультимедиа:<Image name>|Задает имя образа.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
Тип носителя: {установить&#124;загрузки}|Задает тип изображения. Обратите внимание, что этот параметр должен быть установлен в **установить** для Windows Server 2008.|
|/ Архитектура: {x86 &#124; ia64 &#124; x64}|Архитектура загрузочного образа, который связан с Запуск передачи. Так как это может быть то же имя образа для загрузочных образов в различных архитектур, следует указать архитектуры, чтобы убедиться, что используется правильный передачи.|
|\mediaGroup:<Image group name>]|Задает группу изображений изображения. Если указано имя группы не образа и только один образ группа существует на сервере, будет использоваться этой группы образов. Если на сервере существует более одной группы образов, необходимо использовать этот параметр, чтобы указать имя группы.|
|[/ Filename:<File name>]|Указывает имя файла, содержащего изображение. Если изображение не может быть однозначно идентифицируется по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
## <a name="BKMK_examples"></a>Примеры
Чтобы запустить многоадресной передачи, введите одно из следующих:
```
wdsutil /start-MulticastTransmissiomedia:"Vista with Office"
/Imagetype:Install
wdsutil /start-MulticastTransmission /Server:MyWDSServemedia:"Vista with Officemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim
```
Для запуска загрузочного образа многоадресной передачи для Windows Server 2008 R2, тип:
```
wdsutil /start-MulticastTransmission /Server:MyWDSServemedia:"X64 Boot Imagemediatype:Boot /Architecture:x64
/Filename:boot.wim\n\
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды get-AllMulticastTransmissions](using-the-get-allmulticasttransmissions-command.md)
[с помощью команды get-MulticastTransmission](using-the-get-multicasttransmission-command.md) 
 [С помощью команды новый MulticastTransmission](using-the-new-multicasttransmission-command.md)
[с помощью команды remove-MulticastTransmission](using-the-remove-multicasttransmission-command.md)
