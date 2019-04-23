---
title: Управление доступом на основе ролей
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
ms.assetid: ecdfc589-fa14-4bb3-ab7e-456ebc719385
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 86a57e5a74073ecf749c4ec8209999e8ace31508
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59838905"
---
# <a name="role-based-access-control"></a>Управление доступом на основе ролей

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Этот раздел содержит сведения об использовании управления доступом на основе ролей в IPAM.  
  
> [!NOTE]  
> Помимо этого раздела ниже документацию по контролю доступа IPAM доступна в этом разделе.  
>   
> -   [На основе ролей доступ к элементу управления с помощью диспетчера серверов](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Server-Manager.md)  
> -   [На основе ролей доступ к элементу управления с помощью Windows PowerShell](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Windows-PowerShell.md)  
  
Управление доступом на основе ролей позволяет указать права доступа на различных уровнях, включая DNS-сервер, зоны DNS и уровней записей ресурсов DNS.  
С помощью управления доступом на основе ролей, можно указать, кто имеет контроль над операции на создание, изменение и удаление различных типов записей ресурсов DNS.  
  
Управление доступом можно настроить таким образом, чтобы пользователи ограничены следующие разрешения.  
  
-   Пользователи могут изменять только определенные записи ресурсов DNS  
  
-   Пользователи могут изменять записи ресурсов DNS определенного типа, например PTR или MX  
  
-   Пользователи могут изменять записи ресурсов DNS для конкретных зон  
  
## <a name="see-also"></a>См. также  
[На основе ролей доступ к элементу управления с помощью диспетчера серверов](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Server-Manager.md)  
[На основе ролей доступ к элементу управления с помощью Windows PowerShell](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Windows-PowerShell.md)  
[Управление IPAM](Manage-IPAM.md)  
  


