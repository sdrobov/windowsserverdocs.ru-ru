---
title: С помощью команды новый MulticastTransmission
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 84f5aa69f2d4a875995ac6c18fa43bd68518fba3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59875145"
---
# <a name="using-the-new-multicasttransmission-command"></a>С помощью команды новый MulticastTransmission

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает новый многоадресной передачи для изображения. Эта команда эквивалентно созданию передачи с помощью оснастки mmc служб развертывания Windows (щелкните правой кнопкой мыши **передачи многоадресной рассылки** узел, а затем щелкните **создания многоадресной передачи**). Эту команду следует использовать, когда у вас есть служба роли сервера развертывания и транспортный сервер установлена служба роли (это установка по умолчанию). Если у вас есть только транспортный сервер установлена служба роли, используйте [с помощью команды новое пространство имен](using-the-new-namespace-command.md).
## <a name="syntax"></a>Синтаксис
для передачи образов установки:
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
для передачи образа загрузки (поддерживается только для Windows Server 2008 R2):
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
мультимедиа:<Image name>|Указывает имя образа для передачи с использованием многоадресной рассылки.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|/ FriendlyName:<Friendly name>|Указывает понятное имя для передачи.|
|[/ Description:<Description>]|Указывает описание для передачи.|
Тип носителя: {загрузки&#124;установить}|Задает тип образа для передачи с использованием многоадресной рассылки. Примечание **загрузки** поддерживается только для Windows Server 2008 R2.|
|\mediaGroup:<Image group name>]|Указывает группу образов, содержащий изображение. Если указано имя группы не образа и только один образ группа существует на сервере, будет использоваться этой группы образов. Если на сервере существует более одной группы образов, необходимо использовать этот параметр, чтобы указать имя группы.|
|[/ Filename:<File name>]|Указывает имя файла. Если исходное изображение не может быть однозначно идентифицируется по имени, необходимо использовать этот параметр, чтобы указать имя файла.|
|/Transmissiontype:{AutoCast &#124; ScheduledCast}|Указывает, следует ли автоматически начнет передачу (AutoCast) или на основе критериев указанной начальной (ScheduledCast).<br /><br /><ul><li>**Автоматическая передача**. Этот тип передачи указывает, что как только соответствующий клиент запрашивает образа установки, многоадресной передачи выбранного образа начинается. Как другие клиенты запрашивают тот же образ, они объединяются на передачу, который уже запущен.</li><li>**Рассылка по расписанию**. Этот тип передачи задает условия для передачи данных, в зависимости от количества клиентов, запрашивающих образ и/или в определенный день и время начала. Можно указать следующие параметры:<br /><br /><ul><li>[/ time: <time>] — Задает время начала передачи, используя следующий формат: ГГГГ/мм/DD:hh:mm.</li><li>[/ Клиентов: <Number of clients>] — Задает минимальное число клиентов для ожидания перед началом передачи.</li></ul></li></ul>|
|/ Архитектура: {x86 &#124; ia64 &#124; x64}|Задает архитектуру загрузочного образа для передачи с использованием многоадресной рассылки. Так как это может быть то же имя для загрузочных образов для различных архитектур, следует указать архитектуры, чтобы убедиться, что используется правильный образ.|
|[/ Filename:<File name>]|Указывает имя файла. Если исходное изображение не может быть однозначно идентифицируется по имени, необходимо указать имя файла.|
## <a name="BKMK_examples"></a>Примеры
Чтобы создать автоматической рассылки образа загрузки в Windows Server 2008 R2, введите следующую команду:
```
wdsutil /New-MulticastTransmission /FriendlyName:"WDS Boot Transmission"
/Image:"X64 Boot Imagemediatype:Boot /Architecture:x64 /Transmissiontype:AutoCast
```
Чтобы создать автоматической рассылки образа установки, введите следующую команду:
```
wdsutil /New-MulticastTransmission /FriendlyName:"WDS AutoCast Transmission"
/Image:"Vista with Officemediatype:Install /Transmissiontype:AutoCast
```
Чтобы создать передачу рассылкой по расписанию образа установки, введите:
```
wdsutil /New-MulticastTransmission /FriendlyName:"WDS SchedCast Transmission" /Server:MyWDSServemedia:"Vista with Officemediatype:Install 
/Transmissiontype:ScheduledCast /time:"2006/11/20:17:00" /Clients:100
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды get-AllMulticastTransmissions](using-the-get-allmulticasttransmissions-command.md)
[с помощью команды get-MulticastTransmission](using-the-get-multicasttransmission-command.md) 
 [С помощью команды remove-MulticastTransmission](using-the-remove-multicasttransmission-command.md)
[подкоманда: start-MulticastTransmission](subcommand-start-multicasttransmission.md)
