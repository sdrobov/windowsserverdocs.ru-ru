---
title: Использование команды Get-Аутоадддевицес
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 24b4b688-55b0-4bd9-a2f5-7ef4b3dfe2f2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fa30a8ebd73164dc3d8ab267c3deb0739aa4b700
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363251"
---
# <a name="using-the-get-autoadddevices-command"></a>Использование команды Get-Аутоадддевицес

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает все компьютеры, которые находятся в базе данных автоматического добавления на сервере служб развертывания Windows.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices | ApprovedDevices}
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Девицетипе: {Пендингдевицес &#124; режектеддевицес &#124; аппроведдевицес}|Указывает тип возвращаемого компьютера.<br /><br />-   **пендингдевицес** возвращает все компьютеры в базе данных с состоянием "ожидание".<br />-   **режектеддевицес** возвращает все компьютеры в базе данных, состояние которых было отклонено.<br />-   **аппроведдевицес** возвращает все компьютеры в базе данных, имеющие состояние "утверждено".|
## <a name="BKMK_examples"></a>Примеров
Чтобы просмотреть список всех утвержденных компьютеров, введите:
```
wdsutil /Get-AutoaddDevices /Devicetype:ApprovedDevices
```
Чтобы просмотреть список всех отклоненных компьютеров, введите:
```
wdsutil /verbose /Get-AutoaddDevices /Devicetype:RejectedDevices /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды delete-аутоадддевицес](using-the-delete-autoadddevices-command.md)
[с помощью команды "утвердить-Аутоадддевицес](using-the-approve-autoadddevices-command.md)" 
[с помощью команды "отклонить-аутоадддевицес"](using-the-reject-autoadddevices-command.md) .
