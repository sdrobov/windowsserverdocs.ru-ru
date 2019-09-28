---
title: Использование команды REJECT-Аутоадддевицес
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea25a4b2-5fad-4360-9c47-c2c9df7ea31f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2e8fda3037ef921e2b2a7a0acb616b8a67545ff9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363001"
---
# <a name="using-the-reject-autoadddevices-command"></a>Использование команды REJECT-Аутоадддевицес

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отклоняет компьютеры, ожидающие административного утверждения. Если включена политика автоматического добавления, то перед неизвестными компьютерами (не требующими предварительной подготовки) требуется административное утверждение, чтобы установить образ. Эту политику можно включить с помощью вкладки **Отклик PXE** страницы свойств сервера.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Reject-AutoaddDevices [/Server:<Server name>] /RequestId:<Request ID or ALL>
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Рекуестид: идентификатор &#124; запроса < Все >|Указывает идентификатор запроса, назначенный ожидающему компьютеру. Чтобы отклонить все ожидающие компьютеры, укажите **все**.|
## <a name="BKMK_examples"></a>Примеров
Чтобы отклонить отдельный компьютер, введите:
```
wdsutil /Reject-AutoaddDevices /RequestId:12
```
Чтобы отклонить все компьютеры, введите:
```
wdsutil /verbose /Reject-AutoaddDevices /Server:MyWDSServer /RequestId:ALL
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксис командной строки](command-line-syntax-key.md)
[с помощью команды "утвердить-аутоадддевицес](using-the-approve-autoadddevices-command.md)" 
[с помощью команды "Delete-Аутоадддевицес](using-the-delete-autoadddevices-command.md)" 
[с помощью команды Get-аутоадддевицес](using-the-get-autoadddevices-command.md) .
