---
title: Измените порт прослушивания в удаленном рабочем столе
description: Узнайте, как изменить порт прослушивания для клиента удаленного рабочего стола.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
author: lizap
ms.author: elizapo
ms.date: 07/19/2018
ms.localizationpriority: medium
ms.openlocfilehash: 5bf90010143e742f7a0c9b5c262be01e6ccf8c5c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882725"
---
# <a name="change-the-listening-port-for-remote-desktop-on-your-computer"></a>Изменить порт прослушивания для удаленного рабочего стола на компьютере

>Относится к: Windows 10, Windows 8.1, Windows 8, Windows Server 2016, Windows Server 2012 R2, Windows Server 2008 R2

При подключении компьютера (Windows или клиента Windows Server) с помощью клиента удаленного рабочего стола, функции удаленного рабочего стола на компьютере «слышит» запрос на соединение через заданный порт прослушивания (3389 по умолчанию). Этот порт прослушивания на компьютерах Windows можно изменить путем изменения реестра.

1. Запустите редактор реестра. (В поле поиска введите regedit.)
2. Найдите следующий подраздел реестра: HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp\PortNumber
3. Нажмите кнопку **изменить > изменить**, а затем нажмите кнопку **десятичное**.
4. Введите новый номер порта и нажмите кнопку **ОК**. 
5. Закройте редактор реестра и перезагрузите компьютер.

При очередном подключении компьютера к этому компьютеру с помощью подключения удаленного рабочего стола, необходимо ввести новый номер порта. Если вы используете брандмауэр, убедитесь, что в брандмауэре необходимо разрешить подключения к новый номер порта.
