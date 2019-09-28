---
title: Использование команды Get-Аллмултикасттрансмиссионс
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95b8fb79-7a8a-4f0c-88f4-92bc1111c67f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 644684ffb356ef07120bc391e3d3da2daf768eaf
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363345"
---
# <a name="using-the-get-allmulticasttransmissions-command"></a>Использование команды Get-Аллмултикасттрансмиссионс

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
## <a name="parameters"></a>Параметры

|        Параметр        |                                                                                                                                                                                                                                                                   Объяснение                                                                                                                                                                                                                                                                    |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server: <Server name>] |                                                                                                                                                                                 Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.                                                                                                                                                                                  |
|         /Show         | **Windows Server 2008**<br /><br />/Show: Clients — отображает сведения о клиентских компьютерах, подключенных к многоадресным передачам.<br /><br />**Windows Server 2008 R2**<br /><br />Показывать: {установить &#124; &#124; все для загрузки} — тип возвращаемого образа.                                Функция **загрузки** возвращает только передачи загрузочных образов.                                  **Установка** возвращает только передачи образов. **ALL** возвращает оба типа изображений. |
|                         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|    /детаилс: клиенты     |                                                                                                                                                                                              Поддерживается только для Windows Server 2008 R2. При наличии клиенты, подключенные к передаче, будут отображаться.                                                                                                                                                                                               |
| [/Ексклудеделетепендинг] |                                                                                                                                                                                                                                              Исключает из списка все деактивированные передачи.                                                                                                                                                                                                                                               |

## <a name="BKMK_examples"></a>Примеров
Чтобы просмотреть сведения обо всех передачах, введите:
- Windows Server 2008: `wdsutil /Get-AllMulticastTransmissions`
- Windows Server 2008 R2: `wdsutil /Get-AllMulticastTransmissions /Show:All` чтобы просмотреть сведения обо всех передачах, за исключением неактивированных передач, введите:
- Windows Server 2008: `wdsutil /Get-AllMulticastTransmissions /Server:MyWDSServer /Show:Clients /ExcludedeletePending`
- Windows Server 2008 R2: `wdsutil /Get-AllMulticastTransmissions /Server:MyWDSServer /Show:All /details:Clients /ExcludedeletePending`
  #### <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [с помощью команды get-мултикасттрансмиссион](using-the-get-multicasttransmission-command.md)
  [с помощью команды New-Мултикасттрансмиссион](using-the-new-multicasttransmission-command.md)
  [с помощью команды Remove-мултикасттрансмиссион](using-the-remove-multicasttransmission-command.md)
  [ . Подкоманда: Start-Мултикасттрансмиссион](subcommand-start-multicasttransmission.md)
