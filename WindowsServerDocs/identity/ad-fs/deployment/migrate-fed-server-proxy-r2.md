---
title: Перенос прокси-сервера федерации AD FS 2,0
description: Содержит сведения о миграции AD FS прокси-сервера на Windows Server 2012 R2.
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 9a9b5f6454ec93ec27f557588016295935827c18
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966216"
---
# <a name="migrate-the-active-directory-federation-services-proxy-server-to-windows-server-2012-r2"></a>Миграция службы федерации Active Directory (AD FS) прокси-сервера на Windows Server 2012 R2

В службы федерации Active Directory (AD FS) (AD FS) в Windows Server 2012 R2 роль прокси-сервера федерации обрабатывается новой службой роли удаленного доступа, именуемой прокси-сервером веб приложения. В Windows Server 2012 R2, чтобы обеспечить доступность AD FS для доступа за пределами корпоративной сети, можно развернуть один или несколько прокси веб-приложений. Однако вы не можете перенести прокси-сервер федерации, работающий на Windows Server 2008 R2 или Windows Server 2012, в прокси веб – приложения, работающего на Windows Server 2012 R2.  
  
> [!IMPORTANT]
>  Миграция прокси-сервера федерации, работающего на Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012, к прокси веб приложения, работающему под Windows Server 2012 R2, не поддерживается.  
  
Если вы хотите настроить AD FS в перенесенной ферме Windows Server 2012 R2 для доступа к экстрасети, необходимо выполнить новое развертывание одного или нескольких компьютеров прокси-сервера приложений в рамках инфраструктуры AD FS.  
  
При планировании развертывания прокси-сервера веб-приложения можно использовать сведения в следующих разделах.  
  
- [Планирование инфраструктуры прокси веб-приложения](/previous-versions/orphan-topics/ws.11/dn383648(v=ws.11))  
  
- [Планирование прокси-сервера веб-приложений](/previous-versions/orphan-topics/ws.11/dn383647(v=ws.11))  
  
  При развертывании прокси-сервера веб-приложения можно следовать процедурам в следующих разделах.  
  
- [Настройка инфраструктуры прокси-сервера веб-приложений](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383644(v=ws.11))  
  
- [Установка и настройка прокси-сервера веб-приложений](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383662(v=ws.11))  
  
## <a name="next-steps"></a>Дальнейшие шаги
 [Миграция служб ролей службы федерации Active Directory (AD FS) на Windows Server 2012 R2](migrate-ad-fs-service-role-to-windows-server-r2.md)   
 [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)   
 [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)    
 [Проверка переноса AD FS на Windows Server 2012 R2](verify-ad-fs-migration.md)
