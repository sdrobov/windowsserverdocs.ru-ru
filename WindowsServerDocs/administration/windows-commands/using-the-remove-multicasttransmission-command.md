---
title: Использование команды Remove-Мултикасттрансмиссион
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 279554124b046f645b3c83e1490657aa8782104a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362817"
---
# <a name="using-the-remove-multicasttransmission-command"></a>Использование команды Remove-Мултикасттрансмиссион

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отключает передачу многоадресной рассылки для образа. Если не указать **/Force**, существующие клиенты будут выполнять перенос образа, но новые клиенты не смогут присоединяться.
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
носитель: <Image name>|Указывает имя изображения.|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.|
mediaType: {Загрузка&#124;установки}|Указывает тип изображения. Обратите внимание, что этот параметр должен быть установлен для **установки** для Windows Server 2008.|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Указывает архитектуру загрузочного образа, связанного с передачей для запуска. Так как для образов загрузки в разных архитектурах можно использовать одно и то же имя образа, следует указать архитектуру, чтобы гарантировать использование правильной передачи.|
|\Медиаграуп: <Image group name>]|Указывает группу образов, содержащую образ. Если имя группы образов не указано и на сервере существует только одна группа образов, используется эта группа образов. Если на сервере существует несколько групп образов, необходимо использовать этот параметр, чтобы указать имя группы образов.|
|[/Филенаме: <File name>]|Указывает имя файла. Если исходный образ не может быть однозначно определен по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|/Force|удаляет передачу и завершает работу всех клиентов. Если не указано значение параметра **/Force** , существующие клиенты могут завершить перенос образа, но новые клиенты не смогут присоединиться.|
## <a name="BKMK_examples"></a>Примеров
Для завершения передачи пространства имен (текущие клиенты будут выполнять передачу, но новые клиенты не смогут присоединиться) введите:
```
wdsutil /remove-MulticastTransmissiomedia:"Vista with Office"
/Imagetype:Install
```
```
wdsutil /remove-MulticastTransmissiomedia:"x64 Boot Image"
/Imagetype:Boot /Architecture:x64
```
Для принудительного завершения работы всех клиентов введите:
```
wdsutil /remove-MulticastTransmission /Server:MyWDSServer
/Image:"Vista with Officemediatype:InstalmediaGroup:ImageGroup1
/Filename:install.wim /force
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды get-аллмултикасттрансмиссионс](using-the-get-allmulticasttransmissions-command.md)
 с[помощью команды Get-Мултикасттрансмиссион](using-the-get-multicasttransmission-command.md)
[с помощью команды New-мултикасттрансмиссион](using-the-new-multicasttransmission-command.md)
[ . Подкоманда: Start-Мултикасттрансмиссион](subcommand-start-multicasttransmission.md)
