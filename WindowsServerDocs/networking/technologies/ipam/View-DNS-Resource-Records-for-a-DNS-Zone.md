---
title: Просмотр записей ресурсов DNS для зоны DNS
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
ms.assetid: 375feefc-949e-47c3-9e61-35b79e021966
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 786c1ee8fd673bd17465ab9586dd1e0bcfd7971c
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="view-dns-resource-records-for-a-dns-zone"></a>Просмотр записей ресурсов DNS для зоны DNS

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать для просмотра записей ресурсов DNS для зоны DNS в консоли IPAM-клиента.  
  
Членство в группе **Администраторы**, или в эквивалентной минимальным требованием для выполнения этой процедуры.  
  
### <a name="to-view-dns-resource-records-for-a-zone"></a>Чтобы просмотреть записи ресурсов DNS для зоны  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль IPAM-клиента.  
  
2.  В области навигации в **НАБЛЮДЕНИЕ и УПРАВЛЕНИЕ**, нажмите кнопку **зон DNS**.  На панели навигации разделяет на верхней панели навигации и нижней панели навигации.  
  
3.  В нижней области навигации щелкните **прямого просмотра**, а затем разверните домен и зоны список для поиска и выберите зону, которую требуется просмотреть. Например, если зона, имя dublin, щелкните **dublin**.  
  
    ![Выберите зону, которую вы хотите просмотреть](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_DNSzones_01a.jpg)  

  
4.  На панели отображения представления по умолчанию является DNS-серверов для зоны. Чтобы изменить представление, нажмите кнопку **текущее представление**, а затем нажмите кнопку **записей ресурсов**.  
  
    ![Изменить представление для записей ресурсов](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_Zone_RR_02.jpg)  
  
5.  Отображаются записи ресурсов DNS для зоны. Для фильтрации записей, введите текст, который требуется найти в **фильтр**.  
  
    ![Введите текст для фильтра записи](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_DNSzones_01c.jpg)  
  
6.  Для фильтрации записей ресурсов, тип записи, области доступа или других критериев, выберите **добавить условие**, сделайте выбор из списка условий и щелкните **добавить**.  
  
    ![Использование условий для фильтрации записей](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_DNSzones_01d.jpg)  
  
## <a name="see-also"></a>См. также:  
[Управление зоной DNS](DNS-Zone-Management.md)  
[Управление IPAM](Manage-IPAM.md)  
  


