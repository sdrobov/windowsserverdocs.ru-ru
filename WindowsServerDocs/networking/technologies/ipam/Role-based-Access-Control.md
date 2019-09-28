---
title: Управление доступом на основе ролей
description: Этот раздел является частью руководства по управлению IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ecdfc589-fa14-4bb3-ab7e-456ebc719385
ms.author: pashort
author: shortpatti
ms.openlocfilehash: cf6b8418482b606c86bac77b2790e3365e80bf5d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71355155"
---
# <a name="role-based-access-control"></a>Управление доступом на основе ролей

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе содержатся сведения об использовании управления доступом на основе ролей в IPAM.  
  
> [!NOTE]  
> Помимо этого раздела, в этом разделе доступна следующая документация по контролю доступа IPAM.  
>   
> -   [Управление доступом на основе ролей с помощью диспетчер сервера](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Server-Manager.md)  
> -   [Управление доступом на основе ролей с помощью Windows PowerShell](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Windows-PowerShell.md)  
  
Управление доступом на основе ролей позволяет задавать привилегии доступа на различных уровнях, включая DNS-сервер, зону DNS и уровни записи ресурсов DNS.  
С помощью управления доступом на основе ролей можно указать, кто имеет детальный контроль над операциями для создания, изменения и удаления различных типов записей ресурсов DNS.  
  
Можно настроить контроль доступа, чтобы пользователи были ограничены следующими разрешениями.  
  
-   Пользователи могут изменять только определенные записи ресурсов DNS.  
  
-   Пользователи могут изменять записи ресурсов DNS определенного типа, например PTR или MX.  
  
-   Пользователи могут изменять записи ресурсов DNS для конкретных зон.  
  
## <a name="see-also"></a>См. также  
[Управление доступом на основе ролей с помощью диспетчер сервера](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Server-Manager.md)  
[Управление доступом на основе ролей с помощью Windows PowerShell](../../technologies/ipam/Manage-Role-Based-Access-Control-with-Windows-PowerShell.md)  
[Управление IPAM](Manage-IPAM.md)  
  


