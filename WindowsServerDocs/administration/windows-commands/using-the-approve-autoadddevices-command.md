---
title: Утвердить — Аутоадддевицес
description: Команда Windows для утверждения-Аутоадддевицес, которая утверждает компьютеры, ожидающие административного утверждения.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8d76e8d3-ab35-429c-be7b-904f95d0782d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b7f63faabf37337136cad186fd252915adf1a743
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831837"
---
# <a name="approve-autoadddevices"></a>Утвердить — Аутоадддевицес

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Утверждает компьютеры, ожидающие административного утверждения. Если включена политика автоматического добавления, то перед неизвестными компьютерами (не требующими предварительной подготовки) требуется административное утверждение, чтобы установить образ. Эту политику можно включить с помощью вкладки **Отклик PXE** страницы свойств сервера.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Approve-AutoaddDevices [/Server:<Server name>] /RequestId:{<Request ID>| ALL} [/MachineName:<Device name>] [/OU:<DN of OU>] 
[/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/ReferralServer:<Server name>] [/BootProgram:<Relative path>] [/WdsClientUnattend:<Relative path>] [/BootImagepath:<Relative path>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Рекуестид: {идентификатор &#124; запроса ALL}|Указывает идентификатор запроса, назначенный ожидающему компьютеру. Укажите **все** , чтобы утвердить все ожидающие компьютеры.|
|[/Мачиненаме:<Device name>]|Указывает имя добавляемого компьютера. Этот параметр нельзя использовать при утверждении всех компьютеров.|
|[/OU:<DN of OU>]|Определяет различающееся имя подразделения, в котором должен быть создан объект учетной записи компьютера. Например: **OU = MyOU, CN = test, DC = Domain, DC = com**. Расположение по умолчанию — это контейнер компьютера по умолчанию.|
|[/User: < домен &#124; \ пользователь User@Domain>]|Задает разрешения для объекта учетной записи компьютера, чтобы назначить указанного пользователя необходимые права.|
|[/Жоинригхтс: {Жоинонли &#124; Full}]|Указывает тип прав, назначаемых указанному пользователю.<p>-   **жоинонли** требует от администратора сброса учетной записи компьютера, прежде чем пользователь сможет присоединить компьютер к домену.<br />-   **Full** предоставляет пользователю полный доступ, который включает в себя право присоединить компьютер к домену.|
|[/Жоиндомаин: {Да &#124; }]|Указывает, должен ли компьютер быть присоединен к домену как учетная запись компьютера во время установки операционной системы. Значение по умолчанию — **Да**.|
|[/Реферралсервер:<Server name>]|Указывает имя сервера, к которому нужно подключиться для загрузки программы сетевой загрузки и загрузочного образа с помощью тривиальных протокол FTP (TFTP).|
|[/Бутпрограм:<Relative path>]|Указывает относительный путь от папки remoteInstall к программе сетевой загрузки, которую должен получить этот компьютер. Например: **boot\x86\pxeboot.com**.|
|[/Вдсклиентунаттенд:<Relative path>]|Указывает относительный путь от папки remoteInstall к файлу автоматической установки, который автоматизирует клиент служб развертывания Windows.|
|[/Бутимажепас:<Relative path>]|Указывает относительный путь от папки remoteInstall к загрузочному образу, который должен быть получен этим компьютером.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы утвердить компьютер с кодом запроса 12, введите:
```
wdsutil /Approve-AutoaddDevices /RequestId:12
```
Чтобы утвердить компьютер с ИД запроса 20 и развернуть образ с указанными параметрами, введите:
```
wdsutil /Approve-AutoaddDevices /RequestId:20 /MachineName:computer1 /OU:OU=Test,CN=company,DC=Domain,DC=Com /User:Domain\User1 
/JoinRights:Full /ReferralServer:MyWDSServer /BootProgram:boot\x86\pxeboot.n12 /WdsClientUnattend:WDSClientUnattend\Unattend.xml /BootImagepath:boot\x86\images\boot.wim
```
Чтобы утвердить все ожидающие компьютеры, введите:
```
wdsutil /verbose /Approve-AutoaddDevices /RequestId:ALL
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды Delete-Аутоадддевицес](using-the-delete-autoadddevices-command.md) ,
[помощью команды Get-Аутоадддевицес](using-the-get-autoadddevices-command.md) ,
[с помощью команды rereject-аутоадддевицес](using-the-reject-autoadddevices-command.md) .
