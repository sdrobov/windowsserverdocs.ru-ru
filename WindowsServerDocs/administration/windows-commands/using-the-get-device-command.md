---
title: Get-Device
description: Справочный раздел по Get-Device, который получает сведения о предварительно подготовленном компьютере (т. е. физическом компьютере, который был подключен к учетной записи компьютера в доменных службах Active Directory).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1da79286-7e1d-45f2-aea2-d446e16a6911
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6f89266a2f70523ec332ed7cfb6a976f87a8e4f2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719957"
---
# <a name="get-device"></a>Get-Device

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения о службах развертывания Windows о предварительно подготовленном компьютере (т. е. физическом компьютере, который был подключен к учетной записи компьютера в доменных службах Active Directory).

## <a name="syntax"></a>Синтаксис
```
wdsutil /Get-Device {/Device:<Device name> | /ID:<MAC or UUID>} [/Domain:<Domain>] [/forest:{Yes | No}]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|Модем<Device name>|Указывает имя компьютера (SAMAccountName).|
|Удостоверения<MAC or UUID>|Указывает MAC-адрес или UUID (GUID) компьютера, как показано в следующих примерах. Обратите внимание, что допустимый GUID должен быть в одном из двух форматов двоичная строка или строка GUID<p>-   **Двоичная строка**:/ID: ACEFA3E81F20694E953EB2DAA1E8B1B6<br />-   **MAC-адрес**: 00B056882FDC (без дефисов) или 00-B0-56-88-2F-DC (с тире)<br />-   **Строка GUID**:/ID: E8A3EFAC-201F-4E69-953-B2DAA1E8B1B6|
|[/Domain:<Domain>]|Указывает домен для поиска предварительно подготовленного компьютера. Значение этого параметра по умолчанию — локальный домен.|
|[/Forest: {Да &#124; No}]|Указывает, должны ли службы развертывания Windows выполнять поиск по всему лесу или локальному домену. Значение по умолчанию — « **нет**». Это означает, что поиск выполняется только в локальном домене.|
## <a name="examples"></a>Примеры
Чтобы получить сведения, используя имя компьютера, введите:
```
wdsutil /Get-Device /Device:computer1
```
Чтобы получить сведения с помощью MAC-адреса, введите:
```
wdsutil /verbose /Get-Device /ID:00-B0-56-88-2F-DC /Domain:MyDomain
```
Чтобы получить сведения с помощью строки GUID, введите:
```
wdsutil /verbose /Get-Device /ID:E8A3EFAC-201F-4E69-953-B2DAA1E8B1B6 /forest:Yes
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Command-Line Syntax Key](command-line-syntax-key.md)
Подкоманда для синтаксиса командной строки[: Set-Device](subcommand-set-device.md)

[с помощью команды Add-Device](using-the-add-device-command.md)[с помощью команды Get-аллдевицес](using-the-get-alldevices-command.md) .
