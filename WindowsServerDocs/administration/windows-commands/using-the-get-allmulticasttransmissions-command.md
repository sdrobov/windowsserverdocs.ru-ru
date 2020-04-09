---
title: Get-Аллмултикасттрансмиссионс
description: Раздел команд Windows для Get-Аллмултикасттрансмиссионс, в котором отображаются сведения обо всех многоадресных передачах на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 95b8fb79-7a8a-4f0c-88f4-92bc1111c67f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c81db5a5d5ebb9bcc5e2d00165d5c944c687fd97
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831336"
---
# <a name="get-allmulticasttransmissions"></a>Get-Аллмултикасттрансмиссионс

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения обо всех многоадресных передачах на сервере.

## <a name="syntax"></a>Синтаксис
для Windows Server 2008:
```
wdsutil /Get-AllMulticastTransmissions [/Server:<Server name>] [/Show:Clients] [/ExcludedeletePending]
```
для Windows Server 2008 R2:
```
wdsutil /Get-AllMulticastTransmissions [/Server:<Server name>] [/Show:{Boot | Install | All}] [/details:Clients]  [/ExcludedeletePending]
```
### <a name="parameters"></a>Параметры

|        Параметр        |                                                                                                                                                                                                                                                                   Пояснение                                                                                                                                                                                                                                                                    |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server:<Server name>] |                                                                                                                                                                                 Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.                                                                                                                                                                                  |
|         /Show         | **Windows Server 2008**<p>/Show: Clients — отображает сведения о клиентских компьютерах, подключенных к многоадресным передачам.<p>**Windows Server 2008 R2**<p>Показывать: {установить &#124; &#124; все для загрузки} — тип возвращаемого образа.                                Функция **загрузки** возвращает только передачи загрузочных образов.                                  **Установка** возвращает только передачи образов. **ALL** возвращает оба типа изображений. |
|                         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|    /детаилс: клиенты     |                                                                                                                                                                                              Поддерживается только для Windows Server 2008 R2. При наличии клиенты, подключенные к передаче, будут отображаться.                                                                                                                                                                                               |
| [/Ексклудеделетепендинг] |                                                                                                                                                                                                                                              Исключает из списка все деактивированные передачи.                                                                                                                                                                                                                                               |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы просмотреть сведения обо всех передачах, введите:
- Windows Server 2008: `wdsutil /Get-AllMulticastTransmissions`
- Windows Server 2008 R2: `wdsutil /Get-AllMulticastTransmissions /Show:All` чтобы просмотреть сведения обо всех передачах, за исключением неактивированных передач, введите:
- Windows Server 2008: `wdsutil /Get-AllMulticastTransmissions /Server:MyWDSServer /Show:Clients /ExcludedeletePending`
- Windows Server 2008 R2: `wdsutil /Get-AllMulticastTransmissions /Server:MyWDSServer /Show:All /details:Clients /ExcludedeletePending`
  ## <a name="additional-references"></a>Дополнительные материалы
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [с помощью команды Get-Мултикасттрансмиссион](using-the-get-multicasttransmission-command.md) ,
  [помощью команды New-мултикасттрансмиссион](using-the-new-multicasttransmission-command.md) ,
  [с помощью команды Remove-мултикасттрансмиссион,](using-the-remove-multicasttransmission-command.md)
  [подкоманде: Start-мултикасттрансмиссион](subcommand-start-multicasttransmission.md)
