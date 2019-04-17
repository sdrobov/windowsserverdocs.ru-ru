---
title: Задание области доступа для записей ресурсов DNS
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
ms.assetid: a96a8752-5678-49c5-b069-d2cce8042a51
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 06c33a633975497e80863cc8d42b14a0f9ac8193
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="set-access-scope-for-dns-resource-records"></a>Задание области доступа для записей ресурсов DNS

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Чтобы задать область доступа для записей ресурсов DNS с помощью консоли клиента IPAM, можно использовать в этом разделе.  
  
Членство в группе **Администраторы**, или в эквивалентной минимальным требованием для выполнения этой процедуры.  
  
### <a name="to-set-access-scope-for-dns-resource-records"></a>Чтобы задать область доступа для записей ресурсов DNS  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль IPAM-клиента.  
  
2.  В области навигации щелкните **зон DNS**.  В нижней области навигации разверните **прямого просмотра** и найдите и выберите зону, которая содержит записи ресурсов, для которого требуется изменить область доступа.  
  
3.  На панели отображения найдите и выберите записи ресурсов, для которого требуется изменить область доступа.  
  
    ![Выберите записи ресурсов](../../media/Set-Access-Scope-for-DNS-Resource-Records/ipam_RestrictUserToRRControl_02.jpg)  
  
4.  Щелкните правой кнопкой мыши выбранные записи ресурсов DNS и нажмите кнопку **задать область доступа**.  
  
    ![Задание области доступа](../../media/Set-Access-Scope-for-DNS-Resource-Records/ipam_RestrictUserToRRControl_03.jpg)  
  
5.  **Задать область доступа** откроется диалоговое окно. Если это необходимо для вашего развертывания, отмените выделение **наследовать область доступа от родительского**. В **выберите область доступа**, выберите элемент и нажмите кнопку **ОК**.  
  
    ![Выберите область доступа](../../media/Set-Access-Scope-for-DNS-Resource-Records/ipam_RestrictUserToRRControl_04.jpg)  
  
## <a name="see-also"></a>См. также:  
[Управление доступом на основе ролей](Role-based-Access-Control.md)  
[Управление IPAM](Manage-IPAM.md)  
  


