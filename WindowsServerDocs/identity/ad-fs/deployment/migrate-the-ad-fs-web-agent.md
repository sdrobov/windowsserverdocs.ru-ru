---
title: Перенос веб-агент AD FS
description: Содержит сведения о веб-агент AD FS в Windows Server 2012.
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 7cde62cb23c69a425522e40ed65ee2d40ef28268
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66445592"
---
# <a name="migrate-the-ad-fs-web-agent"></a>Перенос веб-агент AD FS

Для переноса AD FS 1.1 агент, использующий токены Windows, или AD агент по утверждениям FS 1.1, которая устанавливается вместе с Windows Server 2008 R2 или Windows Server 2008 до Windows Server 2012, выполните обновление на месте операционной системы компьютера, на котором размещена либо агента в Windows Server 2012. Дополнительные сведения см. в разделе [Установка Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx). Никакая дополнительная настройка не требуется.  
  
> [!IMPORTANT]
>  Перенесенный агент AD FS 1.1, использующий токены Windows, работает только со службой федерации AD FS 1.1, которая устанавливается с Windows Server 2008 R2 или Windows Server 2008. Дополнительные сведения см. в разделе [Interoperating with AD FS 1.x](Interoperating-with-AD-FS-1.x.md).  
> 
>  Перенесенный веб-агент по утверждениям AD FS 1.1 функционирует со следующими системами:  
> 
> - службой федерации AD FS 1.1, установленной с Windows Server 2008 R2 или Windows Server 2008;  
>   -   службой федерации AD FS 2.0, установленной в Windows Server 2008 R2 или Windows Server 2008;  
>   -   Службой федерации AD FS устанавливается вместе с Windows Server 2012  
> 
>   Дополнительные сведения см. в разделе [Interoperating with AD FS 1.x](Interoperating-with-AD-FS-1.x.md).  
  
  
## <a name="next-steps"></a>Следующие шаги
 [Подготовка к миграции сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к миграции прокси-сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенос сервера AD FS 2.0 Federation](migrate-the-ad-fs-fed-server.md)   
 [Перенос прокси-сервера AD FS 2.0 Federation](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)