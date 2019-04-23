---
title: С помощью команды get-AutoaddDevices
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 337c8e76923fe243982ba9c10d18f2e5a5e7d9ff
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59885745"
---
# <a name="using-the-get-autoadddevices-command"></a>С помощью команды get-AutoaddDevices

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает все компьютеры, которые находятся в базе данных автоматического добавления на сервере служб развертывания Windows.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices | ApprovedDevices}
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|/ Devicetype: {PendingDevices &#124; RejectedDevices &#124; ApprovedDevices}|Указывает тип компьютера для возврата.<br /><br />-   **PendingDevices** список всех компьютеров в базе данных, имеют состояние ожидания.<br />-   **RejectedDevices** список всех компьютеров в базе данных, что состояние отклонили.<br />-   **ApprovedDevices** список всех компьютеров в базе данных, что состояние утверждения.|
## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть все из утвержденных компьютеров, введите следующую команду:
```
wdsutil /Get-AutoaddDevices /Devicetype:ApprovedDevices
```
Чтобы просмотреть все отклоненные компьютеры, введите:
```
wdsutil /verbose /Get-AutoaddDevices /Devicetype:RejectedDevices /Server:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды delete-AutoaddDevices](using-the-delete-autoadddevices-command.md)
[с помощью команды утвердить-AutoaddDevices](using-the-approve-autoadddevices-command.md) 
 [ С помощью команды AutoaddDevices отклонения](using-the-reject-autoadddevices-command.md)
