---
title: Управление доступом на основе ролей
description: Этот раздел является частью руководства по управлению IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ipam
ms.topic: article
ms.assetid: ecdfc589-fa14-4bb3-ab7e-456ebc719385
ms.author: lizross
author: eross-msft
ms.openlocfilehash: ae5e36e9c0931ca5735df6111f73e87ef012ee5d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860597"
---
# <a name="role-based-access-control"></a>Управление доступом на основе ролей

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

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
  


