---
title: Изменение порта прослушивания в удаленном рабочем столе
description: Узнайте, как изменить порт прослушивания для клиента удаленного рабочего стола.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
author: lizap
ms.author: elizapo
ms.date: 07/19/2018
ms.localizationpriority: medium
ms.openlocfilehash: b6b5a48435a99b1bf1392acb6a5764b106984bbe
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404190"
---
# <a name="change-the-listening-port-for-remote-desktop-on-your-computer"></a>Изменение порта прослушивания для удаленного рабочего стола на компьютере

>Относится к: Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2008 R2

При подключении компьютера (клиентской версии Windows или Windows Server) с помощью клиента удаленного рабочего стола функции удаленного рабочего стола на компьютере "слышат" запрос на соединение через заданный порт прослушивания (по умолчанию — 3389). Этот порт прослушивания на компьютерах Windows можно изменить путем изменения реестра.

1. Откройте редактор реестра. (В поле поиска введите "regedit").
2. Перейдите к следующему разделу реестра: HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp\PortNumber
3. Нажмите кнопку **Редактировать > Изменить**, а затем выберите пункт **Десятичное**.
4. Введите новый номер порта, а затем нажмите кнопку **ОК**. 
5. Закройте редактор реестра и перезагрузите компьютер.

При очередном подключении компьютера к этому компьютеру с помощью удаленного рабочего стола необходимо будет ввести новый номер порта. Если вы используете брандмауэр, убедитесь, что в нем разрешены подключения к новому номеру порта.
