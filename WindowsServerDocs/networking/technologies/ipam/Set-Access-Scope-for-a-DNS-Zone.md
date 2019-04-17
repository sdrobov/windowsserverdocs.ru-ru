---
title: Задание области доступа для зоны DNS
description: Этот раздел входит руководство по управлению управления IP-адресами (IPAM) в Windows Server 2016.
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
ms.openlocfilehash: a4e84f249e57df6bfd04203c8b825ff5d4d643b2
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="set-access-scope-for-a-dns-zone"></a>Задание области доступа для зоны DNS

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Чтобы задать область доступа для зоны DNS с помощью консоли клиента IPAM, можно использовать в этом разделе.  
  
Членство в группе **Администраторы**, или в эквивалентной минимальным требованием для выполнения этой процедуры.  
  
### <a name="to-set-the-access-scope-for-a-dns-zone"></a>Чтобы задать область доступа для зоны DNS  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль IPAM-клиента.  
  
2.  В области навигации щелкните **зон DNS**. На панели отображения щелкните правой кнопкой мыши зону DNS, для которого вы хотите изменить область доступа., а затем нажмите кнопку **задать область доступа**.  
  
    ![Задание области доступа](../../media/Set-Access-Scope-for-a-DNS-Zone/ipam_SetAccessScopeOfZone_02.jpg)  
  
3.  **Задать область доступа** откроется диалоговое окно. Если это необходимо для вашего развертывания, отмените выделение **наследовать область доступа от родительского**. В **выберите область доступа**, выберите элемент и нажмите кнопку **ОК**.  
  
    ![Выберите область доступа](../../media/Set-Access-Scope-for-a-DNS-Zone/ipam_SetAccessScopeOfZone_03.jpg)  
  
4.  На панели отображения консоли клиента IPAM убедитесь, что был изменен с областью доступа для зоны.  
  
    ![Убедитесь, что был изменен с областью доступа для зоны](../../media/Set-Access-Scope-for-a-DNS-Zone/ipam_SetAccessScopeOfZone_04.jpg)  
  
## <a name="see-also"></a>См. также:  
[Управление доступом на основе ролей](Role-based-Access-Control.md)  
[Управление IPAM](Manage-IPAM.md)  
  


