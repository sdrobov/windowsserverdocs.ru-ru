---
title: С помощью команды get устройства
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 117720c5102da5713c1b0bb5e59cbcc099f3aa8c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59871035"
---
# <a name="using-the-get-device-command"></a>С помощью команды get устройства

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает служб развертывания Windows сведения о предварительно настроенного компьютера (т. е физический компьютер, который были, готового к учетной записи компьютера в доменных службах active directory.
## <a name="syntax"></a>Синтаксис
```
wdsutil /Get-Device {/Device:<Device name> | /ID:<MAC or UUID>} [/Domain:<Domain>] [/forest:{Yes | No}]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ Устройство:<Device name>|Указывает имя компьютера (SAMAccountName).|
|/ ID:<MAC or UUID>|Задает MAC-адрес или идентификатор UUID (GUID) компьютера, как показано в следующих примерах. Обратите внимание, что в одном из двух форматов двоичная строка или строка идентификатора GUID должен быть допустимым идентификатором GUID<br /><br />-   **Двоичная строка**: /ID:ACEFA3E81F20694E953EB2DAA1E8B1B6<br />-   **MAC-адрес**: 00B056882FDC (без дефисов) или 00-B0-56-88-2F-DC (с дефисами)<br />-   **Строка идентификатора GUID**: /ID:E8A3EFAC-201F-4E69-953-B2DAA1E8B1B6|
|[/ Домена:<Domain>]|Указывает домен, для поиска предварительно настроенного компьютера. Значение по умолчанию для этого параметра является локальным доменом.|
|[/ леса: {Да &#124; No}]|Указывает, должен ли поиск служб развертывания Windows, всего леса или локального домена. Значение по умолчанию — **нет**, это означает, что поиск будет осуществляться только локальный домен.|
## <a name="BKMK_examples"></a>Примеры
Чтобы получить сведения, используя имя компьютера, введите следующую команду:
```
wdsutil /Get-Device /Device:computer1
```
Чтобы получить сведения с помощью MAC-адрес, введите следующую команду:
```
wdsutil /verbose /Get-Device /ID:"00-B0-56-88-2F-DC" /Domain:MyDomain
```
Чтобы получить сведения, используя строку идентификатора GUID, введите следующую команду:
```
wdsutil /verbose /Get-Device /ID:E8A3EFAC-201F-4E69-953-B2DAA1E8B1B6 /forest:Yes
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[подкоманда: set-Device](subcommand-set-device.md)
[с помощью команды add Device](using-the-add-device-command.md)
[Using Команда Get-AllDevices](using-the-get-alldevices-command.md)
