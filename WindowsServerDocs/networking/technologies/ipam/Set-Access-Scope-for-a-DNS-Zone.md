---
title: Задание области доступа для зоны DNS
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
ms.assetid: 6a211dde-80eb-4888-b5bb-4e28fe8dc7df
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 73d96a9be7c13afbe4c96d46fffefc0096046c8c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813985"
---
# <a name="set-access-scope-for-a-dns-zone"></a>Задание области доступа для зоны DNS

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Чтобы задать область доступа для зоны DNS с помощью консоли клиента IPAM, можно использовать в этом разделе.  
  
Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  
  
### <a name="to-set-the-access-scope-for-a-dns-zone"></a>Чтобы задать область доступа для зоны DNS  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль ipam-клиента.  
  
2.  В области навигации щелкните **зон DNS**. В панели «дисплей» щелкните правой кнопкой мыши зону DNS, для которого вы хотите изменить область действия доступа. и нажмите кнопку **задание области доступа**.  
  
    ![Задание области доступа](../../media/Set-Access-Scope-for-a-DNS-Zone/ipam_SetAccessScopeOfZone_02.jpg)  
  
3.  **Задание области доступа** откроется диалоговое окно. Если это необходимо для развертывания, щелкните, чтобы отменить выбор **наследовать область доступа от родительского элемента**. В **выберите область доступа**, выберите элемент и нажмите кнопку **ОК**.  
  
    ![Выбор области доступа](../../media/Set-Access-Scope-for-a-DNS-Zone/ipam_SetAccessScopeOfZone_03.jpg)  
  
4.  В панели отображения консоли клиента IPAM убедитесь, что изменен область доступа для зоны.  
  
    ![Убедитесь, что область доступа для зоны изменен](../../media/Set-Access-Scope-for-a-DNS-Zone/ipam_SetAccessScopeOfZone_04.jpg)  
  
## <a name="see-also"></a>См. также  
[Управление доступом на основе ролей](Role-based-Access-Control.md)  
[Управление IPAM](Manage-IPAM.md)  
  


