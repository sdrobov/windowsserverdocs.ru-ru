---
title: Увеличение объема параллельных Аутентификаций, обрабатываемых NPS
description: В этом разделе содержатся инструкции по настройке параллельных аутентификаций сервера политики сети в Windows Server 2016.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 2d9cdada-0625-41c8-8248-a32259b03e47
ms.author: pashort
author: shortpatti
ms.openlocfilehash: aa70c1a26e2c22d26545e1b46a6151d71a2b4095
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="increase-concurrent-authentications-processed-by-nps"></a>Увеличение объема параллельных Аутентификаций, обрабатываемых NPS

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Инструкции по настройке параллельных аутентификаций сервера политики сети можно использовать в этом разделе.

Если вы установили \(NPS\) сервера политики сети на компьютере, отличном от контроллера домена и NPS-сервер принимает большое количество запросов проверки подлинности в секунду, может повысить производительность сервера политики сети, увеличив количество одновременных проверки подлинности между сервером политики сети и контроллера домена.

Чтобы сделать это, необходимо изменить раздел реестра: 

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters`

Добавьте новый параметр с именем **MaxConcurrentApi** и присвойте ему значение от 2 до 5. 

>[!CAUTION]
>Если присвоить значение **MaxConcurrentApi** слишком большое, NPS-сервер может поместить чрезмерной нагрузки на контроллере домена.

Дополнительные сведения об управлении NPS см. в разделе [управление сервером политики сети](nps-manage-top.md).

Дополнительные сведения о сервере политики сети см. в разделе [сервера политики сети (NPS)](nps-top.md).