---
title: Get-Аутоадддевицес
description: Справочный раздел по Get-Аутоадддевицес, в котором отображаются все компьютеры, которые находятся в базе данных автоматического добавления на сервере служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 24b4b688-55b0-4bd9-a2f5-7ef4b3dfe2f2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c15836fa81c694aa9295d0a98376f4bef3125243
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719991"
---
# <a name="get-autoadddevices"></a>Get-Аутоадддевицес

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает все компьютеры, которые находятся в базе данных автоматического добавления на сервере служб развертывания Windows.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices | ApprovedDevices}
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Девицетипе: {Пендингдевицес &#124; Режектеддевицес &#124; Аппроведдевицес}|Указывает тип возвращаемого компьютера.<p>-   **Пендингдевицес** возвращает все компьютеры в базе данных с состоянием "ожидание".<br />-   **Режектеддевицес** возвращает все компьютеры в базе данных, состояние которых было отклонено.<br />-   **Аппроведдевицес** возвращает все компьютеры в базе данных, имеющие состояние "утверждено".|
## <a name="examples"></a>Примеры
Чтобы просмотреть список всех утвержденных компьютеров, введите:
```
wdsutil /Get-AutoaddDevices /Devicetype:ApprovedDevices
```
Чтобы просмотреть список всех отклоненных компьютеров, введите:
```
wdsutil /verbose /Get-AutoaddDevices /Devicetype:RejectedDevices /Server:MyWDSServer
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ](command-line-syntax-key.md)
синтаксиса командной строки[с помощью команды Delete-аутоадддевицес](using-the-delete-autoadddevices-command.md)
с командой rereject-[аутоадддевицес](using-the-approve-autoadddevices-command.md)
[с помощью команды "отклонить-аутоадддевицес"](using-the-reject-autoadddevices-command.md)
