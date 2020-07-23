---
title: Перенос веб-агента AD FS
description: Предоставляет сведения о веб-агенте AD FS для Windows Server 2012.
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 3c18e0a6a2e633c0fad0ce8585296afba8ce444c
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966936"
---
# <a name="migrate-the-ad-fs-web-agent"></a>Перенос веб-агента AD FS

Чтобы перенести агент на основе маркеров Windows AD FS 1,1 или агент AD FS 1,1 с поддержкой утверждений, установленный вместе с Windows Server 2008 R2 или Windows Server 2008 до Windows Server 2012, выполните обновление операционной системы компьютера, на котором размещается агент, на Windows Server 2012. Дополнительные сведения см. в разделе [Установка Windows Server 2012](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj134246(v=ws.11)). Дальнейшая настройка не требуется.  
  
> [!IMPORTANT]
>  Перенесенный агент AD FS 1.1, использующий токены Windows, работает только со службой федерации AD FS 1.1, которая устанавливается с Windows Server 2008 R2 или Windows Server 2008. Дополнительные сведения см. в разделе [Interoperating with AD FS 1.x](Interoperating-with-AD-FS-1.x.md).  
> 
>  Перенесенный веб-агент по утверждениям AD FS 1.1 функционирует со следующими системами:  
> 
> - службой федерации AD FS 1.1, установленной с Windows Server 2008 R2 или Windows Server 2008;  
>   -   службой федерации AD FS 2.0, установленной в Windows Server 2008 R2 или Windows Server 2008;  
>   -   AD FS Служба федерации, установленная с Windows Server 2012  
> 
>   Дополнительные сведения см. в разделе [Interoperating with AD FS 1.x](Interoperating-with-AD-FS-1.x.md).  
  
  
## <a name="next-steps"></a>Дальнейшие шаги
 [Подготовка к миграции сервера федерации AD FS 2,0](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к миграции прокси-сервера AD FS 2,0 Федерации](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенос сервера федерации AD FS 2,0](migrate-the-ad-fs-fed-server.md)   
 [Перенос прокси-сервера AD FS 2,0 Федерации](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)
