---
title: "Перенос прокси-сервера AD FS 2.0 federation"
description: "Сведения о миграции прокси-сервер в Службах федерации Active Directory в Windows Server 2012 R2."
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 33ab29fd5efdb0bdd1fe25580e3f4434071e1c7d
ms.sourcegitcommit: 03ce78a1624dbd7f4e6abf2ec1ef185b55de29a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2017
---
# <a name="migrate-the-active-directory-federation-services-proxy-server-to-windows-server-2012-r2"></a>Перенос прокси-сервер служб федерации Active Directory в Windows Server 2012 R2

В службах Active Directory федерации (AD FS) в Windows Server 2012 R2 роль прокси-сервера федерации выполняет новая служба роли удаленного доступа с именем прокси веб-приложения. В Windows Server 2012 R2 Чтобы включить AD FS за пределами корпоративной сети, можно развернуть один или несколько прокси веб-приложений. Тем не менее нельзя перенести прокси-сервера федерации под управлением Windows Server 2008 R2 или Windows Server 2012 в прокси веб-приложения, работающими под управлением Windows Server 2012 R2.  
  
> [!IMPORTANT]
>  Перенос прокси-сервера федерации под управлением Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012 в прокси веб-приложения, работающими под управлением Windows Server 2012 R2 не поддерживается.  
  
Если вы хотите настроить AD FS в перенесенной ферме серверов Windows Server 2012 R2 для доступа через экстрасеть, необходимо выполнить новое развертывание одного или нескольких компьютеров прокси веб-приложения в рамках инфраструктуры AD FS.  
  
Для планирования развертывания прокси веб-приложения, можно просмотреть сведения в следующих разделах:  
  
-   [Планирование инфраструктуры прокси-сервера веб-приложения](https://technet.microsoft.com/en-us/library/dn383648.aspx)  
  
-   [Планирование сервера прокси-сервера веб-приложений](https://technet.microsoft.com/en-us/library/dn383647.aspx)  
  
 Для развертывания прокси-сервера веб-приложения можно следовать процедурам в следующих разделах:  
  
-   [Настройка инфраструктуры прокси-сервера веб-приложений](https://technet.microsoft.com/en-us/library/dn383644.aspx)  
  
-   [Установка и настройка сервера прокси-сервера веб-приложений](https://technet.microsoft.com/en-us/library/dn383662.aspx)  
  
## <a name="next-steps"></a>Дальнейшие действия
 [Перенос служб ролей для служб федерации Active Directory в Windows Server 2012 R2](migrate-ad-fs-service-role-to-windows-server-r2.md)   
 [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)   
 [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)    
 [Проверка переноса AD FS в Windows Server 2012 R2](verify-ad-fs-migration.md)

