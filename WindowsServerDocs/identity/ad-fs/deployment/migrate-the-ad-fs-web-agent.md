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
ms.openlocfilehash: ddba9668b54e325dae6dfc0cf67d50d3ae5d90be
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408198"
---
# <a name="migrate-the-ad-fs-web-agent"></a>Перенос веб-агента AD FS

Чтобы перенести агент на основе маркеров Windows AD FS 1,1 или агент AD FS 1,1 с поддержкой утверждений, установленный вместе с Windows Server 2008 R2 или Windows Server 2008, на Windows Server 2012, выполните обновление операционной системы компьютера, на котором размещается любой агент, на месте. на Windows Server 2012. Дополнительные сведения см. в разделе [Установка Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx). Никакая дополнительная настройка не требуется.  
  
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
  
  
## <a name="next-steps"></a>Следующие шаги
 [Подготовка к переносу сервера федерации AD FS 2,0](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к переносу прокси-сервера AD FS 2,0 федерации](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенос сервера федерации AD FS 2,0](migrate-the-ad-fs-fed-server.md)   
 [Перенесите прокси-сервер AD FS 2,0 федерации](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)