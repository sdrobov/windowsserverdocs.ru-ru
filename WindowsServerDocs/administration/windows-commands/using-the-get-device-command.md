---
title: Использование команды Get-Device
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1da79286-7e1d-45f2-aea2-d446e16a6911
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6451e0a55a72fc88867a3f3be0e1317d881391aa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363204"
---
# <a name="using-the-get-device-command"></a>Использование команды Get-Device

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения о службах развертывания Windows о предварительно подготовленном компьютере (т. е. физическом компьютере, который был подключен к учетной записи компьютера в доменных службах Active Directory).
## <a name="syntax"></a>Синтаксис
```
wdsutil /Get-Device {/Device:<Device name> | /ID:<MAC or UUID>} [/Domain:<Domain>] [/forest:{Yes | No}]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/Девице: <Device name>|Указывает имя компьютера (SAMAccountName).|
|/ID: <MAC or UUID>|Указывает MAC-адрес или UUID (GUID) компьютера, как показано в следующих примерах. Обратите внимание, что допустимый GUID должен быть в одном из двух форматов двоичная строка или строка GUID<br /><br />-   **двоичная строка**:/ID: ACEFA3E81F20694E953EB2DAA1E8B1B6<br />@no__t — 0**MAC-адрес**: 00B056882FDC (без тире) или 00-B0-56-88-2F-DC (с тире)<br />-   **Строка GUID**:/ID: E8A3EFAC-201F-4E69-953-B2DAA1E8B1B6|
|[/Domain: <Domain>]|Указывает домен для поиска предварительно подготовленного компьютера. Значение этого параметра по умолчанию — локальный домен.|
|[/Forest: {Да &#124; нет}]|Указывает, должны ли службы развертывания Windows выполнять поиск по всему лесу или локальному домену. Значение по умолчанию — « **нет**». Это означает, что поиск выполняется только в локальном домене.|
## <a name="BKMK_examples"></a>Примеров
Чтобы получить сведения, используя имя компьютера, введите:
```
wdsutil /Get-Device /Device:computer1
```
Чтобы получить сведения с помощью MAC-адреса, введите:
```
wdsutil /verbose /Get-Device /ID:"00-B0-56-88-2F-DC" /Domain:MyDomain
```
Чтобы получить сведения с помощью строки GUID, введите:
```
wdsutil /verbose /Get-Device /ID:E8A3EFAC-201F-4E69-953-B2DAA1E8B1B6 /forest:Yes
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксическая клавиша командной строки](command-line-syntax-key.md)
[подкоманда: set-Device](subcommand-set-device.md)
[с помощью команды Add-Device](using-the-add-device-command.md)
[с помощью команды Get-аллдевицес](using-the-get-alldevices-command.md) .
