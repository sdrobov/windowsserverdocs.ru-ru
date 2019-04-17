---
title: "Перенос сервера AD FS 2.0 федерации"
description: "Сведения о миграции сервер AD FS в Windows Server 2012 R2."
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 0a3e8e444f715fe2ae0f0ccd858d90e8664be00c
ms.sourcegitcommit: 03ce78a1624dbd7f4e6abf2ec1ef185b55de29a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2017
---
# <a name="verify-the-ad-fs-20-migration-to-windows-server-2012-r2"></a>Проверьте AD FS 2.0 миграции на Windows Server 2012 R2

После завершения переноса сервера фермы службы федерации Active Directory (AD FS) в Windows Server 2012 R2 можно использовать следующую процедуру для проверки работоспособности; серверов федерации в ферме то есть что серверы federtation может связаться с любого клиента в той же сети.  
  
Членство в группе **пользователей**, **операторы архива**, **Опытные пользователи**, **Администраторы** или эквивалентной группе на локальном компьютере минимальным требованием для выполнения этой процедуры.
  
### <a name="to-verify-that-a-federation-server-is-operational"></a>Чтобы проверить работоспособность сервера федерации  
  
1.  Откройте окно браузера и введите в адресной строке имя серверов федерации и затем добавьте к нему `federationmetadata/2007-06/federationmetadata.xml` чтобы перейти к конечной точке метаданных службы федерации. Например `https://fs.contoso.com/federationmetadata/2007-06/federationmetadata.xml` .  
  
Если в окне браузера вы увидите метаданные сервера федерации без SSL ошибок и предупреждений, сервер федерации работоспособен.  
  
2.  Также можно перейти на страницу входа AD FS (к имени службы федерации с `adfs/ls/idpinitiatedsignon.htm`, например `https://fs.contoso.com/adfs/ls/idpinitiatedsignon.htm`).  При этом отображаются AD FS-страницу входа которой можно выполнить вход с учетными данными администратора домена.  
  
> [!IMPORTANT]
>  Обязательно Настройте в параметрах браузера доверие роли сервера федерации, добавив имя службы федерации (например, `https://fs.contoso.com`) в зону местной интрасети в браузере.  
  
## <a name="next-steps"></a>Дальнейшие действия
 [Перенос служб ролей для служб федерации Active Directory в Windows Server 2012 R2](migrate-ad-fs-service-role-to-windows-server-r2.md)   
 [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)  
 [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)   
 [Миграция прокси-сервера федерации AD FS](migrate-fed-server-proxy-r2.md)   
