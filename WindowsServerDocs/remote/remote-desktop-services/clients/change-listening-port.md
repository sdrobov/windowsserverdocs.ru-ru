---
title: Изменение ожидающего порта в удаленного рабочего стола
description: Узнайте, как изменение ожидающего порта для клиента удаленного рабочего стола.
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
ms.openlocfilehash: b70479b644f4984c93136d6493483c372703244d
ms.sourcegitcommit: d3f73936160505a40633ad8dd5931ac5fe3eccdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9297324"
---
# Изменение ожидающего порта для удаленного рабочего стола на компьютере

>Область применения: Windows 10, Windows 8.1, Windows 8, Windows Server 2019 г., Windows Server 2016, Windows Server 2012 R2, Windows Server 2008 R2

При подключении к компьютеру (клиент Windows или Windows Server) через клиент удаленного рабочего стола, функцию удаленного рабочего стола на компьютере «так же будет слышать «запрос подключения через определенный порт прослушивания (3389 по умолчанию). Можно изменить, ожидающего порта на компьютерах Windows путем изменения реестра.

1. Запустите редактор реестра. (В поле поиска введите команду regedit.)
2. Перейдите в следующий раздел реестра: HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp\PortNumber
3. Нажмите кнопку **Изменить > изменить**и нажмите кнопку **десятичных**.
4. Введите новый номер порта и нажмите кнопку **ОК**. 
5. Закройте редактор реестра и перезагрузите компьютер.

Следующий раз, когда при подключении к этому компьютеру с помощью подключения удаленного рабочего стола, необходимо ввести новый порт. Если вы используете брандмауэр, убедитесь, что настройка брандмауэра для разрешения подключений на новый номер порта.
