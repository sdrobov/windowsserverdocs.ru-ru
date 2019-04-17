---
title: "Перенос служб ролей для служб федерации Active Directory в Windows Server 2012 R2"
description: "Инструкции по переносу службы AD FS Windows Server 2012 R2."
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 478729a7b6560beba5f04a1a15ad035561ad31f0
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="migrate-active-directory-federation-services-role-services-to-windows-server-2012-r2"></a>Перенос служб ролей для служб федерации Active Directory в Windows Server 2012 R2
 Этот документ содержит инструкции по переносу следующих служб ролей Active Directory службы федерации (AD FS), устанавливается вместе с Windows Server 2012 R2:  
  
-   Сервер федерации AD FS 2.0, установленной на Windows Server 2008 или Windows Server 2008 R2  
  
-   Сервера федерации AD FS, установленного в Windows Server 2012  
  
## <a name="supported-migration-scenarios"></a>Поддерживаемые сценарии миграции  
 Инструкции по миграции в данном руководстве состоят из следующих задач:  
  
-   Экспорт данных AD FS 2.0 конфигурации с сервера под управлением Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012  
  
-   Обновление на месте операционной системы этого сервера с Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012 на Windows Server 2012 R2. 
  
-   Восстановление первоначальной конфигурации AD FS и остальных Служб федерации Active Directory параметров служб на этом сервере, где теперь выполняется роль сервера AD FS, установленная с Windows Server 2012 R2.  
  
 Это руководство не содержит инструкций по миграции сервера, на котором выполняется несколько ролей. Если на сервере выполняется несколько ролей, рекомендуется разработать специальную процедуру миграции для данной серверной среды с использованием информации из других руководств по миграции ролей. Руководства по миграции для дополнительных ролей доступны на [портал миграции Windows Server](https://go.microsoft.com/fwlink/?LinkId=247608).  
  
### <a name="supported-operating-systems"></a>Поддерживаемые операционные системы  
 Операционная система конечного сервера:  
  
 Windows Server 2012 R2 (основных серверных компонентов и полная установка)  
  
 Процессор конечного сервера:  
  
 на базе x64  
  
|Процессор исходного сервера|Операционная система исходного сервера|  
|-----------------------------|------------------------------------|  
|x86-или x 64-зависимости| Windows Server 2008, полная и установкой основных серверных компонентов|  
|на базе x64|Windows Server 2008 R2|  
|на базе x64|Вариант установки Server Core Windows Server 2008 R2|  
|на базе x64|Server Core и полная установка Windows Server 2012|  
  
> [!NOTE]
>  -   Версии операционных систем, перечисленных в приведенной выше таблице являются самыми ранними сочетаниями ОС и пакетов обновления, которые поддерживаются.  
> -   Foundation, Standard, Enterprise и Datacenter выпусков операционной системы Windows Server поддерживаются как исходный или конечный сервер.  
> -   Поддерживается миграция между физическими и виртуальными операционными системами.  
  
### <a name="supported-ad-fs-role-services-and-features"></a>Поддерживаемые службы ролей AD FS и компоненты  
 В следующей таблице описаны сценарии переноса служб ролей AD FS и их соответствующие параметры, описанные в этом руководстве.  
  
|От|В AD FS, установленного с Windows Server 2012 R2|  
|----------|----------------------------------------------------------------------------------------------|  
|Сервер федерации AD FS 2.0, установленной на Windows Server 2008 или Windows Server 2008 R2|Поддерживается миграция на том же сервере. Дополнительные сведения см. в разделе:<br /><br /> [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)<br /><br /> [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)|  
|Сервера федерации AD FS, установленного в Windows Server 2012|Поддерживается миграция на том же сервере.  Дополнительные сведения см. в разделе:<br /><br /> [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)<br /><br /> [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)|  
  
## <a name="next-steps"></a>Дальнейшие действия
 [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)   
 [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)   
 [Миграция прокси-сервера федерации AD FS](migrate-fed-server-proxy-r2.md)   
 [Проверка переноса AD FS в Windows Server 2012 R2](verify-ad-fs-migration.md)