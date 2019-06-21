---
title: Задание области доступа для записей ресурсов DNS
description: Этот раздел является частью в руководстве по управления IP Address Management (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a96a8752-5678-49c5-b069-d2cce8042a51
ms.author: pashort
author: shortpatti
ms.openlocfilehash: c79e1f63b9bcb43520a57defca8228b76db68a31
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67283868"
---
# <a name="set-access-scope-for-dns-resource-records"></a>Задание области доступа для записей ресурсов DNS

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Чтобы задать область доступа для записи ресурсов DNS с помощью консоли клиента IPAM, можно использовать в этом разделе.  
  
Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  
  
### <a name="to-set-access-scope-for-dns-resource-records"></a>Чтобы задать область доступа для записи ресурсов DNS  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль ipam-клиента.  
  
2.  В области навигации щелкните **зон DNS**.  В нижней области навигации разверните **прямого просмотра** и найдите и выберите области, содержащей записи ресурсов, области доступа, вы хотите изменить.  
  
3.  В панели «дисплей» найдите и выберите область доступа, которого вы хотите изменить записи ресурсов.  
  
    ![Выберите записи ресурсов](../../media/Set-Access-Scope-for-DNS-Resource-Records/ipam_RestrictUserToRRControl_02.jpg)  
  
4.  Щелкните правой кнопкой мыши выбранные записи ресурсов DNS, а затем нажмите кнопку **задание области доступа**.  
  
    ![Задание области доступа](../../media/Set-Access-Scope-for-DNS-Resource-Records/ipam_RestrictUserToRRControl_03.jpg)  
  
5.  **Задание области доступа** откроется диалоговое окно. Если это необходимо для развертывания, щелкните, чтобы отменить выбор **наследовать область доступа от родительского элемента**. В **выберите область доступа**, выберите элемент и нажмите кнопку **ОК**.  
  
    ![Выбор области доступа](../../media/Set-Access-Scope-for-DNS-Resource-Records/ipam_RestrictUserToRRControl_04.jpg)  
  
## <a name="see-also"></a>См. также  
[Управление доступом на основе ролей](Role-based-Access-Control.md)  
[Управление IPAM](Manage-IPAM.md)  
  


