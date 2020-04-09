---
title: Перенос служб ролей для служб федерации Active Directory в Windows Server 2012 R2
description: Содержит инструкции по переносу службы AD FS в Windows Server 2012 R2.
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 6c2f9c8079eb2dfaf208c8835940351a925d0a16
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857507"
---
# <a name="migrate-active-directory-federation-services-role-services-to-windows-server-2012-r2"></a>Перенос служб ролей для служб федерации Active Directory в Windows Server 2012 R2
 В этом документе приведены инструкции по переносу следующих служб ролей в службы федерации Active Directory (AD FS) (AD FS), устанавливаемый вместе с Windows Server 2012 R2.  
  
-   Сервер федерации AD FS 2,0, установленный в Windows Server 2008 или Windows Server 2008 R2  
  
-   AD FS сервер федерации, установленный в Windows Server 2012  
  
## <a name="supported-migration-scenarios"></a>Поддерживаемые сценарии миграции  
 Инструкции по миграции в данном руководстве состоят из следующих задач:  
  
- Экспорт данных конфигурации AD FS 2,0 с сервера под Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012  
  
- Выполнение обновления операционной системы этого сервера на месте с Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012 до Windows Server 2012 R2. 
  
- Повторное создание исходной конфигурации AD FS и восстановление оставшихся параметров службы AD FS на этом сервере, на котором теперь выполняется роль AD FS Server, установленная вместе с Windows Server 2012 R2.  
  
  Данное руководство не содержит инструкций по переносу сервера, на котором выполняются несколько ролей. Если сервер выполняет несколько ролей, рекомендуется разработать специальную процедуру миграции для данной серверной среды c использованием информации из других руководств по переносу ролей. Руководства по миграции для дополнительных ролей можно найти на [портале по переносу ролей и компонентов на Windows Server](https://go.microsoft.com/fwlink/?LinkId=247608).  
  
### <a name="supported-operating-systems"></a>Поддерживаемые операционные системы  
 Операционная система целевого сервера:  
  
 Windows Server 2012 R2 (параметры ядра сервера и полная установка)  
  
 Процессор целевого сервера:  
  
 На базе архитектуры x64  
  
|Процессор исходного сервера|Операционная система исходного сервера|  
|-----------------------------|------------------------------------|  
|32-разрядный (x86) или 64-разрядный (x64)| Windows Server 2008, оба варианта установки: Full и Server Core|  
|На базе архитектуры x64|Windows Server 2008 R2|  
|На базе архитектуры x64|Вариант установки основных серверных компонентов Windows Server 2008 R2|  
|На базе архитектуры x64|Параметры Server Core и полная установка Windows Server 2012|  
  
> [!NOTE]
> - Версии операционных систем, представленные в предыдущей таблице, являются самыми ранними поддерживаемыми сочетаниями ОС и пакетов обновления.  
>   -   В качестве исходного или целевого сервера поддерживаются выпуски Foundation, Standard, Enterprise и Datacenter операционной системы Windows Server.  
>   -   Также поддерживается миграция между физическими и виртуальными операционными системами.  
  
### <a name="supported-ad-fs-role-services-and-features"></a>Поддерживаемые службы и функции ролей AD FS  
 В следующей таблице описаны сценарии миграции служб роли AD FS и соответствующие им параметры, описанные в этом разделе.  
  
|С|Установка AD FS с Windows Server 2012 R2|  
|----------|----------------------------------------------------------------------------------------------|  
|Сервер федерации AD FS 2,0, установленный в Windows Server 2008 или Windows Server 2008 R2|Поддерживается миграция на том же сервере. Дополнительные сведения см. в следующих разделах:<p> [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)<p> [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)|  
|AD FS сервер федерации, установленный в Windows Server 2012|Поддерживается миграция на том же сервере.  Дополнительные сведения см. в разделе:<p> [Подготовка к миграции сервера федерации AD FS](prepare-migrate-ad-fs-server-r2.md)<p> [Перенос сервера федерации AD FS](migrate-ad-fs-fed-server-r2.md)|  
  
## <a name="next-steps"></a>Следующие шаги
 [Подготовка к миграции сервера AD FS федерации](prepare-migrate-ad-fs-server-r2.md)   
 [Миграция AD FS сервера федерации](migrate-ad-fs-fed-server-r2.md)   
 [Перенос  прокси-сервера AD FS Федерации](migrate-fed-server-proxy-r2.md)  
 [Проверка AD FS миграции на Windows Server 2012 R2](verify-ad-fs-migration.md)