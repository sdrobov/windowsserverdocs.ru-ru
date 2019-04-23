---
title: С помощью команды get-AllDevices
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: e5f51bcc2332cced906be1eec3265541ffd2d225
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59886375"
---
# <a name="using-the-get-alldevices-command"></a>С помощью команды get-AllDevices

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает свойства всех подготовленных компьютеров служб развертывания Windows. Предварительно настроенный компьютер является физическим компьютером, была связана с учетной записи компьютера в доменных службах active directory.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-AllDevices [/forest:{Yes | No}] [/ReferralServer:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ леса: {Да &#124; No}]|Указывает, должно ли служб развертывания Windows возвращать компьютеры в лесу или локального домена. Значение по умолчанию — **нет**, это значит, что возвращаются только компьютеры в локальном домене.|
|[/ ReferralServer:<Server name>]|Возвращает только те компьютеры, которые предварительно настроены для указанного сервера.|
## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть все компьютеры, введите одно из следующих:
```
wdsutil /Get-AllDevices
wdsutil /verbose /Get-AllDevices /forest:Yes /ReferralServer:MyWDSServer
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[подкоманда: set-Device](subcommand-set-device.md)
[с помощью команды add Device](using-the-add-device-command.md)
[с помощью get устройства Команда](using-the-get-device-command.md)
