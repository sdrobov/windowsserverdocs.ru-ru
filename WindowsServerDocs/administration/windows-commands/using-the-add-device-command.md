---
title: Использование команды Add-Device
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1e599cc4-464a-421b-b6bb-c101af154131
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 475db63af52df0f26a09e2a8312c4910277e4c0f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363851"
---
# <a name="using-the-add-device-command"></a>Использование команды Add-Device

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Предварительная настройка компьютера в доменных службах Active Directory. Предварительно подготовленные компьютеры также называются известными компьютерами. Это позволяет настроить свойства для управления установкой клиента. Например, можно настроить программу сетевой загрузки и файл автоматической установки, который должен получить клиент, а также сервер, с которого клиент должен загрузить программу сетевой загрузки.
Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).
## <a name="syntax"></a>Синтаксис
```
wdsutil /add-Device /Device:<Device name> /ID:<UUID | MAC address> [/ReferralServer:<Server name>] [/BootProgram:<Relative path>] [/WdsClientUnattend:<Relative path>] 
[/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/BootImagepath:<Relative path>] [/OU:<DN of OU>] [/Domain:<Domain>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/Девице: <computer name>|Указывает имя добавляемого компьютера.|
|/ID: < UUID &#124; MAC Address >|Указывает идентификатор GUID/UUID или MAC-адрес компьютера. GUID/UUID должны быть в одном из двух форматов: двоичная строка или строка GUID. Пример:<br /><br />Двоичная строка: **/ID: ACEFA3E81F20694E953EB2DAA1E8B1B6**<br /><br />Строка GUID: **/ID: E8A3EFAC-201F-4E69-953E-B2DAA1E8B1B6**<br /><br />MAC-адрес должен иметь следующий формат: **00B056882FDC** (без тире) или **00-B0-56-88-2F-DC** (с тире)|
|[/Реферралсервер: <Server name>]|Указывает имя сервера, к которому нужно подключиться для загрузки программы сетевой загрузки и загрузочного образа с помощью тривиальных протокол FTP (TFTP).|
|[/Бутпрограм: <Relative path>]|Указывает относительный путь от папки remoteInstall к программе сетевой загрузки, которую должен получить этот компьютер. Например: "boot\x86\pxeboot.com"|
|[/Вдсклиентунаттенд: <Relative path>]|Указывает относительный путь от папки remoteInstall к файлу автоматической установки, который автоматизирует экраны установки клиента служб развертывания Windows.|
|[/User: < домен &#124; \ пользователь User@Domain >]|Задает разрешения для объекта учетной записи компьютера, чтобы предоставить указанному пользователю необходимые права для приподключения компьютера к домену.|
|[/Жоинригхтс: {Жоинонли &#124; Full}]|Указывает тип прав, назначаемых пользователю.<br /><br />-   **жоинонли** требует, чтобы администратор переустановил учетную запись компьютера, прежде чем пользователь сможет присоединить компьютер к домену.<br />-   **Full** предоставляет пользователю полный доступ, который включает в себя право присоединить компьютер к домену.|
|[/Жоиндомаин: {Да &#124; }]|Указывает, должен ли компьютер быть присоединен к домену как учетная запись компьютера во время установки операционной системы. Значение по умолчанию — **Да**.|
|[/Бутимажепас: <Relative path>]|Указывает относительный путь от папки remoteInstall к загрузочному образу, который должен использоваться этим компьютером.|
|[/OU: <DN of OU>]|Различающееся имя подразделения, в котором должен быть создан объект учетной записи компьютера. Пример: **OU = MyOU, CN = тест, DC = Domain, DC = com**. Расположение по умолчанию — это контейнер компьютера по умолчанию.|
|[/Domain: <Domain>]|Домен, в котором должен быть создан объект учетной записи компьютера. Расположение по умолчанию — локальный домен.|
## <a name="BKMK_examples"></a>Примеров
Чтобы добавить компьютер с помощью MAC-адреса, введите:
```
wdsutil /add-Device /Device:computer1 /ID:00-B0-56-88-2F-DC
```
Чтобы добавить компьютер с помощью строки GUID, введите:
```
wdsutil /add-Device /Device:computer1 /ID:{E8A3EFAC-201F-4E69-953F-B2DAA1E8B1B6} /ReferralServer:WDSServer1 /BootProgram:boot\x86\pxeboot.com 
/WDSClientUnattend:WDSClientUnattend\unattend.xml /User:Domain\MyUser/JoinRights:Full /BootImagepath:boot\x86\images\boot.wim /OU:"OU=MyOU,CN=Test,DC=Domain,DC=com"
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды get-аллдевицес](using-the-get-alldevices-command.md)
[с помощью команды Get-Device](using-the-get-device-command.md)
[подкоманда: Set-Device](subcommand-set-device.md)
[New-WdsClient](https://technet.microsoft.com/library/dn283430.aspx)
