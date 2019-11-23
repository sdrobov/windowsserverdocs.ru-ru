---
title: Увеличение объема параллельных аутентификаций, обрабатываемых NPS
description: В этом разделе приводятся инструкции по настройке параллельной проверки подлинности сервера политики сети в Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 2d9cdada-0625-41c8-8248-a32259b03e47
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 31dec30ba3c843b78974daa7a1e4ed6893b1ebbd
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396427"
---
# <a name="increase-concurrent-authentications-processed-by-nps"></a>Увеличение объема параллельных аутентификаций, обрабатываемых NPS

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

С помощью этого раздела можно получить инструкции по настройке параллельной проверки подлинности сервера политики сети.

Если сервер политики сети \(\) NPS на компьютере, отличном от контроллера домена, и сервер политики сети получает большое количество запросов на проверку подлинности в секунду, можно повысить производительность сервера политики сети, увеличив число одновременных проверок подлинности между сервером политики сети и контроллером домена.

Для этого необходимо изменить следующий раздел реестра: 

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters`

Добавьте новое значение с именем **MaxConcurrentApi** и присвойте ему значение от 2 до 5. 

>[!CAUTION]
>Если присвоить слишком большое значение **MaxConcurrentApi** , сервер NPS может нагрузить чрезмерную нагрузку на контроллер домена.

Дополнительные сведения об управлении NPS см. в разделе [Управление сервером политики сети](nps-manage-top.md).

Дополнительные сведения о NPS см. в разделе [сервер политики сети (NPS)](nps-top.md).