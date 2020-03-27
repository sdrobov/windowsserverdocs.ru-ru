---
title: Создание зоны DNS
description: Этот раздел является частью руководства по управлению IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a030ff51-a815-4fc4-b26d-aae41c3e4ce5
ms.author: lizross
author: eross-msft
ms.openlocfilehash: a9762d15d0b95954623bbefdec38696885676975
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80312638"
---
# <a name="create-a-dns-zone"></a>Создание зоны DNS

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

С помощью этого раздела можно создать зону DNS с помощью консоли клиента IPAM.  
  
Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  
  
### <a name="to-create-a-dns-zone"></a>Создание зоны DNS  
  
1.  В диспетчер сервера щелкните **IPAM**. Откроется консоль клиента IPAM.  
  
2.  В области навигации в окне **мониторинг и управление**щелкните **DNS и DHCP-серверы**. На панели "дисплей" выберите **Тип сервера**, а затем щелкните **DNS**. Все DNS-серверы, управляемые IPAM, перечислены в результатах поиска.  
  
3.  Выберите сервер, на который нужно добавить зону, и щелкните правой кнопкой мыши сервер.  Щелкните **создать зону DNS**.  
  
    ![Создание зоны DNS](../../media/Create-a-DNS-Zone/ipam_CreateDNSZone_01a.jpg)  
  
4.  Откроется диалоговое окно **Создание зоны DNS** . В окне **Общие свойства**выберите категорию зоны, тип зоны и введите имя в списке **имя зоны**. Также выберите значения, подходящие для развертывания, в окне **Дополнительные свойства**и нажмите кнопку **ОК**.  
  
    ![Дополнительные свойства](../../media/Create-a-DNS-Zone/ipam_CreateDNSZone_02a.jpg)  
  
## <a name="see-also"></a>См. также  
[Управление зоной DNS](DNS-Zone-Management.md)  
[Управление IPAM](Manage-IPAM.md)  
  


