---
title: Создание роли пользователя для управления доступом
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
ms.assetid: ae6a42db-a104-401b-a8e6-b85c47d30b46
ms.author: pashort
author: shortpatti
ms.openlocfilehash: fa0ed71d399ad638a648946952fe170d93f69ceb
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="create-a-user-role-for-access-control"></a>Создание роли пользователя для управления доступом

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать для создания новой роли пользователя управления доступом в консоли IPAM-клиента.  
  
Членство в группе **Администраторы**, или в эквивалентной минимальным требованием для выполнения этой процедуры.  
  
> [!NOTE]  
> После создания роли, можно создать политику доступа, чтобы назначить роль для конкретного пользователя или группы Active Directory. Дополнительные сведения см. в разделе [Создание политики доступа](../../technologies/ipam/Create-an-Access-Policy.md).  
  
### <a name="to-create-a-role"></a>Создание роли  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль IPAM-клиента.  
  
2.  В области навигации щелкните **КОНТРОЛЯ доступа**и в нижней области навигации щелкните **ролей**.  
  
    ![Ролей управления доступом](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_01.jpg)  
  
3.  Щелкните правой кнопкой мыши **ролей**, а затем нажмите кнопку **добавить роль пользователя**.  
  
    ![Добавить роль пользователя](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_02.jpg)  
  
4.  **Добавление или изменение роли** откроется диалоговое окно. В **имя**, введите имя для роли, функциональность роли очистить. Например, если вы хотите создать роль, которая позволяет администраторам управлять записи ресурсов DNS SRV, можно присвоить имя роли **IPAMSrv**. Если требуется, прокрутите вниз в **операций** и найдите тип операции, которую требуется определить для роли. Например, прокрутите вниз до **операции Управление записями ресурсов DNS-сервера**.  
  
    ![Операции Управление записями ресурсов DNS-сервера](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_03.jpg)  
  
5.  Разверните **операции Управление записями ресурсов DNS-сервера**, а затем найдите **операций записи SRV**.  
  
    ![Операций записи SRV](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_04.jpg)  
  
6.  Разверните и выберите **операций записи SRV**, а затем нажмите кнопку **ОК**.  
  
    ![Выбрать операции записи SRV](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_05.jpg)  
  
7.  В консоли IPAM-клиента выберите роль, которую вы только что создали. В **Просмотр подробностей** отображаются допустимые операции для роли.  
  
    ![Сведения о новой роли](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_06.jpg)  
  
## <a name="see-also"></a>См. также:  
[Управление доступом на основе ролей](Role-based-Access-Control.md)  
[Управление IPAM](Manage-IPAM.md)  
  


