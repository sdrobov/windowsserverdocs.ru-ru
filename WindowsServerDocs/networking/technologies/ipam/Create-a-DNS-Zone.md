---
title: Создание зоны DNS
description: Этот раздел является частью руководства по управлению IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ipam
ms.topic: article
ms.assetid: a030ff51-a815-4fc4-b26d-aae41c3e4ce5
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 0ae9869b95cfa1da04e0103b5a824ff1fc21568f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80814757"
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
  


