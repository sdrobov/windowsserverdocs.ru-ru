---
title: Создание роли пользователя для управления доступом
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
ms.assetid: ae6a42db-a104-401b-a8e6-b85c47d30b46
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 69d7acec19a460b51819bdc30ce40e21089c7bcf
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59823585"
---
# <a name="create-a-user-role-for-access-control"></a>Создание роли пользователя для управления доступом

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе можно использовать для создания новой роли контроля доступа в консоли ipam-клиента.  
  
Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  
  
> [!NOTE]  
> После создания роли, можно создать политику доступа, чтобы назначить роль для конкретного пользователя или группы Active Directory. Дополнительные сведения см. в разделе [Создание политики доступа](../../technologies/ipam/Create-an-Access-Policy.md).  
  
### <a name="to-create-a-role"></a>Создание роли  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль ipam-клиента.  
  
2.  В области навигации щелкните **КОНТРОЛЯ доступа**, а в нижней области навигации щелкните **ролей**.  
  
    ![Ролей управления доступом](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_01.jpg)  
  
3.  Щелкните правой кнопкой мыши **ролей**, а затем нажмите кнопку **добавить роль пользователя**.  
  
    ![Добавить роль пользователя](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_02.jpg)  
  
4.  **Добавить или изменить роль** откроется диалоговое окно. В **имя**, введите имя для роли, которая делает функцию роли очистить. Например, если вы хотите создать роль, которая позволяет администраторам управлять DNS SRV-записи, можно назвать роли **IPAMSrv**. При необходимости прокрутите вниз содержимое **операций** искомый тип операций, необходимо определить для роли. В этом примере прокрутите вниз до раздела **операции управления записями ресурсов DNS**.  
  
    ![Операции управления записями ресурсов DNS](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_03.jpg)  
  
5.  Разверните **операции управления записями ресурсов DNS**, а затем найдите **операции с записями SRV**.  
  
    ![Операции записи SRV](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_04.jpg)  
  
6.  Разверните и выберите **операции с записями SRV**, а затем нажмите кнопку **ОК**.  
  
    ![Выбор операций записи SRV](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_05.jpg)  
  
7.  В консоли клиента IPAM выберите роль, которую вы только что создали. В **Просмотр подробностей** отображаются разрешенные операции роли.  
  
    ![Сведения о новой роли](../../media/Create-a-User-Role-for-Access-Control/ipam_CreateUserRole_06.jpg)  
  
## <a name="see-also"></a>См. также  
[Управление доступом на основе ролей](Role-based-Access-Control.md)  
[Управление IPAM](Manage-IPAM.md)  
  


