---
title: Get-Аутоадддевицес
description: Раздел команд Windows для Get-Аутоадддевицес, в котором отображаются все компьютеры, которые находятся в базе данных автоматического добавления на сервере служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 24b4b688-55b0-4bd9-a2f5-7ef4b3dfe2f2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b373fca81769ff1296d0e9a0788fe536c4fc3132
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831187"
---
# <a name="get-autoadddevices"></a>Get-Аутоадддевицес

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает все компьютеры, которые находятся в базе данных автоматического добавления на сервере служб развертывания Windows.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices | ApprovedDevices}
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Девицетипе: {Пендингдевицес &#124; режектеддевицес &#124; аппроведдевицес}|Указывает тип возвращаемого компьютера.<p>-   **пендингдевицес** возвращает все компьютеры в базе данных с состоянием "ожидание".<br />-   **режектеддевицес** возвращает все компьютеры в базе данных, состояние которых было отклонено.<br />-   **аппроведдевицес** возвращает все компьютеры в базе данных с состоянием утверждено.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы просмотреть список всех утвержденных компьютеров, введите:
```
wdsutil /Get-AutoaddDevices /Devicetype:ApprovedDevices
```
Чтобы просмотреть список всех отклоненных компьютеров, введите:
```
wdsutil /verbose /Get-AutoaddDevices /Devicetype:RejectedDevices /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды Delete-Аутоадддевицес](using-the-delete-autoadddevices-command.md) ,
[помощью команды "утвердить-Аутоадддевицес](using-the-approve-autoadddevices-command.md) "
[помощью команды "отклонить-аутоадддевицес"](using-the-reject-autoadddevices-command.md)
