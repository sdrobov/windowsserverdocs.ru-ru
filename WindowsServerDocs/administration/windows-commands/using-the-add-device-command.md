---
title: С помощью команды add устройства
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 85e9ef4445b4dabbe85c2397d62b06756e17879d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59878545"
---
# <a name="using-the-add-device-command"></a>С помощью команды add устройства

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Предварительно подготавливает компьютер в доменных службах active directory. Подготовленных компьютеров также называются известных компьютеров. Это позволяет настроить свойства для управления установкой для клиента. Например можно настроить программу сетевой загрузки и файл автоматической установки, который должен получать клиент, а также сервер, с которого клиент должен загружать программу сетевой загрузки.
Примеры об использовании этой команды, см. в разделе [примеры](#BKMK_examples).
## <a name="syntax"></a>Синтаксис
```
wdsutil /add-Device /Device:<Device name> /ID:<UUID | MAC address> [/ReferralServer:<Server name>] [/BootProgram:<Relative path>] [/WdsClientUnattend:<Relative path>] 
[/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/BootImagepath:<Relative path>] [/OU:<DN of OU>] [/Domain:<Domain>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ Устройство:<computer name>|Указывает имя компьютера для добавления.|
|/ID:<UUID &#124; MAC address>|Указывает GUID/UUID или MAC-адрес компьютера. GUID/UUID должен находиться в одном из двух форматов двоичная строка или строка идентификатора GUID. Пример:<br /><br />Двоичная строка: **/ID:ACEFA3E81F20694E953EB2DAA1E8B1B6**<br /><br />Строка идентификатора GUID: **/ID:E8A3EFAC-201F-4E69-953E-B2DAA1E8B1B6**<br /><br />MAC-адрес должен быть в следующем формате: **00B056882FDC** (без дефисов) или **00-B0-56-88-2F-DC** (с дефисами)|
|[/ ReferralServer:<Server name>]|Указывает имя сервера, связь для загрузки программы сетевой загрузки и образа загрузки, используя упрощенный протокол передачи файлов (tftp).|
|[/ BootProgram:<Relative path>]|Указывает относительный путь из папки remoteInstall к программе сетевой загрузки, который должен получать этот компьютер. Например: «boot\x86\pxeboot.com»|
|[/ WdsClientUnattend:<Relative path>]|Указывает относительный путь из папки remoteInstall в файл автоматической установки, который автоматизирует экраны установки клиента служб развертывания Windows.|
|[/User:<Domain\User &#124; User@Domain>]|Задает разрешения для объекта учетной записи компьютера, чтобы предоставить пользователю права, необходимые для присоединения компьютера к домену.|
|[/JoinRights:{JoinOnly &#124; Full}]|Указывает тип прав для назначения пользователю.<br /><br />-   **JoinOnly** требует от администратора для сброса учетной записи компьютера, прежде чем пользователь может подключить компьютер к домену.<br />-   **Полный** дает полный доступ для пользователя, который включает в себя права для присоединения компьютера к домену.|
|[/ JoinDomain: {Да &#124; No}]|Указывает ли компьютер должен быть присоединен к домену как эта учетная запись компьютера во время установки операционной системы. Значение по умолчанию — **Да**.|
|[/ BootImagepath:<Relative path>]|Указывает относительный путь из папки remoteInstall в загрузочный образ, который следует использовать этот компьютер.|
|[/ OU:<DN of OU>]|Различающееся имя подразделения, в котором должен будет создан объект учетной записи компьютера. Пример: **OU = MyOU, CN = Test, DC = Domain, DC = com**. Расположение по умолчанию — контейнер по умолчанию на компьютере.|
|[/ Домена:<Domain>]|Домен, в котором должен будет создан объект учетной записи компьютера. По умолчанию находится в локальном домене.|
## <a name="BKMK_examples"></a>Примеры
Чтобы добавить компьютер с помощью MAC-адрес, введите:
```
wdsutil /add-Device /Device:computer1 /ID:00-B0-56-88-2F-DC
```
Чтобы добавить компьютер с помощью строка идентификатора GUID, введите:
```
wdsutil /add-Device /Device:computer1 /ID:{E8A3EFAC-201F-4E69-953F-B2DAA1E8B1B6} /ReferralServer:WDSServer1 /BootProgram:boot\x86\pxeboot.com 
/WDSClientUnattend:WDSClientUnattend\unattend.xml /User:Domain\MyUser/JoinRights:Full /BootImagepath:boot\x86\images\boot.wim /OU:"OU=MyOU,CN=Test,DC=Domain,DC=com"
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды get-AllDevices](using-the-get-alldevices-command.md)
[с помощью команды get устройств](using-the-get-device-command.md)
[подкоманда: SET-Device](subcommand-set-device.md)
[New WdsClient](https://technet.microsoft.com/library/dn283430.aspx)
