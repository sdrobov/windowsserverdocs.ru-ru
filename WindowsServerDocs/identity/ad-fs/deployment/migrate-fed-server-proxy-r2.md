---
title: Перенос прокси-сервера AD FS 2.0 federation
description: Сведения о переносе сервера прокси-сервера AD FS в Windows Server 2012 R2.
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: a2eb6c670e704564bed49486b8950dab96da8a80
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66444569"
---
# <a name="migrate-the-active-directory-federation-services-proxy-server-to-windows-server-2012-r2"></a>Перенос прокси-сервер служб федерации Active Directory в Windows Server 2012 R2

В службах Active Directory Federation (AD FS) в Windows Server 2012 R2 роль прокси-сервера федерации выполняет, новая служба роли удаленного доступа, которая называется прокси веб-приложения. В Windows Server 2012 R2 чтобы разрешить доступ к AD FS за пределами корпоративной сети, можно развернуть один или несколько прокси веб-приложений. Тем не менее нельзя перенести прокси-сервера федерации под управлением Windows Server 2008 R2 или Windows Server 2012 в прокси веб-приложения, под управлением Windows Server 2012 R2.  
  
> [!IMPORTANT]
>  Перенос прокси-сервера федерации под управлением Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012 в прокси веб-приложения, под управлением Windows Server 2012 R2 не поддерживается.  
  
Если вы хотите настроить AD FS в перенесенной ферме Windows Server 2012 R2 для доступа через экстрасеть, необходимо выполнить новое развертывание одного или нескольких компьютеров прокси веб-приложения в качестве части инфраструктуры AD FS.  
  
При планировании развертывания прокси-сервера веб-приложения можно использовать сведения в следующих разделах.  
  
- [Планирование инфраструктуры прокси-сервера веб-приложения](https://technet.microsoft.com/library/dn383648.aspx)  
  
- [Планирование сервера прокси-сервера веб-приложений](https://technet.microsoft.com/library/dn383647.aspx)  
  
  При развертывании прокси-сервера веб-приложения можно следовать процедурам в следующих разделах.  
  
- [Настройка инфраструктуры прокси-сервера веб-приложений](https://technet.microsoft.com/library/dn383644.aspx)  
  
- [Установка и настройка сервера прокси-сервера веб-приложений](https://technet.microsoft.com/library/dn383662.aspx)  
  
## <a name="next-steps"></a>Следующие шаги
 [Перенос служб ролей для служб федерации Active Directory в Windows Server 2012 R2](migrate-ad-fs-service-role-to-windows-server-r2.md)   
 [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)   
 [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)    
 [Проверка переноса AD FS в Windows Server 2012 R2](verify-ad-fs-migration.md)

