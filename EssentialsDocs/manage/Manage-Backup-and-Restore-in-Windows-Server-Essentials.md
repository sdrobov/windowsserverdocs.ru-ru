---
title: "Управление архивацией и восстановлением в Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 41000915-f6ff-4dbb-b7be-629ef36386d4
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 6f6f0d27472664cd1cc538897d3d525fad506282
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="manage-backup-and-restore-in-windows-server-essentials"></a>Управление архивацией и восстановлением в Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
 
 Windows Server Essentials предоставляет надежные способы для выполнения регулярной архивации сервера и сетевых компьютеров. В случае потери данных можно восстановить данные из успешного архива на сервере без восстановления всего компьютера. При необходимости можно выполнить полное восстановление системы на сервере или клиентских компьютеров в сети. В следующей таблице описаны различные варианты архивации для вас и их преимущества.  
  
|Возможность архивации|Описание|Преимущества|  
|--------------------|-----------------|----------------|  
|Резервное копирование сервера|Архивация сервера под управлением Windows Server Essentials. Резервное копирование данных на внешний USB-накопитель.<br /><br /> Дополнительные сведения см. в разделе [Управление архивацией сервера](Manage-Server-Backup-in-Windows-Server-Essentials.md) и [восстановление или исправление сервера](Restore-or-repair-your-server-running-Windows-Server-Essentials.md).|— Позволяет восстановить файлы и папки на сервере.<br /><br /> — Позволяет выполнить полное восстановление системы сервера.|  
|Резервное копирование клиентских компьютеров|Архивация клиентских компьютеров в сети. Резервное копирование данных на сервере под управлением Windows Server Essentials.<br /><br /> Дополнительные сведения см. в разделе [управление Архивация данных клиента](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md) и [полное восстановление системы из существующей резервной копии компьютера клиента](Restore-a-full-system-from-an-existing-client-computer-backup.md).|— Позволяет восстановить файлы и папки с сервера.<br /><br /> — Позволяет выполнить полное восстановление системы клиентского компьютера.|  
| Служба архивации Microsoft Azure|Выполнение оперативной архивации файлов или папок на сервере. При использовании службы архивации Azure для резервного копирования данных сервера информация шифруется с использованием парольной фразы, а затем отправляется в защищенный ЦОД в Интернете.<br /><br /> Дополнительные сведения см. в разделе [управление оперативной архивацией](Manage-Online-Backup-in-Windows-Server-Essentials.md).|— Позволяет восстановить файлы и папки с сервера.<br /><br /> -Пир использовании добавочных архиваций в облако передаются только изменения в файлах.<br /><br /> -Резервное копирование хранятся в Microsoft Azure и являются автономными, что сокращает потребность в защите внутренних архивных носителей.|  
  
## <a name="see-also"></a>См. также:  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)  
  
-   [Использование Windows Server Essentials](../use/Use-Windows-Server-Essentials.md)
