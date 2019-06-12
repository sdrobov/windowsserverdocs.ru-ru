---
title: С помощью команды get-AllMulticastTransmissions
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: b05f8802a288d80960cf79356675cb9adce9c260
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440533"
---
# <a name="using-the-get-allmulticasttransmissions-command"></a>С помощью команды get-AllMulticastTransmissions

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о всех многоадресных передач на сервере.
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
| [/ Server:<Server name>] |                                                                                                                                                                                 Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.                                                                                                                                                                                  |
|         [/ Show]         | **Windows Server 2008**<br /><br />/Show:clients - Отображает сведения о клиентских компьютерах, подключенных к многоадресные передачи.<br /><br />**Windows Server 2008 R2**<br /><br />Демонстрация: {загрузки &#124; установить &#124; все}-тип возвращаемого изображения.                                **Загрузки** возвращает загружена только передачи образа.                                  **Установка** возвращает только установить передачи образа. **Все** возвращает оба типы изображений. |
|                         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|    /Details:Clients     |                                                                                                                                                                                              Поддерживается только для Windows Server 2008 R2. При его наличии, будет отображаться клиентов, подключенных к передаче.                                                                                                                                                                                               |
| [/ExcludedeletePending] |                                                                                                                                                                                                                                              Исключает все деактивированные передачи данных из списка.                                                                                                                                                                                                                                               |

## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть сведения о всех передач, введите:
- Windows Server 2008: `wdsutil /Get-AllMulticastTransmissions`
- Windows Server 2008 R2: `wdsutil /Get-AllMulticastTransmissions /Show:All` Чтобы просмотреть сведения о всех передач, за исключением отключенных передач, введите:
- Windows Server 2008: `wdsutil /Get-AllMulticastTransmissions /Server:MyWDSServer /Show:Clients /ExcludedeletePending`
- Windows Server 2008 R2: `wdsutil /Get-AllMulticastTransmissions /Server:MyWDSServer /Show:All /details:Clients /ExcludedeletePending`
  #### <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса команд](command-line-syntax-key.md)
  [с помощью команды get-MulticastTransmission](using-the-get-multicasttransmission-command.md)
  [с помощью команды новый MulticastTransmission](using-the-new-multicasttransmission-command.md) 
   [С помощью команды remove-MulticastTransmission](using-the-remove-multicasttransmission-command.md)
  [подкоманда: start-MulticastTransmission](subcommand-start-multicasttransmission.md)
