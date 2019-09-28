---
title: Служба доменных имен (DNS)
description: В этом разделе приводится обзор DNS в Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-dns
ms.topic: article
ms.assetid: 1324ba18-4e28-4b9d-bbe7-75707e6d30ab
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 6ad3b66ff0b271c3b6f6134a96aaf6b5171bc7d4
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71406167"
---
# <a name="domain-name-system-dns"></a>Служба доменных имен (DNS)

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

Служба доменных имен (DNS) — это один из стандартных отраслевых протоколов, включающих TCP/IP, а клиент DNS и DNS-сервер предоставляют службам разрешения имен IP-адресов компьютеров и пользователей.  
  
> [!NOTE]  
> Помимо этого раздела, доступно следующее содержимое DNS.  
>   
> -   [Новые возможности DNS-клиента](What-s-New-in-DNS-Client.md)  
> -   [Новые возможности DNS-сервера](What-s-New-in-DNS-Server.md)  
> -   [Рекомендации по сценариям политики DNS](deploy/DNS-Policy-Scenario-Guide.md)  
> -   Видео @no__t 0Windows Server 2016: Управление DNS в IPAM @ no__t-0  
  
В Windows Server 2016 DNS является ролью сервера, которую можно установить с помощью диспетчер сервера или команд Windows PowerShell. При установке нового леса Active Directory и домена служба DNS автоматически устанавливается с Active Directory в качестве глобального сервера каталога для леса и домена.  
  
Службы домен Active Directory Services (AD DS) используют DNS в качестве механизма расположения контроллера домена. При выполнении любой из основных Active Directory операций, таких как проверка подлинности, обновление или поиск, компьютеры используют DNS для поиска контроллеров домена Active Directory. Кроме того, контроллеры домена используют DNS для размещения друг друга.  
  
Служба DNS-клиента входит во все клиентские и серверные версии операционной системы Windows и работает по умолчанию при установке операционной системы. При настройке сетевого подключения TCP/IP с IP-адресом DNS-сервера клиент DNS запрашивает DNS-сервер для обнаружения контроллеров домена и разрешает имена компьютеров в IP-адреса. Например, когда пользователь сети с учетной записью пользователя Active Directory входит в домен Active Directory, служба DNS-клиента запрашивает у DNS-сервера поиск контроллера домена для Active Directory домена. Когда DNS-сервер отвечает на запрос и предоставляет клиенту IP-адрес контроллера домена, клиент связывается с контроллером домена, и процесс проверки подлинности может быть начат.  
  
DNS-сервер Windows Server 2016 и службы DNS-клиента используют протокол DNS, включенный в набор протоколов TCP/IP. DNS является частью уровня приложения в модели справочника по протоколу TCP/IP, как показано на следующем рисунке.  
  
![DNS в TCP/IP](../media/Domain-Name-System--DNS-/dns_in_tcpip.jpg)  
  

