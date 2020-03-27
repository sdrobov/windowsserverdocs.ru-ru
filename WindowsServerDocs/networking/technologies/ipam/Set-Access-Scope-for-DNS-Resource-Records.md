---
title: Задание области доступа для записей ресурсов DNS
description: Этот раздел является частью руководства по управлению IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a96a8752-5678-49c5-b069-d2cce8042a51
ms.author: lizross
author: eross-msft
ms.openlocfilehash: fd084c856b4f78810ce732fd64b801d6b0f7b67d
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80316785"
---
# <a name="set-access-scope-for-dns-resource-records"></a>Задание области доступа для записей ресурсов DNS

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Этот раздел можно использовать для задания области доступа для записей ресурсов DNS с помощью консоли клиента IPAM.  
  
Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  
  
### <a name="to-set-access-scope-for-dns-resource-records"></a>Настройка области доступа для записей ресурсов DNS  
  
1.  В диспетчер сервера щелкните **IPAM**. Откроется консоль клиента IPAM.  
  
2.  В области навигации щелкните **зоны DNS**.  В нижней области навигации разверните узел **прямой просмотр** и выберите зону, содержащую записи ресурсов, область доступа которой требуется изменить.  
  
3.  На панели "дисплей" выберите записи ресурсов, область доступа к которой необходимо изменить.  
  
    ![Выбор записей ресурсов](../../media/Set-Access-Scope-for-DNS-Resource-Records/ipam_RestrictUserToRRControl_02.jpg)  
  
4.  Щелкните правой кнопкой мыши выбранные записи ресурсов DNS и выберите **задать область доступа**.  
  
    ![Задание области доступа](../../media/Set-Access-Scope-for-DNS-Resource-Records/ipam_RestrictUserToRRControl_03.jpg)  
  
5.  Откроется диалоговое окно **Установка области доступа** . Если требуется для развертывания, щелкните, чтобы снять флажок **наследовать область доступа от родительского объекта**. В **области выберите область доступа**выберите элемент и нажмите кнопку **ОК**.  
  
    ![Выберите область доступа](../../media/Set-Access-Scope-for-DNS-Resource-Records/ipam_RestrictUserToRRControl_04.jpg)  
  
## <a name="see-also"></a>См. также  
[Управление доступом на основе ролей](Role-based-Access-Control.md)  
[Управление IPAM](Manage-IPAM.md)  
  


