---
title: Использование команды Get-Аллдевицес
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5824b3d2-2df1-4ed6-a289-e6c47c13fea2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5b7d2ce709c7e3fbaf7ab4f0e49be14c98ba1cd9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401973"
---
# <a name="using-the-get-alldevices-command"></a>Использование команды Get-Аллдевицес

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает свойства служб развертывания Windows для всех предварительно подготовленных компьютеров. Предварительно подготовленный компьютер — это физический компьютер, связанный с учетной записью компьютера в доменных службах Active Directory.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-AllDevices [/forest:{Yes | No}] [/ReferralServer:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Forest: {Да &#124; нет}]|Указывает, должны ли службы развертывания Windows возвращать компьютеры во всем лесу или в локальном домене. Значение по умолчанию — « **нет**». Это означает, что возвращаются только компьютеры в локальном домене.|
|[/Реферралсервер: <Server name>]|Возвращает только те компьютеры, которые предварительно подготовлены для указанного сервера.|
## <a name="BKMK_examples"></a>Примеров
Чтобы просмотреть все компьютеры, введите одно из следующих действий:
```
wdsutil /Get-AllDevices
wdsutil /verbose /Get-AllDevices /forest:Yes /ReferralServer:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксическая клавиша командной строки](command-line-syntax-key.md)
[подкоманда: set-Device](subcommand-set-device.md)
[с помощью команды Add-](using-the-add-device-command.md)Device 
[с помощью команды Get-Device](using-the-get-device-command.md) .
