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
ms.author: pashort
author: shortpatti
ms.openlocfilehash: dbd46ad129a4b3e5bbbe55f584f1bae43bd077c3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71355422"
---
# <a name="create-a-dns-zone"></a>Создание зоны DNS

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

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
  


