---
title: С помощью команды AutoaddDevices отклонения
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: af46aec7c8f02b3600983b66bd1b0ac6f5dd1dcc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852565"
---
# <a name="using-the-reject-autoadddevices-command"></a>С помощью команды AutoaddDevices отклонения

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отклоняет компьютеров, ожидающих утверждения администратора. При включении политики автоматического добавления административное утверждение является обязательным, перед установкой образа неизвестные компьютеры (те, которые не были предварительно настроены). Вы можете включить этой политики с помощью **Отклик PXE** вкладки на странице свойств сервера s.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Reject-AutoaddDevices [/Server:<Server name>] /RequestId:<Request ID or ALL>
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|/RequestId:<Request ID &#124; ALL>|Указывает идентификатор запроса, назначенный для ожидающего компьютера. Чтобы отклонить все ожидающие компьютеры, укажите **все**.|
## <a name="BKMK_examples"></a>Примеры
Чтобы отклонить один компьютер, введите:
```
wdsutil /Reject-AutoaddDevices /RequestId:12
```
Чтобы отклонить все компьютеры, введите:
```
wdsutil /verbose /Reject-AutoaddDevices /Server:MyWDSServer /RequestId:ALL
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды утвердить-AutoaddDevices](using-the-approve-autoadddevices-command.md)
[с помощью команды delete-AutoaddDevices](using-the-delete-autoadddevices-command.md) 
 [ С помощью команды get-AutoaddDevices](using-the-get-autoadddevices-command.md)
