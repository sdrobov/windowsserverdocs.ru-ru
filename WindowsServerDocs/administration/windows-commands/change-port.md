---
title: change port
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d772c90-e849-4e74-b9ec-b6cae1159336 Lizap
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0e587572acd1af1cc7dbd2550e1eae5244d0d1dd
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379605"
---
# <a name="change-port"></a>change port

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

перечисление или изменение сопоставления COM-портов для совместимости с приложениями MS-DOS.
Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).
> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](https://technet.microsoft.com/library/hh831527) в библиотеке TechNet по Windows Server.
> ## <a name="syntax"></a>Синтаксис
> ```
> change port [<PortX>=<PortY> | /d <PortX> | /query]
> ```
> ## <a name="parameters"></a>Параметры
> 
> |    Параметр    |              Описание               |
> |-----------------|----------------------------------------|
> | <PortX>=<PortY> |    Сопоставляет COM-<*порткс*> с <ным >ом*порта*.    |
> |   /d <PortX>    | Удаляет сопоставление для COM-<*порткс*>. |
> |     /Query      |  Отображает текущие сопоставления портов.   |
> |       /?        |  Отображение справки в командной строке.  |
> 
> ## <a name="remarks"></a>Примечания
> - Большинство приложений MS-DOS поддерживают только последовательные порты с COM1 до COM4. Команда **изменить порт** сопоставляет последовательный порт с другим номером порта, что позволяет приложениям, которые не поддерживают порты COM с большим числом номеров, обращаться к последовательному порту. повторное сопоставление работает только для текущего сеанса и не сохраняется при выходе из сеанса и последующем входе в систему.
> - Используйте параметр **порт изменений** без параметров для отображения доступных COM-портов и их текущих сопоставлений.
>   ## <a name="BKMK_examples"></a>Примеров
> - Чтобы преобразовать COM12 в порт COM1 для использования приложением на основе MS-DOS, введите:
>   ```
>   change port com12=com1
>   ```
> - Чтобы отобразить текущие сопоставления портов, введите:
>   ```
>   change port /query
>   ```
>   #### <a name="additional-references"></a>Дополнительные ссылки
>   [Раздел синтаксиса командной строки](command-line-syntax-key.md)
>   [изменение](change.md)
>   [службы удаленных рабочих столов &#40;Справочник по&#41; командам служб терминалов](remote-desktop-services-terminal-services-command-reference.md)
