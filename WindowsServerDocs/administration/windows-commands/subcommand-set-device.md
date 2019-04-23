---
title: Подкоманды set-Device
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 401567f8-eaeb-4a2d-b811-140bb007028d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 80bb9144936cf493784603bcbdb8a0d1e5c870bd
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59848065"
---
# <a name="subcommand-set-device"></a>Подкоманда: set-Device

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет атрибуты предварительно настроенного компьютера. Предварительно настроенный компьютер — это компьютер, на который была связана с объектом учетной записи компьютера в серверах домена active directory (AD DS). Предварительно настроенным клиентам, также называются известных компьютеров. Можно настроить свойства учетной записи компьютера, для управления установкой для клиента. Например можно настроить программу сетевой загрузки и файл автоматической установки, который должен получать клиент, а также сервер, с которого клиент должен загружать программу сетевой загрузки.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Set-Device /Device:<Device name> [/ID:<UUID | MAC address>] [/ReferralServer:<Server name>] [/BootProgram:<Relative path>] 
[/WdsClientUnattend:<Relative path>] [/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/BootImagepath:<Relative path>] [/Domain:<Domain>] [/resetAccount]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ Устройство:<computer name>|Указывает имя компьютера (SAM-Account-Name).|
|[/ Идентификатор: < UUID &#124; MAC-адрес >]|Указывает GUID/UUID или MAC-адрес компьютера. Это значение должно быть одним из следующих трех форматах:<br /><br />-Двоичная строка: **/ID:ACEFA3E81F20694E953EB2DAA1E8B1B6**<br />-Строка идентификатор GUID/UUID: / идентификатор:**E8A3EFAC-201F-4E69-953E-B2DAA1E8B1B6**<br />-MAC адрес: **00B056882FDC** (без дефисов) или **00-B0-56-88-2F-DC** (с дефисами)|
|[/ ReferralServer:<Server name>]|Указывает имя сервера, связь для загрузки сети программа и загрузочный образ загрузки с помощью упрощенный протокол передачи файлов (tftp).|
|[/ BootProgram:<Relative path>]|Указывает относительный путь из папки remoteInstall к программе сетевой загрузки, который получит указанный компьютер. Например: **boot\x86\pxeboot.com**|
|[/ WdsClientUnattend:<Relative path>]|Указывает относительный путь из папки remoteInstall в файл автоматической установки, который автоматизирует экраны установки для клиента служб развертывания Windows.|
|[/User:<Domain\User &#124; User@Domain>]|Задает разрешения для объекта учетной записи компьютера, чтобы предоставить пользователю права, необходимые для присоединения компьютера к домену.|
|[/JoinRights:{JoinOnly &#124; Full}]|Указывает тип прав для назначения пользователю.<br /><br />-   **JoinOnly** требует от администратора для сброса учетной записи компьютера, прежде чем пользователь может подключить компьютер к домену.<br />-   **Полный** дает полный доступ для пользователя, включая право на присоединение компьютера к домену.|
|[/ JoinDomain: {Да &#124; No}]|Указывает ли компьютер должен быть присоединен к домену как эта учетная запись компьютера во время установки служб развертывания Windows. Значение по умолчанию — **Да**.|
|[/ BootImagepath:<Relative path>]|Указывает относительный путь из папки remoteInstall в загрузочный образ, который будет использоваться компьютером.|
|[/ Домена:<Domain>]|Указывает домен, для поиска предварительно настроенного компьютера. Значение по умолчанию является локальным доменом.|
|[/resetAccount]|Сбрасывает разрешения на указанном компьютере, таким образом, чтобы любой пользователь с соответствующими разрешениями могут присоединиться к домену с помощью этой учетной записи.|
## <a name="BKMK_examples"></a>Примеры
Чтобы задать сервера программы и ссылок сетевой загрузки для компьютера, введите следующую команду:
```
wdsutil /Set-Device /Device:computer1 /ReferralServer:MyWDSServer
/BootProgram:boot\x86\pxeboot.n12
```
Чтобы задать различные параметры для компьютера, введите следующую команду:
```
wdsutil /verbose /Set-Device /Device:computer2 /ID:00-B0-56-88-2F-DC /WdsClientUnattend:WDSClientUnattend\unattend.xml 
/User:Domain\user /JoinRights:JoinOnly /JoinDomain:No /BootImagepath:boot\x86\images\boot.wim /Domain:NorthAmerica /resetAccount
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add Device](using-the-add-device-command.md)
[с помощью команды get-AllDevices](using-the-get-alldevices-command.md)
[Using Команда Get-Device](using-the-get-device-command.md)
