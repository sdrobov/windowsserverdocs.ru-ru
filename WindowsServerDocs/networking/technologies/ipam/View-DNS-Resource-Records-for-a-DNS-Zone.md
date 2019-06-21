---
title: Просмотр записей ресурсов DNS для зоны DNS
description: Этот раздел является частью в руководстве по управления IP Address Management (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 375feefc-949e-47c3-9e61-35b79e021966
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 44db34199257367e98279ccbcbc2d5041ee9884c
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67283806"
---
# <a name="view-dns-resource-records-for-a-dns-zone"></a>Просмотр записей ресурсов DNS для зоны DNS

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе можно использовать для просмотра записей ресурсов DNS для зоны DNS в консоли ipam-клиента.  
  
Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  
  
### <a name="to-view-dns-resource-records-for-a-zone"></a>Чтобы просмотреть записи ресурсов DNS для зоны  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль ipam-клиента.  
  
2.  В области навигации в **НАБЛЮДЕНИЕ и УПРАВЛЕНИЕ**, нажмите кнопку **зон DNS**.  На панели навигации делит на верхней панели навигации и нижней панели навигации.  
  
3.  В нижней области навигации щелкните **прямого просмотра**, а затем разверните домены и зоны список и найдите и выберите зону для просмотра. Например, если у вас есть зону с именем Дублин, щелкните **dublin**.  
  
    ![Выберите зону, которую вы хотите просмотреть](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_DNSzones_01a.jpg)  

  
4.  На панели отображения представления по умолчанию является DNS-серверов для зоны. Чтобы изменить представление, щелкните **текущее представление**, а затем нажмите кнопку **записей ресурсов**.  
  
    ![Изменить представление записей ресурсов](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_Zone_RR_02.jpg)  
  
5.  Отображаются записи ресурсов DNS для зоны. Чтобы отфильтровать записи, введите текст, который необходимо найти в **фильтра**.  
  
    ![Введите текст для фильтрации записей](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_DNSzones_01c.jpg)  
  
6.  Для фильтрации записей ресурсов, тип записи, области доступа или другие критерии, нажмите кнопку **добавить условие**, укажите необходимые элементы в списке условий и нажмите кнопку **добавить**.  
  
    ![Использовать критерии для фильтрации записей](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_DNSzones_01d.jpg)  
  
## <a name="see-also"></a>См. также  
[Управление зонами DNS](DNS-Zone-Management.md)  
[Управление IPAM](Manage-IPAM.md)  
  


