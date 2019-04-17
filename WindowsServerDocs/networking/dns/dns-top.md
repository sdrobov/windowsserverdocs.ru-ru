---
title: Системе доменных имен (DNS)
description: В этом разделе представлен обзор DNS-сервера в Windows Server 2016
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-dns
ms.topic: article
ms.assetid: 1324ba18-4e28-4b9d-bbe7-75707e6d30ab
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 23851d2d8015fc6ae9e0653e8a0843f8c4295162
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="domain-name-system-dns"></a>Системе доменных имен (DNS)

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Система доменных имен (DNS) — это один набор стандартных протоколов, реализующих взаимодействие TCP/IP и вместе DNS-клиент и DNS-сервера предоставляют компьютеру имя to-IP адрес сопоставления службы разрешения имен для компьютеров и пользователей.  
  
> [!NOTE]  
> Дополнение к данному разделу доступна следующее содержимое DNS.  
>   
> -   [Новые возможности DNS-клиента](What-s-New-in-DNS-Client.md)  
> -   [Новые возможности DNS-сервера](What-s-New-in-DNS-Server.md)  
> -   [Руководство по сценарию политики DNS](deploy/DNS-Policy-Scenario-Guide.md)  
> -   Видео: [Windows Server 2016: управления DNS в IPAM](https://channel9.msdn.com/Blogs/windowsserver/Windows-Server-2016-DNS-management-in-IPAM)  
  
В Windows Server 2016 DNS — это роль сервера, который можно установить с помощью диспетчера сервера или Windows PowerShell команд. При установке нового леса Active Directory и домен, DNS-сервера устанавливается автоматически вместе с Active Directory в качестве сервера глобального каталога для леса и домена.  
  
DNS использует доменных служб Active Directory (AD DS) в качестве механизма расположение контроллера домена. При выполнении любых участника операций Active Directory, такие как проверка подлинности, обновление или поиска, компьютеры используют DNS для обнаружения контроллеров домена Active Directory. Кроме того контроллеры домена используют DNS для обнаружения друг с другом.  
  
Служба DNS-клиент входит во все клиентские и серверные версии операционной системы Windows и выполняется по умолчанию после установки операционной системы. При настройке сетевое подключение TCP/IP с помощью IP-адрес DNS-сервера, DNS-клиент запрашивает DNS-сервера для обнаружения контроллеров домена и разрешения имен компьютеров в IP-адреса. Например при входе пользователей с помощью учетной записи пользователя в Active Directory для домена Active Directory, служба DNS-клиента запрашивает DNS-сервер, чтобы найти контроллер домена для домена Active Directory. Когда DNS-сервер отвечает на запрос и предоставляет IP-адрес контроллера домена клиенту, клиент обращается к контроллеру домена, и можно начать процесс проверки подлинности.  
  
Служба DNS-сервера Windows Server 2016 и DNS-клиента использовать протокол DNS, который входит в набор протоколов TCP/IP. DNS-сервера является частью на уровне приложения эталонной модели TCP/IP, как показано на следующем рисунке.  
  
![DNS в TCP/IP](../media/Domain-Name-System--DNS-/dns_in_tcpip.jpg)  
  

