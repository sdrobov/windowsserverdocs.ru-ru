---
title: Перенос сервера федерации AD FS 2,0
description: Содержит сведения о миграции AD FS Server на Windows Server 2012 R2.
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 1357c4bd86f45de5d83b38419b3612afc123dea9
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70867886"
---
# <a name="verify-the-ad-fs-20-migration-to-windows-server-2012-r2"></a>Проверка перехода AD FS 2,0 на Windows Server 2012 R2

После того как вы выполните ту же миграцию сервера Active Directory служба федерации (AD FS) на Windows Server 2012 R2, можно использовать следующую процедуру, чтобы убедиться в работоспособности серверов федерации в ферме. то есть любой клиент в той же сети может получить доступ к серверам федертатион.  
  
Минимальным требованием для выполнения этой процедуры является членство в одной из следующих групп: **Пользователи**, **Операторы архива**, **Опытные пользователи**, **Администраторы**, — или эквивалентной группе на локальном компьютере.
  
### <a name="to-verify-that-a-federation-server-is-operational"></a>Проверка работоспособности сервера федерации  
  
1.  Откройте окно браузера и в адресной строке введите имя сервера федерации, а затем добавьте его с помощью `federationmetadata/2007-06/federationmetadata.xml` , чтобы перейти к конечной точке метаданных службы федерации. Например, `https://fs.contoso.com/federationmetadata/2007-06/federationmetadata.xml` .  
  
Если в окне браузера вы увидите метаданные сервера федерации без каких-либо ошибок или предупреждений по поводу SSL-сертификата, то сервер федерации работоспособен.  
  
2. Также можно перейти на страницу входа служб федерации Active Directory (добавьте к имени службы федерации строку `adfs/ls/idpinitiatedsignon.htm`, например `https://fs.contoso.com/adfs/ls/idpinitiatedsignon.htm`).  Появится страница входа в службы федерации Active Directory, на которой можно выполнить вход с учетными данными администратора домена.  
  
> [!IMPORTANT]
>  Обязательно настройте параметры браузера, чтобы они доверяли роли сервера федерации, добавив имя службы федерации (например, `https://fs.contoso.com`) в зону локальной интрасети браузера.  
  
## <a name="next-steps"></a>Следующие шаги
 [Миграция служб ролей службы федерации Active Directory (AD FS) на Windows Server 2012 R2](migrate-ad-fs-service-role-to-windows-server-r2.md)   
 [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)  
 [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)   
 [Перенос прокси-сервера AD FS Федерации](migrate-fed-server-proxy-r2.md)   
