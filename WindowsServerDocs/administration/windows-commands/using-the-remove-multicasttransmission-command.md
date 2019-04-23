---
title: С помощью команды remove-MulticastTransmission
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a7f5c31-bfbf-425d-9129-a6f9173fe83d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dc3ba385644ef9da9b5d592142091ff087cd7545
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59839685"
---
# <a name="using-the-remove-multicasttransmission-command"></a>С помощью команды remove-MulticastTransmission

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отключает многоадресной передачи для изображения. Если не указать **/force**, существующие клиенты будут завершения передачи образа, но новые клиенты не смогут присоединиться.
## <a name="syntax"></a>Синтаксис
**Windows Server 2008**
```
wdsutil /remove-MulticastTransmissiomedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image Group>] [/Filename:<File name>] [/force]
```
**Windows Server 2008 R2** для загрузочных образов:
```
wdsutil [Options] /remove-MulticastTransmissiomedia:<Image name>
\x20    [/Server:<Server name>]
\x20  mediatype:Boot
\x20    /Architecture:{x86 | ia64 | x64}
\x20    [/Filename:<File name>]
```
для образов установки:
```
wdsutil [Options] /remove-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Install
       mediaGroup:<Image Group
        [/Filename:<File name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
мультимедиа:<Image name>|Задает имя образа.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, используется локальный сервер.|
Тип носителя: {установить&#124;загрузки}|Задает тип изображения. Обратите внимание, что этот параметр должен быть установлен в **установить** для Windows Server 2008.|
|/ Архитектура: {x86 &#124; ia64 &#124; x64}|Задает архитектуру загрузочного образа, который связан с Запуск передачи. Так как это может быть то же имя образа для загрузочных образов в различных архитектур, следует указать архитектуры, чтобы убедиться, что используется правильный передачи.|
|\mediaGroup:<Image group name>]|Указывает группу образов, содержащий изображение. Если указано имя группы не образа и только один образ группа существует на сервере, будет использоваться этой группы образов. Если на сервере существует более одной группы образов, необходимо использовать этот параметр, чтобы указать имя группы.|
|[/ Filename:<File name>]|Указывает имя файла. Если исходное изображение не может быть однозначно идентифицируется по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|[/ force]|Удаляет передачи и завершения всех клиентов. Если не указано значение для **/force** параметр, существующие клиенты могут выполнить передачу образа, но новые клиенты не смогут присоединиться.|
## <a name="BKMK_examples"></a>Примеры
Чтобы остановить пространства имен (текущих клиентов будет завершена передача, но новые клиенты не смогут соединиться с), тип:
```
wdsutil /remove-MulticastTransmissiomedia:"Vista with Office"
/Imagetype:Install
```
```
wdsutil /remove-MulticastTransmissiomedia:"x64 Boot Image"
/Imagetype:Boot /Architecture:x64
```
Чтобы выполнить завершение всех клиентов, введите следующую команду:
```
wdsutil /remove-MulticastTransmission /Server:MyWDSServer
/Image:"Vista with Officemediatype:InstalmediaGroup:ImageGroup1
/Filename:install.wim /force
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды get-AllMulticastTransmissions](using-the-get-allmulticasttransmissions-command.md)
[с помощью команды get-MulticastTransmission](using-the-get-multicasttransmission-command.md) 
 [С помощью команды новый MulticastTransmission](using-the-new-multicasttransmission-command.md)
[подкоманда: start-MulticastTransmission](subcommand-start-multicasttransmission.md)
