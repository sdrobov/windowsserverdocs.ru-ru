---
title: Служба доменных имен (DNS)
description: В этом разделе представлен обзор службы DNS в Windows Server 2016
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-dns
ms.topic: article
ms.assetid: 1324ba18-4e28-4b9d-bbe7-75707e6d30ab
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 3d4ec63e904dd899a3ddc53a59274ad607136edd
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59870825"
---
# <a name="domain-name-system-dns"></a>Служба доменных имен (DNS)

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Система доменных имен (DNS) является одним из стандартных в отрасли наборов протоколов, реализующих взаимодействие TCP/IP и обеспечивают DNS-клиент и DNS-сервер службы разрешения имен сопоставление имя IP-адрес компьютера для компьютеров и пользователей.  
  
> [!NOTE]  
> Помимо этого раздела доступно следующее содержимое DNS.  
>   
> -   [Новые возможности DNS-клиента](What-s-New-in-DNS-Client.md)  
> -   [Новые возможности DNS-сервера](What-s-New-in-DNS-Server.md)  
> -   [Руководство по сценарию политики DNS](deploy/DNS-Policy-Scenario-Guide.md)  
> -   Видео [Windows Server 2016: Управление DNS в IPAM](https://channel9.msdn.com/Blogs/windowsserver/Windows-Server-2016-DNS-management-in-IPAM)  
  
В Windows Server 2016 DNS — это роль сервера, который можно установить с помощью диспетчера серверов или Windows PowerShell команд. При установке нового леса Active Directory и домен, DNS устанавливается автоматически вместе с Active Directory в качестве сервера глобального каталога для леса и домена.  
  
Доменных служб Active Directory (AD DS) использует DNS в качестве механизма расположение контроллера домена. При выполнении любых операций основной Active Directory, такие как проверка подлинности, обновление или выполните поиск, компьютеры используют DNS для обнаружения контроллеров домена Active Directory. Кроме того контроллеры домена используют DNS находить друг друга.  
  
Служба DNS-клиента включается во все клиентские и серверные версии операционной системы Windows и выполняется по умолчанию после установки операционной системы. Если необходимо настроить сетевые подключения TCP/IP с IP-адрес DNS-сервера, DNS-клиент запрашивает сервера DNS для обнаружения контроллеров домена, а также для разрешения имен в IP-адреса. Например при входе пользователя сети с помощью учетной записи пользователя Active Directory для домена Active Directory, служба DNS-клиент запрашивает DNS-сервер для поиска контроллера домена для домена Active Directory. Когда DNS-сервер отвечает на запрос и предоставляет IP-адрес контроллера домена клиенту, клиент обращается к контроллеру домена, и можно начать процесс проверки подлинности.  
  
Службы DNS-сервера Windows Server 2016 и DNS-клиента используют протокол DNS, которое включено в набор протоколов TCP/IP. DNS является частью уровня приложения эталонной модели TCP/IP, как показано на следующем рисунке.  
  
![DNS в TCP/IP](../media/Domain-Name-System--DNS-/dns_in_tcpip.jpg)  
  

