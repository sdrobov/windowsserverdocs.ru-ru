---
title: Фильтрация представления записей ресурсов DNS
description: Этот раздел является частью в руководстве по управления IP Address Management (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b80294a-7325-476b-84eb-69f0d051e8b2
ms.author: pashort
author: shortpatti
ms.openlocfilehash: cc3f2b8ec6e7c5149ef6351639fbbf8f0def8be8
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67283934"
---
# <a name="filter-the-view-of-dns-resource-records"></a>Фильтрация представления записей ресурсов DNS

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе можно использовать для фильтрации представления записей ресурсов DNS в консоли ipam-клиента.  
  
Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  
  
### <a name="to-filter-the-view-of-dns-resource-records"></a>Для фильтрации представления записей ресурсов DNS  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль ipam-клиента.  
  
2.  В области навигации в **НАБЛЮДЕНИЕ и УПРАВЛЕНИЕ**, нажмите кнопку **зон DNS**.  На панели навигации делит на верхней панели навигации и нижней панели навигации.  
  
3.  В нижней области навигации щелкните **прямого просмотра**. Все управляемые IPAM DNS зоны прямого просмотра отображаются в результатах поиска панели отображения.  
  
4.  Щелкните зону, записи которых вы хотите просматривать и фильтровать.  
  
5.  В панели «дисплей» щелкните **текущее представление**, а затем нажмите кнопку **записей ресурсов**. Записи ресурсов для зоны, отображаются на панели отображения.  
  
6.  В панели «дисплей» щелкните **добавить условие**.  
  
    ![Добавить условие](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_01.jpg)  
  
7.  Выберите условие из раскрывающегося списка. Например, если вы хотите просмотреть записей определенного типа, щелкните **тип записи**.  
  
    ![Выберите критерий](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_02.jpg)  
  
8.  Нажмите кнопку **Добавить**.  
  
    ![Добавить критерии](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_03.jpg)  
  
9. **Тип записи** добавляется в качестве параметра поиска. Введите текст для типа записи, которую требуется найти. Например, если вы хотите просмотреть только записи SRV, введите **SRV**.  
  
    ![Укажите тип записи, который требуется найти](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_04.jpg)  
  
10. Нажмите клавишу ВВОД. Записи ресурсов DNS будут отфильтрованы согласно условию и поиск указанную фразу.  
  
    ![Запустить фильтр](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_05.jpg)  
  
## <a name="see-also"></a>См. также  
[Управление записями ресурсов DNS](DNS-Resource-Record-Management.md)  
[Управление IPAM](Manage-IPAM.md)  
  


