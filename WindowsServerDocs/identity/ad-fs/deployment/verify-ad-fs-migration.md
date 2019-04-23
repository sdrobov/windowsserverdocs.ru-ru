---
title: Перенос сервера AD FS 2.0 federation
description: Сведения о переносе сервера AD FS в Windows Server 2012 R2.
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 0a3e8e444f715fe2ae0f0ccd858d90e8664be00c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59877775"
---
# <a name="verify-the-ad-fs-20-migration-to-windows-server-2012-r2"></a>Проверьте AD FS 2.0 перехода на Windows Server 2012 R2

После завершения переноса сервера фермы службы федерации Active Directory (AD FS) в Windows Server 2012 R2, можно использовать следующую процедуру для проверки работоспособности; серверы федерации в ферме то есть что ваши серверы federtation сможем связаться с любого клиента в той же сети.  
  
Минимальным требованием для выполнения этой процедуры является членство в одной из следующих групп: **Пользователи**, **Операторы архива**, **Опытные пользователи**, **Администраторы**, — или эквивалентной группе на локальном компьютере.
  
### <a name="to-verify-that-a-federation-server-is-operational"></a>Проверка работоспособности сервера федерации  
  
1.  Откройте окно браузера и в адресной строке введите имя серверов федерации и затем добавьте к нему `federationmetadata/2007-06/federationmetadata.xml` для перехода к конечной точке метаданных службы федерации. Например `https://fs.contoso.com/federationmetadata/2007-06/federationmetadata.xml` .  
  
Если в окне браузера вы увидите метаданные сервера федерации без каких-либо ошибок или предупреждений по поводу SSL-сертификата, то сервер федерации работоспособен.  
  
2.  Также можно перейти на страницу входа служб федерации Active Directory (добавьте к имени службы федерации строку `adfs/ls/idpinitiatedsignon.htm`, например `https://fs.contoso.com/adfs/ls/idpinitiatedsignon.htm`).  Появится страница входа в службы федерации Active Directory, на которой можно выполнить вход с учетными данными администратора домена.  
  
> [!IMPORTANT]
>  Обязательно настройте в параметрах браузера доверие к роли сервера федерации, добавив имя службы федерации (например, `https://fs.contoso.com`) в зону "Локальная интрасеть" в браузере.  
  
## <a name="next-steps"></a>Следующие шаги
 [Перенос служб ролей для служб федерации Active Directory в Windows Server 2012 R2](migrate-ad-fs-service-role-to-windows-server-r2.md)   
 [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)  
 [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)   
 [Миграция прокси-сервера федерации AD FS](migrate-fed-server-proxy-r2.md)   
