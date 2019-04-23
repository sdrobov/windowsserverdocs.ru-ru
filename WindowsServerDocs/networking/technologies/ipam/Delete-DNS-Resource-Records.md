---
title: Удаление записей ресурсов DNS
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
ms.assetid: 366e6fd5-d563-4de3-9551-5614cbb8f2cb
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 2d3c5f4f02cc1a8386bf12fe634620ba98f2f23a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59883225"
---
# <a name="delete-dns-resource-records"></a>Удаление записей ресурсов DNS

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Чтобы удалить одну или несколько записей ресурсов DNS с помощью консоли клиента IPAM, можно использовать в этом разделе.  
  
Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  
  
### <a name="to-delete-dns-resource-records"></a>Для удаления записей ресурсов DNS  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль ipam-клиента.  
  
2.  В области навигации в **НАБЛЮДЕНИЕ и УПРАВЛЕНИЕ**, нажмите кнопку **зон DNS**.  На панели навигации делит на верхней панели навигации и нижней панели навигации.  
  
3.  Щелкните, чтобы развернуть **прямого просмотра** и домен, где расположены записи зоны и ресурсов, которые требуется удалить. Выберите в зоне и на панели отображения, щелкните **текущее представление**. Нажмите кнопку **записей ресурсов**.  
  
4.  В панели «дисплей» найдите и выберите записей ресурсов, которые требуется удалить.  
  
    ![Выберите записи ресурса для удаления](../../media/Delete-DNS-Resource-Records/ipam_DeleteRR_01.jpg)  
  
5.  Щелкните правой кнопкой мыши выбранные записи, а затем нажмите кнопку **запись ресурса DNS на удаление**.  
  
    ![Удалить записи](../../media/Delete-DNS-Resource-Records/ipam_DeleteRR_02.jpg)  
  
6.  **Удалить запись ресурса DNS** откроется диалоговое окно. Убедитесь, что выбран правильный DNS-сервер. Если это не так, нажмите кнопку **DNS-сервер** и выберите сервер, из которого требуется удалить записи ресурсов. Нажмите кнопку **ОК**. IPAM удаляет записи ресурсов DNS-сервера.  
  
    ![Убедитесь, что выбран правильный DNS-сервера и удаления записей](../../media/Delete-DNS-Resource-Records/ipam_DeleteRR_03.jpg)  
  
## <a name="see-also"></a>См. также  
[Управление записями ресурсов DNS](DNS-Resource-Record-Management.md)  
[Управление IPAM](Manage-IPAM.md)  
  


