---
title: Перенос служб ролей для служб федерации Active Directory в Windows Server 2012
description: Инструкции по переносу службы AD FS в Windows Server 2012.
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 63dc9825b9c9b8a06d0946859e08a536589eb044
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66445698"
---
# <a name="migrate-active-directory-federation-services-role-services-to-windows-server-2012"></a>Перенос служб ролей для служб федерации Active Directory в Windows Server 2012

Ниже приведены инструкции по переносу следующих служб ролей для федерации служб Active Directory (AD FS) в Windows Server 2012:  
  
-   Агент токены AD FS 1.1 Windows и AD FS 1.1 по утверждениям агента, установленного с Windows Server 2008 или Windows Server 2008 R2  
  
-   Сервера федерации AD FS 2.0 и прокси-сервера AD FS 2.0 федерации устанавливается на Windows Server 2008 или Windows Server 2008 R2    
  
## <a name="supported-migration-scenarios"></a>Поддерживаемые сценарии миграции  
 Инструкции по переносу содержит следующие задачи:  
  
- Экспорт данных 2.0 конфигурации AD FS с сервера, на котором работает Windows Server 2008 или Windows Server 2008 R2  
  
- Обновление на месте операционной системы этого сервера с Windows Server 2008 или Windows Server 2008 R2 до Windows Server 2012.
  
- Восстановление первоначальной конфигурации AD FS и AD FS оставшихся параметров на этом сервере, где теперь выполняется роль сервера AD FS, которая устанавливается вместе с Windows Server 2012 служб.  
  
  Данное руководство не содержит инструкций по переносу сервера, на котором выполняются несколько ролей. Если сервер выполняет несколько ролей, рекомендуется разработать специальную процедуру миграции для данной серверной среды c использованием информации из других руководств по переносу ролей. Руководства по миграции для дополнительных ролей можно найти на [портале по переносу ролей и компонентов на Windows Server](https://go.microsoft.com/fwlink/?LinkId=247608).  
  
## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы  
 **Операционная система конечного сервера:**  
  

- Windows Server 2012 или Windows Server 2008 R2 (Server Core и выбрана полная установка)  
  
  **Процессор конечного сервера:**  
  

- На базе архитектуры x64  
  
|Процессор исходного сервера|Операционная система исходного сервера|  
|-----|-----|  
|32-разрядный (x86) или 64-разрядный (x64)|Windows Server 2003 с пакетом обновления 2|  
|32-разрядный (x86) или 64-разрядный (x64)|Windows Server 2003 R2|  
|32-разрядный (x86) или 64-разрядный (x64)|Windows Server 2008, полная установка и установка основных серверных компонентов|  
|На базе архитектуры x64|Windows Server 2008 R2|  
|На базе архитектуры x64|Вариант установки основных серверных компонентов Windows Server 2008 R2|  
|На базе архитектуры x64|Server Core полная установка и Windows Server 2012|  
  
> [!NOTE]
> - Версии операционных систем, представленные в предыдущей таблице, являются самыми ранними поддерживаемыми сочетаниями ОС и пакетов обновления.  
>   -   Выпуски Foundation, Standard, Enterprise и Datacenter операционной системы Windows Server поддерживаются в качестве источника или целевой сервер.  
>   -   Также поддерживается миграция между физическими и виртуальными операционными системами.  
  
### <a name="supported-ad-fs-role-services-and-features"></a>Поддерживаемые службы роли AD FS и возможности  
 В следующей таблице описаны сценарии переноса служб ролей AD FS и их соответствующие параметры, описанные в этом руководстве.  
  
|С|Для AD FS, установленные с Windows Server 2012|  
|----------|-----|  
|Сервера федерации AD FS 1.0, установленного с Windows Server 2003 R2|миграция не поддерживается|  
|AD FS 1.0 федерации сервера прокси-сервер устанавливается вместе с Windows Server 2003 R2|миграция не поддерживается|  
|AD FS 1.0 Windows токены агента, установленного с Windows Server 2003 R2|миграция не поддерживается|  
|AD FS 1.0 по утверждениям агента, установленного с Windows Server 2003 R2)|миграция не поддерживается|  
|Сервера федерации AD FS 1.1, установленного с Windows Server 2008 или Windows Server 2008 R2|миграция не поддерживается|  
|Устанавливается вместе с Windows Server 2008 или Windows Server 2008 R2 server прокси AD FS 1.1 федерации|миграция не поддерживается|  
|AD FS 1.1 Windows токены агента, установленного с Windows Server 2008 или Windows Server 2008 R2|Поддерживается миграция на одном сервере, но перенесенный агент на базе токенов Windows AD FS будет работать только со службой AD FS 1.1 федерации устанавливается вместе с Windows Server 2008 или Windows Server 2008 R2. Дополнительные сведения см. в следующих разделах:<br /><br /> [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)<br /><br /> [Взаимодействие с AD FS 1.x](Interoperating-with-AD-FS-1.x.md)|  
|AD FS 1.1 по утверждениям агента, установленного с Windows Server 2008 или Windows Server 2008 R2)|Поддерживается миграция на том же сервере. Перенесенный агент AD FS 1.1 по утверждениям web будет функционировать со следующими:<br /><br /> Службой федерации AD FS 1.1, установленного с Windows Server 2008 или Windows Server 2008 R2<br /><br /> Службы AD FS 2.0 federation, установленной на Windows Server 2008 или Windows Server 2008 R2<br /><br /> Службой федерации AD FS устанавливается вместе с Windows Server 2012<br /><br /> Дополнительные сведения см. в следующих разделах:<br /><br /> [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)<br /><br /> [Взаимодействие с AD FS 1.x](Interoperating-with-AD-FS-1.x.md)|  
|Сервера федерации AD FS 2.0, установленного в Windows Server 2008 или Windows Server 2008 R2|Поддерживается миграция на том же сервере. Дополнительные сведения см. в следующих разделах:<br /><br /> [Подготовка к переносу сервера федерации AD FS 2.0](prepare-to-migrate-ad-fs-fed-server.md)<br /><br /> [Перенос сервера федерации AD FS 2.0](migrate-the-ad-fs-fed-server.md)|  
|Устанавливается на Windows Server 2008 или Windows Server 2008 R2 server прокси AD FS 2.0 федерации|Поддерживается миграция на том же сервере.  Подробную информацию см. в следующих разделах:<br /><br /> [Подготовка к переносу прокси-сервера федерации AD FS 2.0](prepare-to-migrate-ad-fs-fed-proxy.md)<br /><br /> [Перенос прокси-сервера федерации AD FS 2.0](migrate-the-ad-fs-2-fed-server-proxy.md)|  
  
## <a name="see-also"></a>См. также  
 [Подготовка к миграции сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к миграции прокси-сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенос сервера AD FS 2.0 Federation](migrate-the-ad-fs-fed-server.md)   
 [Перенос прокси-сервера AD FS 2.0 Federation](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)