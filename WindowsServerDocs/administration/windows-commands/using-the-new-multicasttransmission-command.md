---
title: Использование команды New-Мултикасттрансмиссион
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1f1dc46-dd50-4eb9-9f72-cf0e5d71bd3d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8a6893d34e8f1242966d644159823277cf71a0c0
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401988"
---
# <a name="using-the-new-multicasttransmission-command"></a>Использование команды New-Мултикасттрансмиссион

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

создает новую многоадресную передачу для образа. Эта команда эквивалентна созданию передачи с помощью оснастки MMC для служб развертывания Windows (щелкните правой кнопкой мыши узел **многоадресные** передачи и выберите команду **Создать многоадресную передачу**). Эту команду следует использовать при наличии установленной службы роли сервера развертывания и службы роли транспортного сервера (установка по умолчанию). Если установлена только служба роли транспортного сервера, используйте [команду New-Namespace](using-the-new-namespace-command.md).
## <a name="syntax"></a>Синтаксис
для передач образов установки:
```
wdsutil [Options] /New-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
        /FriendlyName:<Friendly name>
        [/Description:<Description>]
        /Transmissiontype: {AutoCast | ScheduledCast}
            [/time:<YYYY/MM/DD:hh:mm>]
            [/Clients:<Num of Clients>]
      mediatype:Install
       mediaGroup:<Image Group>]
        [/Filename:<File name>]
```
для передач загрузочных образов (поддерживается только для Windows Server 2008 R2):
```
wdsutil [Options] /New-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
        /FriendlyName:<Friendly name>
        [/Description:<Description>]
        /Transmissiontype: {AutoCast | ScheduledCast}
            [/time:<YYYY/MM/DD:hh:mm>]
            [/Clients:<Num of Clients>]
      mediatype:Boot
        /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
носитель: <Image name>|Указывает имя изображения, которое должно быть передано с помощью многоадресной рассылки.|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/FriendlyName: <Friendly name>|Указывает понятное имя передачи.|
|/Description<Description>]|Задает описание передачи.|
mediaType: {Установка&#124;загрузки}|Указывает тип изображения, передаваемого с помощью многоадресной рассылки. Примечание. **Загрузка** поддерживается только для Windows Server 2008 R2.|
|\Медиаграуп: <Image group name>]|Указывает группу образов, содержащую образ. Если имя группы образов не указано и на сервере существует только одна группа образов, используется эта группа образов. Если на сервере существует несколько групп образов, необходимо использовать этот параметр, чтобы указать имя группы образов.|
|[/Филенаме: <File name>]|Указывает имя файла. Если исходный образ не может быть однозначно определен по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|/Трансмиссионтипе: {автотрансляция &#124; счедуледкаст}|Указывает, следует ли начинать передачу автоматически (автотрансляцию) или на основе указанных критериев запуска (Счедуледкаст).<br /><br /><ul><li>**Автоматическое приведение**. Этот тип передачи указывает, что как только соответствующий клиент запрашивает установочный образ, начинается многоадресная передача выбранного образа. Поскольку другие клиенты запрашивают тот же образ, они присоединяются к уже запущенной передаче.</li><li>**Запланированное приведение**. Этот тип передачи задает критерий запуска для передачи на основе числа клиентов, запрашивающих образ, и/или определенного дня и времени. Можно указать следующие параметры.<br /><br /><ul><li>[/Тиме: <time>] — задает время начала передачи с использованием следующего формата: ГГГГ/мм/дд: чч: мм.</li><li>[/Клиентс: <Number of clients>] — задает минимальное число клиентов для ожидания перед началом передачи.</li></ul></li></ul>|
|/Арчитектуре: {x86 &#124; ia64 &#124; x64}|Указывает архитектуру загрузочного образа для передачи с помощью многоадресной рассылки. Так как для образов загрузки различных архитектур можно использовать одно и то же имя, необходимо указать архитектуру для обеспечения правильного использования образа.|
|[/Филенаме: <File name>]|Указывает имя файла. Если исходный образ не может быть однозначно определен по имени, необходимо указать имя файла.|
## <a name="BKMK_examples"></a>Примеров
Чтобы создать автоматическую передачу образа загрузки в Windows Server 2008 R2, введите:
```
wdsutil /New-MulticastTransmission /FriendlyName:"WDS Boot Transmission"
/Image:"X64 Boot Imagemediatype:Boot /Architecture:x64 /Transmissiontype:AutoCast
```
Чтобы создать автоматическую передачу образа установки, введите:
```
wdsutil /New-MulticastTransmission /FriendlyName:"WDS AutoCast Transmission"
/Image:"Vista with Officemediatype:Install /Transmissiontype:AutoCast
```
Чтобы создать запланированную передачу образа установки, введите:
```
wdsutil /New-MulticastTransmission /FriendlyName:"WDS SchedCast Transmission" /Server:MyWDSServemedia:"Vista with Officemediatype:Install 
/Transmissiontype:ScheduledCast /time:"2006/11/20:17:00" /Clients:100
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды get-аллмултикасттрансмиссионс](using-the-get-allmulticasttransmissions-command.md)
 с[помощью команды Get-Мултикасттрансмиссион](using-the-get-multicasttransmission-command.md)
[с помощью команды Remove-мултикасттрансмиссион](using-the-remove-multicasttransmission-command.md)
[ . Подкоманда: Start-Мултикасттрансмиссион](subcommand-start-multicasttransmission.md)
