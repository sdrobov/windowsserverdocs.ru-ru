---
title: С помощью команды новое пространство имен
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 50d51101afe95c99b7034fc50b3d30b799ee02ce
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59871155"
---
# <a name="using-the-new-namespace-command"></a>С помощью команды новое пространство имен

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает и настраивает новое пространство имен. Этот параметр следует использовать при наличии только транспортный сервер установлена служба роли. Если у вас есть служба роли сервера развертывания и службы роли транспортного сервера установлен (по умолчанию), используйте [с помощью команды новый MulticastTransmission](using-the-new-multicasttransmission-command.md). Обратите внимание на то, что необходимо зарегистрировать поставщика содержимого, прежде чем использовать этот параметр.
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
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, используется локальный сервер.|
|/ FriendlyName:<Friendly name>|Указывает понятное имя пространства имен.|
|[/ Description:<Description>]|Задает описание пространства имен.|
|/ Пространство имен:<Namespace name>|Задает имя пространства имен. Обратите внимание, что это не понятное имя, и оно должно быть уникальным.<br /><br />-   **Служба роли сервера развертывания**: Для этого параметра используется следующий синтаксис /Namespace:WDS:<Image group>/<Image name>/<Index>. Пример: **WDS:ImageGroup1/Install.wim/1**<br />-   **Служба роли сервера транспорта**: Это значение должно соответствовать имени, заданное при создании пространства имен, на сервере.|
|/ Поставщик содержимого:<Name>]|Указывает имя поставщика содержимого, которое предоставляет содержимое для пространства имен.|
|[/ ConfigString:<Configuration string>]|Строка конфигурации для поставщика содержимого.|
|/Namespacetype: {AutoCast &#124; ScheduledCast}|Задает параметры для передачи. Необходимо указать параметры, используя следующие параметры:<br /><br />-[/ time: <time>] — Задает время начала передачи, используя следующий формат: ГГГГ/мм/DD:hh:mm. Этот параметр применяется только к рассылки по расписанию.<br />-[/ Клиентов: <Number of clients>] — Задает минимальное число клиентов для ожидания перед началом передачи. Этот параметр применяется только к рассылки по расписанию.|
## <a name="BKMK_examples"></a>Примеры
Чтобы создать пространство имен Автоматическая передача, введите:
```
wdsutil /New-Namespace /FriendlyName:"Custom AutoCast Namespace" /Namespace:"Custom Auto 1" /ContentProvider:MyContentProvider /Namespacetype:AutoCast
```
Чтобы создать пространство имен рассылкой по расписанию, введите следующую команду:
```
wdsutil /New-Namespace /Server:MyWDSServer /FriendlyName:"Custom Scheduled Namespace" /Namespace:"Custom Auto 1" /ContentProvider:MyContentProvider 
/Namespacetype:ScheduledCast /time:"2006/11/20:17:00" /Clients:20
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды get-AllNamespaces](using-the-get-allnamespaces-command.md)
[с помощью команды remove-Namespace](using-the-remove-namespace-command.md) 
 [ Подкоманда: start-пространство имен](subcommand-start-namespace.md)
