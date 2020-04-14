---
title: Delete — Аутоадддевицес
description: Команды Windows для DELETE-Аутоадддевицес, которые удаляют компьютеры, которые ожидают, отклонены или утверждены из базы данных автоматического добавления.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8dcaca6a-212e-4c36-98e3-00938eef6b9c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 29df0bd92859e9ee0b5b5bedfbd2e66173059cb5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831667"
---
# <a name="delete-autoadddevices"></a>Delete — Аутоадддевицес

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет из базы данных автоматического добавления компьютеры, которые ожидают, отклонены или утверждены. Эта база данных хранит сведения об этих компьютерах на сервере.

## <a name="syntax"></a>Синтаксис
```
wdsutil /delete-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices |ApprovedDevices}
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Девицетипе: {Пендингдевицес &#124; режектеддевицес &#124;аппроведдевицес}|Указывает тип компьютера, удаляемого из базы данных. Это может быть любой из следующих трех типов:<p>-   **пендингдевицес** возвращает все компьютеры в базе данных с состоянием "ожидание".<br />-   **режектеддевицес** возвращает все компьютеры в базе данных, состояние которых было отклонено.<br />-   **аппроведдевицес** возвращает все компьютеры, состояние "утверждено".|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы удалить все отклоненные компьютеры, введите:
```
wdsutil /delete-AutoaddDevices /Devicetype:RejectedDevices
```
Чтобы удалить все утвержденные компьютеры, введите:
```
wdsutil /verbose /delete-AutoaddDevices /Server:MyWDSServer /Devicetype:ApprovedDevices
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды "утвердить-Аутоадддевицес](using-the-approve-autoadddevices-command.md) "
[помощью команды Get-Аутоадддевицес,](using-the-get-autoadddevices-command.md)
[с помощью команды "отклонить-аутоадддевицес"](using-the-reject-autoadddevices-command.md)
