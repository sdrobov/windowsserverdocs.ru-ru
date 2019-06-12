---
title: Перенос служб ролей для служб федерации Active Directory в Windows Server 2012 R2
description: Инструкции по переносу службы AD FS в Windows Server 2012 R2.
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 34eab7d5e0325a4ad8268a900738eea30b944ebb
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66444567"
---
# <a name="migrate-active-directory-federation-services-role-services-to-windows-server-2012-r2"></a>Перенос служб ролей для служб федерации Active Directory в Windows Server 2012 R2
 Этот документ содержит инструкции по переносу следующих служб ролей в службах Active Directory Federation (AD FS), установленной в составе Windows Server 2012 R2:  
  
-   Сервера федерации AD FS 2.0, установленного в Windows Server 2008 или Windows Server 2008 R2  
  
-   Сервера федерации AD FS на Windows Server 2012  
  
## <a name="supported-migration-scenarios"></a>Поддерживаемые сценарии миграции  
 Инструкции по миграции в данном руководстве состоят из следующих задач:  
  
- Экспорт данных AD FS 2.0 конфигурации с сервера под управлением Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012  
  
- Обновление на месте операционной системы этого сервера с Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012 до Windows Server 2012 R2. 
  
- Восстановление первоначальной конфигурации AD FS и AD FS оставшихся параметров на этом сервере, где теперь выполняется роль сервера AD FS, которая устанавливается с Windows Server 2012 R2 служб.  
  
  Данное руководство не содержит инструкций по переносу сервера, на котором выполняются несколько ролей. Если сервер выполняет несколько ролей, рекомендуется разработать специальную процедуру миграции для данной серверной среды c использованием информации из других руководств по переносу ролей. Руководства по миграции для дополнительных ролей можно найти на [портале по переносу ролей и компонентов на Windows Server](https://go.microsoft.com/fwlink/?LinkId=247608).  
  
### <a name="supported-operating-systems"></a>Поддерживаемые операционные системы  
 Операционная система конечного сервера:  
  
 Windows Server 2012 R2 (Server Core и выбрана полная установка)  
  
 Процессор конечного сервера:  
  
 На базе архитектуры x64  
  
|Процессор исходного сервера|Операционная система исходного сервера|  
|-----------------------------|------------------------------------|  
|32-разрядный (x86) или 64-разрядный (x64)| Windows Server 2008, полная установка и установка основных серверных компонентов|  
|На базе архитектуры x64|Windows Server 2008 R2|  
|На базе архитектуры x64|Вариант установки основных серверных компонентов Windows Server 2008 R2|  
|На базе архитектуры x64|Server Core полная установка и Windows Server 2012|  
  
> [!NOTE]
> - Версии операционных систем, представленные в предыдущей таблице, являются самыми ранними поддерживаемыми сочетаниями ОС и пакетов обновления.  
>   -   Выпуски Foundation, Standard, Enterprise и Datacenter операционной системы Windows Server поддерживаются в качестве источника или целевой сервер.  
>   -   Также поддерживается миграция между физическими и виртуальными операционными системами.  
  
### <a name="supported-ad-fs-role-services-and-features"></a>Поддерживаемые службы роли AD FS и возможности  
 В следующей таблице описаны сценарии переноса служб ролей AD FS и их соответствующие параметры, описанные в этом руководстве.  
  
|С|Для AD FS, установленные с Windows Server 2012 R2|  
|----------|----------------------------------------------------------------------------------------------|  
|Сервера федерации AD FS 2.0, установленного в Windows Server 2008 или Windows Server 2008 R2|Поддерживается миграция на том же сервере. Дополнительные сведения см. в следующих разделах:<br /><br /> [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)<br /><br /> [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)|  
|Сервера федерации AD FS на Windows Server 2012|Поддерживается миграция на том же сервере.  Подробную информацию см. в следующих разделах:<br /><br /> [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)<br /><br /> [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)|  
  
## <a name="next-steps"></a>Следующие шаги
 [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)   
 [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)   
 [Миграция прокси-сервера федерации AD FS](migrate-fed-server-proxy-r2.md)   
 [Проверка переноса AD FS в Windows Server 2012 R2](verify-ad-fs-migration.md)