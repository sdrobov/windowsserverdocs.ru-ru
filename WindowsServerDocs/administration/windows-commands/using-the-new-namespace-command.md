---
title: Использование команды New-Namespace
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6df60703-30bd-4d59-a8d9-9fe3efe96add
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1df6634bc7598701db050f3d240e41dbb6f06019
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363015"
---
# <a name="using-the-new-namespace-command"></a>Использование команды New-Namespace

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

создает и настраивает новое пространство имен. Этот параметр следует использовать, если установлена только служба роли транспортного сервера. Если у вас установлена служба роли сервера развертывания и служба роли транспортного сервера (по умолчанию), используйте [команду New-мултикасттрансмиссион](using-the-new-multicasttransmission-command.md). Обратите внимание, что перед использованием этого параметра необходимо зарегистрировать поставщик содержимого.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /New-Namespace [/Server:<Server name>]
     /FriendlyName:<Friendly name>
     [/Description:<Description>]
     /Namespace:<Namespace name>
     /ContentProvider:<Name>
     [/ConfigString:<Configuration string>]
     /Namespacetype: {AutoCast | ScheduledCast}
         [/time:<YYYY/MM/DD:hh:mm>]
         [/Clients:<Number of clients>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.|
|/FriendlyName: <Friendly name>|Указывает понятное имя пространства имен.|
|/Description<Description>]|Задает описание пространства имен.|
|/Namespace: <Namespace name>|Указывает имя пространства имен. Обратите внимание, что это не понятное имя, оно должно быть уникальным.<br /><br />**служба роли сервера развертывания**-   : Для этого параметра используется синтаксис/namespace: WDS: <Image group> @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4. Пример: **WDS: ImageGroup1/install. wim/1**<br />**служба роли транспортного сервера**-   : Это значение должно совпадать с именем, заданным при создании пространства имен на сервере.|
|/Контентпровидер: <Name>]|Указывает имя поставщика содержимого, который предоставит содержимое для пространства имен.|
|[/Конфигстринг: <Configuration string>]|Задает строку конфигурации для поставщика содержимого.|
|/Намеспацетипе: {автотрансляция &#124; счедуледкаст}|Задает параметры передачи. Параметры задаются с помощью следующих параметров.<br /><br />-[/Тиме: <time>] — задает время начала передачи с использованием следующего формата: ГГГГ/мм/дд: чч: мм. Этот параметр применяется только к передачам по расписанию.<br />-[/Клиентс: <Number of clients>] — задает минимальное число клиентов для ожидания перед началом передачи. Этот параметр применяется только к передачам по расписанию.|
## <a name="BKMK_examples"></a>Примеров
Чтобы создать пространство имен автоматического приведения, введите:
```
wdsutil /New-Namespace /FriendlyName:"Custom AutoCast Namespace" /Namespace:"Custom Auto 1" /ContentProvider:MyContentProvider /Namespacetype:AutoCast
```
Чтобы создать пространство имен с расписанием, введите:
```
wdsutil /New-Namespace /Server:MyWDSServer /FriendlyName:"Custom Scheduled Namespace" /Namespace:"Custom Auto 1" /ContentProvider:MyContentProvider 
/Namespacetype:ScheduledCast /time:"2006/11/20:17:00" /Clients:20
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды get-аллнамеспацес](using-the-get-allnamespaces-command.md)
[с помощью команды Remove-Namespace](using-the-remove-namespace-command.md)
[подкоманда: Start-Namespace](subcommand-start-namespace.md)
