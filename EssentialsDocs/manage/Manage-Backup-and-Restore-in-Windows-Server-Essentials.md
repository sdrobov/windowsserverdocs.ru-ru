---
title: Управление архивацией и восстановлением в Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59828525"
---
# <a name="manage-backup-and-restore-in-windows-server-essentials"></a>Управление архивацией и восстановлением в Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
 
 Windows Server Essentials предоставляет надежные способы для выполнения регулярной архивации сервера и сетевых компьютеров. В случае потери данных можно восстановить данные из успешного архива на сервере без восстановления всего компьютера. При необходимости можно выполнить полное восстановление системы на сервере или клиентских компьютерах в сети. В следующей таблице описаны различные варианты архивации и их преимущества.  
  
|Возможность архивации|Описание|Преимущества|  
|--------------------|-----------------|----------------|  
|Архивация данных сервера|Архивация сервера под управлением Windows Server Essentials. Данные архивируются на внешний USB-накопитель.<br /><br /> Дополнительные сведения см. в разделе [Manage Server Backup](Manage-Server-Backup-in-Windows-Server-Essentials.md) и [восстановления или исправления сервера](Restore-or-repair-your-server-running-Windows-Server-Essentials.md).|— Может восстановить файлы и папки на сервере.<br /><br /> — Может выполнить полное восстановление системы сервера.|  
|Архивация клиентских компьютеров|Архивация клиентских компьютеров в сети. Выполняется архивация данных на сервере, работающем под управлением Windows Server Essentials.<br /><br /> Дополнительные сведения см. в разделе [управление клиента резервного копирования](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md) и [полное восстановление системы из существующей резервной копии компьютера клиента](Restore-a-full-system-from-an-existing-client-computer-backup.md).|— Может восстановить файлы и папки с сервера.<br /><br /> — Может выполнить полное восстановление системы клиентского компьютера.|  
| Служба архивации Microsoft Azure|Выполнение оперативной архивации файлов или папок на сервере. При использовании Azure Backup для резервного копирования данных сервера информация шифруется с помощью парольной фразы перед отправкой в защищенный ЦОД в Интернете.<br /><br /> Дополнительные сведения см. в разделе [управление оперативной архивацией](Manage-Online-Backup-in-Windows-Server-Essentials.md).|— Может восстановить файлы и папки с сервера.<br /><br /> — С добавочное резервное копирование в облако передаются только изменения в файлах.<br /><br /> -Резервные копии хранятся в Microsoft Azure и являются автономными, что снижает потребность в защите внутренних архивных носителей.|  
  
## <a name="see-also"></a>См. также  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)  
  
-   [Использование Windows Server Essentials](../use/Use-Windows-Server-Essentials.md)
