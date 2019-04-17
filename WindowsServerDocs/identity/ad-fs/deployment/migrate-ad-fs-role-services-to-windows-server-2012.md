---
title: "Перенос служб ролей для служб федерации Active Directory в Windows Server 2012"
description: "Инструкции по переносу службы AD FS в Windows Server 2012."
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 2b44ed504c2b3dc8a8ac0ca9648f1db9e362e075
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="migrate-active-directory-federation-services-role-services-to-windows-server-2012"></a>Перенос служб ролей для служб федерации Active Directory в Windows Server 2012

Следующие инструкции по миграции следующие службы ролей для федерации служб Active Directory (AD FS) в Windows Server 2012:  
  
-   Агент на базе токенов AD FS 1.1 Windows и AD FS 1.1 утверждениям агента, установленного с Windows Server 2008 или Windows Server 2008 R2  
  
-   Сервер федерации AD FS 2.0 и прокси-сервера AD FS 2.0 федерации ОС Windows Server 2008 или Windows Server 2008 R2    
  
## <a name="supported-migration-scenarios"></a>Поддерживаемые сценарии миграции  
 Инструкции по миграции содержит следующие задачи:  
  
-   Экспорт данных AD FS 2.0 конфигурации с сервера под управлением Windows Server 2008 или Windows Server 2008 R2  
  
-   Обновление на месте операционной системы этого сервера с Windows Server 2008 или Windows Server 2008 R2 до Windows Server 2012.
  
-   Восстановление первоначальной конфигурации AD FS и остальных Служб федерации Active Directory параметров служб на этом сервере, где теперь выполняется роль сервера AD FS, установленная с Windows Server 2012.  
  
 Это руководство не содержит инструкций по миграции сервера, на котором выполняется несколько ролей. Если на сервере выполняется несколько ролей, рекомендуется разработать специальную процедуру миграции для данной серверной среды с использованием информации из других руководств по миграции ролей. Руководства по миграции для дополнительных ролей доступны на [портал миграции Windows Server](https://go.microsoft.com/fwlink/?LinkId=247608).  
  
## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы  
 **Операционная система конечного сервера:**  
  

-  Windows Server 2012 или Windows Server 2008 R2 (основных серверных компонентов и полная установка)  
  
 **Процессор конечного сервера:**  
  

-  на базе x64  
  
|Процессор исходного сервера|Операционная система исходного сервера|  
|-----|-----|  
|x86-или x 64-зависимости|Windows Server 2003 с пакетом обновления 2|  
|x86-или x 64-зависимости|Windows Server 2003 R2|  
|x86-или x 64-зависимости|Windows Server 2008, полная и установкой основных серверных компонентов|  
|на базе x64|Windows Server 2008 R2|  
|на базе x64|Вариант установки Server Core Windows Server 2008 R2|  
|на базе x64|Server Core и полная установка Windows Server 2012|  
  
> [!NOTE]
>  -   Версии операционных систем, перечисленных в приведенной выше таблице являются самыми ранними сочетаниями ОС и пакетов обновления, которые поддерживаются.  
> -   Foundation, Standard, Enterprise и Datacenter выпусков операционной системы Windows Server поддерживаются как исходный или конечный сервер.  
> -   Поддерживается миграция между физическими и виртуальными операционными системами.  
  
### <a name="supported-ad-fs-role-services-and-features"></a>Поддерживаемые службы ролей AD FS и компоненты  
 В следующей таблице описаны сценарии переноса служб ролей AD FS и их соответствующие параметры, описанные в этом руководстве.  
  
|От|В AD FS, установленного с Windows Server 2012|  
|----------|-----|  
|Сервера федерации AD FS 1.0, установленного с Windows Server 2003 R2|Миграция не поддерживается|  
|AD FS 1.0 федерации сервера прокси-сервера устанавливаются вместе с Windows Server 2003 R2|Миграция не поддерживается|  
|Агент на базе токенов AD FS 1.0 Windows устанавливаются вместе с Windows Server 2003 R2|Миграция не поддерживается|  
|AD FS 1.0 утверждениям агента, установленного с Windows Server 2003 R2)|Миграция не поддерживается|  
|Сервера федерации AD FS 1.1, установленного с Windows Server 2008 или Windows Server 2008 R2|Миграция не поддерживается|  
|AD FS 1.1 федерации сервера прокси-сервера устанавливаются вместе с Windows Server 2008 или Windows Server 2008 R2|Миграция не поддерживается|  
|Агент токены AD FS 1.1 Windows устанавливаются вместе с Windows Server 2008 или Windows Server 2008 R2|Миграция на том же сервере поддерживается, однако перенесенный агент на базе токенов AD FS Windows будет функционировать только 1.1 служба федерации AD FS, установленной с Windows Server 2008 или Windows Server 2008 R2. Дополнительные сведения см. в разделе:<br /><br /> [Перенос 1.1 веб-агенты AD FS](migrate-the-ad-fs-web-agent.md)<br /><br /> [Взаимодействие с AD FS 1.x](Interoperating-with-AD-FS-1.x.md)|  
|Агент AD FS 1.1 утверждениям, установленной с Windows Server 2008 или Windows Server 2008 R2)|Поддерживается миграция на том же сервере. Перенесенный 1.1 утверждениям веб-агент AD FS будет функционировать со следующими системами:<br /><br /> Службой федерации AD FS 1.1, установленного с Windows Server 2008 или Windows Server 2008 R2<br /><br /> Службой 2.0 федерации AD FS, установленной с Windows Server 2008 или Windows Server 2008 R2<br /><br /> Службой федерации AD FS, установленного с Windows Server 2012<br /><br /> Дополнительные сведения см. в разделе:<br /><br /> [Перенос 1.1 веб-агенты AD FS](migrate-the-ad-fs-web-agent.md)<br /><br /> [Взаимодействие с AD FS 1.x](Interoperating-with-AD-FS-1.x.md)|  
|Сервер федерации AD FS 2.0, установленной на Windows Server 2008 или Windows Server 2008 R2|Поддерживается миграция на том же сервере. Дополнительные сведения см. в разделе:<br /><br /> [Подготовка к миграции сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-server.md)<br /><br /> [Перенос сервера AD FS 2.0 Federation](migrate-the-ad-fs-fed-server.md)|  
|AD FS 2.0 федерации сервера прокси-сервер установлен на Windows Server 2008 или Windows Server 2008 R2|Поддерживается миграция на том же сервере.  Дополнительные сведения см. в разделе:<br /><br /> [Подготовка к миграции прокси-сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-proxy.md)<br /><br /> [Перенос прокси-сервера AD FS 2.0 Federation](migrate-the-ad-fs-2-fed-server-proxy.md)|  
  
## <a name="see-also"></a>См. также:  
 [Подготовка к миграции сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к миграции прокси-сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенос сервера AD FS 2.0 Federation](migrate-the-ad-fs-fed-server.md)   
 [Перенос прокси-сервера AD FS 2.0 Federation](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос 1.1 веб-агенты AD FS](migrate-the-ad-fs-web-agent.md)