---
title: "Миграция веб-агент AD FS"
description: "Содержит сведения о веб-агент AD FS в Windows Server 2012."
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 945a5f4cf0e6c491479b095671ff5e77416c6fa3
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="migrate-the-ad-fs-web-agent"></a>Миграция веб-агент AD FS

Для переноса AD FS 1.1 агент, использующий токены Windows, или AD агент по утверждениям FS 1.1, установленного с Windows Server 2008 R2 или Windows Server 2008 на Windows Server 2012, выполните обновление на месте операционной системы компьютера, на котором размещен либо агентов, до Windows Server 2012. Дополнительные сведения см. в разделе [Установка Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx). Никакая дополнительная настройка не требуется.  
  
> [!IMPORTANT]
>  Перенесенные AD FS 1.1 Windows агент, использующий токены работает только со службой 1.1 федерации AD FS, установленная с Windows Server 2008 R2 или Windows Server 2008. Дополнительные сведения см. в разделе [взаимодействии с AD FS 1.x](Interoperating-with-AD-FS-1.x.md).  
>   
>  Перенесенные AD FS 1.1 утверждениям веб-агент функционирует со следующими:  
>   
>  -   Службой федерации AD FS 1.1, установленного с Windows Server 2008 R2 или Windows Server 2008  
> -   Службой федерации AD FS 2.0 установлена на Windows Server 2008 R2 или Windows Server 2008  
> -   Службой федерации AD FS, установленного с Windows Server 2012  
>   
>  Дополнительные сведения см. в разделе [взаимодействии с AD FS 1.x](Interoperating-with-AD-FS-1.x.md).  
  
  
## <a name="next-steps"></a>Дальнейшие действия
 [Подготовка к миграции сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к миграции прокси-сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенос сервера AD FS 2.0 Federation](migrate-the-ad-fs-fed-server.md)   
 [Перенос прокси-сервера AD FS 2.0 Federation](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос 1.1 веб-агенты AD FS](migrate-the-ad-fs-web-agent.md)