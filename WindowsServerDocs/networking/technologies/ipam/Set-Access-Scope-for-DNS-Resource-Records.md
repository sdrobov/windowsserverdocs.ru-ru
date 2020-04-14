---
title: Задание области доступа для записей ресурсов DNS
description: Этот раздел является частью руководства по управлению IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ipam
ms.topic: article
ms.assetid: a96a8752-5678-49c5-b069-d2cce8042a51
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 613796c933498d104db4895733c9a9b1957cb952
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860617"
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
  


