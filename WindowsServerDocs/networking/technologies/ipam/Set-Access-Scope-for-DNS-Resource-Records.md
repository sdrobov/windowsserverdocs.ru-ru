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
ms.author: pashort
author: shortpatti
ms.openlocfilehash: b1790f2cbf84fd68f33ca30d2fe7663dde824240
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405645"
---
# <a name="set-access-scope-for-dns-resource-records"></a>Задание области доступа для записей ресурсов DNS

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

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
  


