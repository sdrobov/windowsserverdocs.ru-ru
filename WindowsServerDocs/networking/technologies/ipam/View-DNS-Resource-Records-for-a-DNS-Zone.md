---
title: Просмотр записей ресурсов DNS для зоны DNS
description: Этот раздел является частью руководства по управлению IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 375feefc-949e-47c3-9e61-35b79e021966
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 6e4b5ecd87e4976c0c65403bd63180e1d659e40b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405634"
---
# <a name="view-dns-resource-records-for-a-dns-zone"></a>Просмотр записей ресурсов DNS для зоны DNS

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

Этот раздел можно использовать для просмотра записей ресурсов DNS для зоны DNS в консоли клиента IPAM.  
  
Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  
  
### <a name="to-view-dns-resource-records-for-a-zone"></a>Просмотр записей ресурсов DNS для зоны  
  
1.  В диспетчер сервера щелкните **IPAM**. Откроется консоль клиента IPAM.  
  
2.  В области навигации в окне **мониторинг и управление**щелкните **зоны DNS**.  Панель навигации разделяется на верхнюю панель навигации и нижнюю панель навигации.  
  
3.  В нижней области навигации щелкните **прямой поиск**, а затем разверните список домены и зона, чтобы найти и выбрать зону, которую нужно просмотреть. Например, если имеется зона с именем Dublin, щелкните элемент **Dublin**.  
  
    ![Выберите зону, которую нужно просмотреть](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_DNSzones_01a.jpg)  

  
4.  В области отображения представлением по умолчанию являются DNS-серверы для зоны. Чтобы изменить представление, щелкните **Текущее представление**, а затем — **записи ресурсов**.  
  
    ![Изменение представления на записи ресурсов](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_Zone_RR_02.jpg)  
  
5.  Отобразятся записи ресурсов DNS для зоны. Чтобы отфильтровать записи, введите текст, который нужно найти в поле **Фильтр**.  
  
    ![Введите текст для фильтрации записей](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_DNSzones_01c.jpg)  
  
6.  Чтобы отфильтровать записи ресурсов по типу записи, области доступа или другим критериям, нажмите кнопку **Добавить условие**, а затем выберите в списке критерий и нажмите кнопку **Добавить**.  
  
    ![Использование критериев для фильтрации записей](../../media/View-DNS-Resource-Records-for-a-DNS-Zone/ipam_DNSzones_01d.jpg)  
  
## <a name="see-also"></a>См. также  
[Управление зоной DNS](DNS-Zone-Management.md)  
[Управление IPAM](Manage-IPAM.md)  
  


