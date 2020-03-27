---
title: Фильтрация представления записей ресурсов DNS
description: Этот раздел является частью руководства по управлению IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b80294a-7325-476b-84eb-69f0d051e8b2
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 4e032e2c5b89dc362fceb34e06525d8632f7b19e
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80312405"
---
# <a name="filter-the-view-of-dns-resource-records"></a>Фильтрация представления записей ресурсов DNS

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

С помощью этого раздела можно отфильтровать представление записей ресурсов DNS в консоли клиента IPAM.  
  
Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  
  
### <a name="to-filter-the-view-of-dns-resource-records"></a>Фильтрация представления записей ресурсов DNS  
  
1.  В диспетчер сервера щелкните **IPAM**. Откроется консоль клиента IPAM.  
  
2.  В области навигации в окне **мониторинг и управление**щелкните **зоны DNS**.  Панель навигации разделяется на верхнюю панель навигации и нижнюю панель навигации.  
  
3.  В нижней области навигации щелкните **прямой поиск**. Все зоны прямого просмотра DNS, управляемые IPAM, отображаются в результатах поиска на панели отображения.  
  
4.  Щелкните зону, записи которой нужно просмотреть и отфильтровать.  
  
5.  На панели отображения щелкните **Текущее представление**, а затем щелкните **записи ресурсов**. Записи ресурсов для зоны отображаются на панели отображения.  
  
6.  На панели "Отображение" нажмите кнопку **Добавить условие**.  
  
    ![Добавить условие](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_01.jpg)  
  
7.  Выберите критерий из раскрывающегося списка. Например, если требуется просмотреть конкретный тип записи, щелкните **тип записи**.  
  
    ![Выберите критерий](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_02.jpg)  
  
8.  Нажмите кнопку **Добавить**.  
  
    ![Добавление условий](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_03.jpg)  
  
9. **Тип записи** добавляется в качестве параметра поиска. Введите текст для типа записи, которую необходимо найти. Например, если нужно просмотреть только записи типа SRV, введите **SRV**.  
  
    ![Укажите тип записи, которую необходимо найти](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_04.jpg)  
  
10. Нажмите клавишу ВВОД. Записи ресурсов DNS фильтруются в соответствии с указанными критериями и фразой поиска.  
  
    ![Запуск фильтра](../../media/Filter-the-View-of-DNS-Resource-Records/ipam_FilterRR_05.jpg)  
  
## <a name="see-also"></a>См. также  
[Управление записью ресурса DNS](DNS-Resource-Record-Management.md)  
[Управление IPAM](Manage-IPAM.md)  
  


