---
title: С помощью команды delete-AutoaddDevices
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8dcaca6a-212e-4c36-98e3-00938eef6b9c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8b3375418c5ce0b02e187e292cac5b168f0de5dc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813505"
---
# <a name="using-the-delete-autoadddevices-command"></a>С помощью команды delete-AutoaddDevices

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет компьютеры, находящиеся в ожидании, отклонен или утверждения из базы данных автоматического добавления. Эта база данных хранит сведения об этих компьютеров на сервере.
## <a name="syntax"></a>Синтаксис
```
wdsutil /delete-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices |ApprovedDevices}
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|/ Devicetype: {PendingDevices &#124; RejectedDevices &#124;ApprovedDevices}|Указывает тип компьютера для удаления из базы данных. Это может быть любой из следующих трех типов:<br /><br />-   **PendingDevices** список всех компьютеров в базе данных, имеют состояние ожидания.<br />-   **RejectedDevices** список всех компьютеров в базе данных, что состояние отклонили.<br />-   **ApprovedDevices** отображается список всех компьютеров, которые имеют состояние утверждения.|
## <a name="BKMK_examples"></a>Примеры
Для удаления всех отклоненных компьютеров, введите следующую команду:
```
wdsutil /delete-AutoaddDevices /Devicetype:RejectedDevices
```
Для удаления всех утвержденных компьютеров, введите следующую команду:
```
wdsutil /verbose /delete-AutoaddDevices /Server:MyWDSServer /Devicetype:ApprovedDevices
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды утвердить-AutoaddDevices](using-the-approve-autoadddevices-command.md)
[с помощью команды get-AutoaddDevices](using-the-get-autoadddevices-command.md) 
 [С помощью команды AutoaddDevices отклонения](using-the-reject-autoadddevices-command.md)
