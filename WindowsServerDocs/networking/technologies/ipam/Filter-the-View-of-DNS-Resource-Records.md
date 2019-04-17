---
title: Фильтрация представления записей ресурсов DNS
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
ms.assetid: 5b80294a-7325-476b-84eb-69f0d051e8b2
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 35c0e822daa9f2c8c49ae7e6f2f40ec0411cb6fa
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="filter-the-view-of-dns-resource-records"></a>Фильтрация представления записей ресурсов DNS

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать для фильтрации представления записей ресурсов DNS в консоли IPAM-клиента.  
  
Членство в группе **Администраторы**, или в эквивалентной минимальным требованием для выполнения этой процедуры.  
  
### <a name="to-filter-the-view-of-dns-resource-records"></a>Фильтрация представления записей ресурсов DNS  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль IPAM-клиента.  
  
2.  В области навигации в **НАБЛЮДЕНИЕ и УПРАВЛЕНИЕ**, нажмите кнопку **зон DNS**.  На панели навигации разделяет на верхней панели навигации и нижней панели навигации.  
  
3.  В нижней области навигации щелкните **прямого просмотра**. Все управляемые IPAM DNS зоны прямого просмотра отображаются в результатах поиска панели отображения.  
  
4.  Щелкните зону для просмотра и фильтра записи.  
  
5.  В панели «дисплей» выберите **текущее представление**, а затем нажмите кнопку **записей ресурсов**. Записи ресурсов в зоне отображаются на панели отображения.  
  
6.  В панели «дисплей» выберите **добавить условие**.  
  
    ![Добавить условие](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_01.jpg)  
  
7.  Выберите условие из раскрывающегося списка. Например, если вы хотите просмотреть конкретного типа записи, нажмите кнопку **тип записи**.  
  
    ![Критерии выбора](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_02.jpg)  
  
8.  Нажмите кнопку **добавить**.  
  
    ![Добавление условия](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_03.jpg)  
  
9. **Тип записи** добавляется как параметр поиска. Введите текст для типа записи, который требуется найти. Например, если вы хотите просмотреть только записи SRV, введите **SRV**.  
  
    ![Укажите тип записи, чтобы найти](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_04.jpg)  
  
10. Нажмите клавишу ВВОД. Записи ресурсов DNS, фильтруются в соответствии с критериями и поиска фразу, которые вы указали.  
  
    ![Запустите фильтр](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_05.jpg)  
  
## <a name="see-also"></a>См. также:  
[Управление записями ресурсов DNS](DNS-Resource-Record-Management.md)  
[Управление IPAM](Manage-IPAM.md)  
  


