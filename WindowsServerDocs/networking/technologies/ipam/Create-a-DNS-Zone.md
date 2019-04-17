---
title: Создание зоны DNS
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
ms.assetid: a030ff51-a815-4fc4-b26d-aae41c3e4ce5
ms.author: pashort
author: shortpatti
ms.openlocfilehash: e532837e6c98694fa040a6d47a8e536eecb4c3da
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="create-a-dns-zone"></a>Создание зоны DNS

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать для создания зоны DNS с помощью консоли клиента IPAM.  
  
Членство в группе **Администраторы**, или в эквивалентной минимальным требованием для выполнения этой процедуры.  
  
### <a name="to-create-a-dns-zone"></a>Создание зоны DNS  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль IPAM-клиента.  
  
2.  В области навигации в **НАБЛЮДЕНИЕ и УПРАВЛЕНИЕ**, нажмите кнопку **DNS и DHCP-серверы**. В панели «дисплей» выберите **тип сервера**, а затем нажмите кнопку **DNS**. В результатах поиска указаны все DNS-серверы, которые управляются IPAM.  
  
3.  Найдите сервер, где вы хотите добавить в зону и щелкните правой кнопкой мыши сервер.  Нажмите кнопку **создать DNS-зоны**.  
  
    ![Создание зоны DNS](../../media/Create-a-DNS-Zone/ipam_CreateDNSZone_01a.jpg)  
  
4.  **Создание зоны DNS** откроется диалоговое окно. В **общие свойства**, выберите зону категорию, тип зоны и введите имя в **имя зоны**. Также выберите подходящие значения для развертывания в **дополнительные свойства**, а затем нажмите кнопку **ОК**.  
  
    ![Расширенные свойства](../../media/Create-a-DNS-Zone/ipam_CreateDNSZone_02a.jpg)  
  
## <a name="see-also"></a>См. также:  
[Управление зоной DNS](DNS-Zone-Management.md)  
[Управление IPAM](Manage-IPAM.md)  
  


