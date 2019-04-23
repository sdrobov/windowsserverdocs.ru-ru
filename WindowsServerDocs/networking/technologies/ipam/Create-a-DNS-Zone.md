---
title: Создание зоны DNS
description: Этот раздел является частью в руководстве по управления IP Address Management (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a030ff51-a815-4fc4-b26d-aae41c3e4ce5
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 31dbae80882e1375e548d5f6942c6473786f838f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59870225"
---
# <a name="create-a-dns-zone"></a>Создание зоны DNS

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе можно использовать для создания зоны DNS с помощью консоли ipam-клиента.  
  
Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  
  
### <a name="to-create-a-dns-zone"></a>Чтобы создать зону DNS  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль ipam-клиента.  
  
2.  В области навигации в **НАБЛЮДЕНИЕ и УПРАВЛЕНИЕ**, нажмите кнопку **DNS и DHCP-серверы**. В панели «дисплей» щелкните **тип сервера**, а затем нажмите кнопку **DNS**. Все DNS-серверы под управлением IPAM, перечислены в результатах поиска.  
  
3.  Найдите нужный сервер, где вы хотите добавить в зону и щелкните правой кнопкой мыши сервер.  Нажмите кнопку **создание зоны DNS**.  
  
    ![Создание зоны DNS](../../media/Create-a-DNS-Zone/ipam_CreateDNSZone_01a.jpg)  
  
4.  **Создайте зону DNS** откроется диалоговое окно. В **общие свойства**, выберите категорию зоны, тип зоны и введите имя в **имя зоны**. Также выберите значения, соответствующие вашему развертыванию в **дополнительные свойства**, а затем нажмите кнопку **ОК**.  
  
    ![Дополнительные свойства](../../media/Create-a-DNS-Zone/ipam_CreateDNSZone_02a.jpg)  
  
## <a name="see-also"></a>См. также  
[Управление зонами DNS](DNS-Zone-Management.md)  
[Управление IPAM](Manage-IPAM.md)  
  


