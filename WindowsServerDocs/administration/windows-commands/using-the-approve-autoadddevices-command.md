---
title: С помощью команды утвердить AutoaddDevices
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d76e8d3-ab35-429c-be7b-904f95d0782d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9ce9824c45a00ccb9f1f9e357c7e3d36b2857f69
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59886825"
---
# <a name="using-the-approve-autoadddevices-command"></a>С помощью команды утвердить AutoaddDevices

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Утверждает компьютеры, которые ожидают утверждения администратора. При включении политики автоматического добавления административное утверждение является обязательным, перед установкой образа неизвестные компьютеры (те, которые не были предварительно настроены). Вы можете включить этой политики с помощью **Отклик PXE** вкладки на странице свойств сервера s.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Approve-AutoaddDevices [/Server:<Server name>] /RequestId:{<Request ID>| ALL} [/MachineName:<Device name>] [/OU:<DN of OU>] 
[/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/ReferralServer:<Server name>] [/BootProgram:<Relative path>] [/WdsClientUnattend:<Relative path>] [/BootImagepath:<Relative path>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|/RequestId:{Request ID &#124; ALL}|Указывает идентификатор запроса, назначенный для ожидающего компьютера. Укажите **все** утверждение всех ожидающих компьютеров.|
|[/ MachineName:<Device name>]|Указывает имя компьютера для добавления. Этот параметр нельзя использовать при утверждении всех компьютеров.|
|[/ OU:<DN of OU>]|Задает различающееся имя подразделения (OU), где должен будет создан объект учетной записи компьютера. Пример: **OU = MyOU, CN = Test, DC = Domain, DC = com**. Расположение по умолчанию является контейнером компьютера по умолчанию.|
|[/User:<Domain\User &#124; User@Domain>]|Задает разрешения для объекта учетной записи компьютера для назначения необходимых прав для указанного пользователя.|
|[/JoinRights:{JoinOnly &#124; Full}]|Указывает тип прав для назначения для указанного пользователя.<br /><br />-   **JoinOnly** требует от администратора для сброса учетной записи компьютера, прежде чем пользователь может подключить компьютер к домену.<br />-   **Полный** дает полный доступ для пользователя, который включает в себя права для присоединения компьютера к домену.|
|[/ JoinDomain: {Да &#124; No}]|Указывает ли компьютер должен быть присоединен к домену как эта учетная запись компьютера во время установки операционной системы. Значение по умолчанию — **Да**.|
|[/ ReferralServer:<Server name>]|Указывает имя сервера для обращения к скачиванию образа программы и загрузки загрузки сети, используя упрощенный протокол передачи файлов (tftp).|
|[/ BootProgram:<Relative path>]|Указывает относительный путь из папки remoteInstall к программе сетевой загрузки, который должен получать этот компьютер. Например: **boot\x86\pxeboot.com**.|
|[/ WdsClientUnattend:<Relative path>]|Указывает относительный путь из папки remoteInstall в файл автоматической установки, который автоматизирует клиента служб развертывания Windows.|
|[/ BootImagepath:<Relative path>]|Указывает относительный путь из папки remoteInstall в загрузочный образ, который должен получать этот компьютер.|
## <a name="BKMK_examples"></a>Примеры
Чтобы утвердить компьютер с RequestId 12, введите:
```
wdsutil /Approve-AutoaddDevices /RequestId:12
```
Чтобы утвердить компьютер с RequestID 20 и развертывание образа с указанными параметрами, введите следующую команду:
```
wdsutil /Approve-AutoaddDevices /RequestId:20 /MachineName:computer1 /OU:"OU=Test,CN=company,DC=Domain,DC=Com" /User:Domain\User1 
/JoinRights:Full /ReferralServer:MyWDSServer /BootProgram:boot\x86\pxeboot.n12 /WdsClientUnattend:WDSClientUnattend\Unattend.xml /BootImagepath:boot\x86\images\boot.wim
```
Утверждение всех ожидающих компьютеров, введите следующую команду:
```
wdsutil /verbose /Approve-AutoaddDevices /RequestId:ALL
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды delete-AutoaddDevices](using-the-delete-autoadddevices-command.md)
[с помощью команды get-AutoaddDevices](using-the-get-autoadddevices-command.md) 
 [С помощью команды AutoaddDevices отклонения](using-the-reject-autoadddevices-command.md)
