---
title: Перенос служб ролей для служб федерации Active Directory в Windows Server 2012
description: Содержит инструкции по переносу службы AD FS в Windows Server 2012.
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 36d37eb2cc886d9831b995aa8cfdda16765994b8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857517"
---
# <a name="migrate-active-directory-federation-services-role-services-to-windows-server-2012"></a>Перенос служб ролей для служб федерации Active Directory в Windows Server 2012

Ниже приведены инструкции по миграции следующих служб ролей в службы федерации Active Directory (AD FS) (AD FS) в Windows Server 2012.  
  
-   Агент на основе маркеров Windows AD FS 1,1 и AD FS 1,1 с поддержкой утверждений, установленный с Windows Server 2008 или Windows Server 2008 R2  
  
-   Прокси-сервер AD FS 2,0 и сервер федерации AD FS 2,0, установленный на Windows Server 2008 или Windows Server 2008 R2    
  
## <a name="supported-migration-scenarios"></a>Поддерживаемые сценарии миграции  
 Инструкции по миграции содержат следующие задачи.  
  
- Экспорт данных конфигурации AD FS 2,0 с сервера под Windows Server 2008 или Windows Server 2008 R2  
  
- Выполнение обновления операционной системы этого сервера на месте с Windows Server 2008 или Windows Server 2008 R2 до Windows Server 2012.
  
- Повторное создание исходной конфигурации AD FS и восстановление оставшихся параметров службы AD FS на этом сервере, на котором теперь выполняется роль AD FS Server, установленная вместе с Windows Server 2012.  
  
  Данное руководство не содержит инструкций по переносу сервера, на котором выполняются несколько ролей. Если сервер выполняет несколько ролей, рекомендуется разработать специальную процедуру миграции для данной серверной среды c использованием информации из других руководств по переносу ролей. Руководства по миграции для дополнительных ролей можно найти на [портале по переносу ролей и компонентов на Windows Server](https://go.microsoft.com/fwlink/?LinkId=247608).  
  
## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы  
 **Операционная система целевого сервера:**  
  

- Windows Server 2012 или Windows Server 2008 R2 (параметры Server Core и полная установка)  
  
  **Процессор целевого сервера:**  
  

- На базе архитектуры x64  
  
|Процессор исходного сервера|Операционная система исходного сервера|  
|-----|-----|  
|32-разрядный (x86) или 64-разрядный (x64)|Windows Server 2003 с пакетом обновления 2|  
|32-разрядный (x86) или 64-разрядный (x64)|Windows Server 2003 R2|  
|32-разрядный (x86) или 64-разрядный (x64)|Windows Server 2008, оба варианта установки: Full и Server Core|  
|На базе архитектуры x64|Windows Server 2008 R2|  
|На базе архитектуры x64|Вариант установки основных серверных компонентов Windows Server 2008 R2|  
|На базе архитектуры x64|Параметры Server Core и полная установка Windows Server 2012|  
  
> [!NOTE]
> - Версии операционных систем, представленные в предыдущей таблице, являются самыми ранними поддерживаемыми сочетаниями ОС и пакетов обновления.  
>   -   В качестве исходного или целевого сервера поддерживаются выпуски Foundation, Standard, Enterprise и Datacenter операционной системы Windows Server.  
>   -   Также поддерживается миграция между физическими и виртуальными операционными системами.  
  
### <a name="supported-ad-fs-role-services-and-features"></a>Поддерживаемые службы и функции ролей AD FS  
 В следующей таблице описаны сценарии миграции служб роли AD FS и соответствующие им параметры, описанные в этом разделе.  
  
|С|Установка AD FS с Windows Server 2012|  
|----------|-----|  
|Сервер федерации AD FS 1,0, установленный с Windows Server 2003 R2|миграция не поддерживается|  
|Прокси-сервер AD FS 1,0 Федерации, установленный с Windows Server 2003 R2|миграция не поддерживается|  
|AD FS 1,0 агент на основе маркеров Windows, установленный с Windows Server 2003 R2|миграция не поддерживается|  
|AD FS 1,0 агент с поддержкой утверждений, установленный с Windows Server 2003 R2)|миграция не поддерживается|  
|Сервер федерации AD FS 1,1, установленный с Windows Server 2008 или Windows Server 2008 R2|миграция не поддерживается|  
|AD FS 1,1 прокси-сервер федерации, установленный с Windows Server 2008 или Windows Server 2008 R2|миграция не поддерживается|  
|AD FS 1,1 агент на основе маркеров Windows, установленный с Windows Server 2008 или Windows Server 2008 R2|Миграция на одном сервере поддерживается, но перенесенный AD FS агент на основе маркеров Windows будет работать только со службой федерации AD FS 1,1, установленной с Windows Server 2008 или Windows Server 2008 R2. Дополнительные сведения см. в следующих разделах:<p> [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)<p> [Взаимодействие с AD FS 1.x](Interoperating-with-AD-FS-1.x.md)|  
|AD FS 1,1 агент с поддержкой утверждений, установленный с Windows Server 2008 или Windows Server 2008 R2)|Поддерживается миграция на том же сервере. Перенесенный веб-агент AD FS 1,1 с поддержкой утверждений будет работать следующим образом:<p> Служба федерации AD FS 1,1, установленная с Windows Server 2008 или Windows Server 2008 R2<p> Служба федерации AD FS 2,0, установленная в Windows Server 2008 или Windows Server 2008 R2<p> AD FS Служба федерации, установленная с Windows Server 2012<p> Дополнительные сведения см. в следующих разделах:<p> [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)<p> [Взаимодействие с AD FS 1.x](Interoperating-with-AD-FS-1.x.md)|  
|Сервер федерации AD FS 2,0, установленный в Windows Server 2008 или Windows Server 2008 R2|Поддерживается миграция на том же сервере. Дополнительные сведения см. в следующих разделах:<p> [Подготовка к переносу сервера федерации AD FS 2.0](prepare-to-migrate-ad-fs-fed-server.md)<p> [Перенос сервера федерации AD FS 2.0](migrate-the-ad-fs-fed-server.md)|  
|Прокси-сервер AD FS 2,0 Федерации, установленный в Windows Server 2008 или Windows Server 2008 R2|Поддерживается миграция на том же сервере.  Дополнительные сведения см. в разделе:<p> [Подготовка к переносу прокси-сервера федерации AD FS 2.0](prepare-to-migrate-ad-fs-fed-proxy.md)<p> [Перенос прокси-сервера федерации AD FS 2.0](migrate-the-ad-fs-2-fed-server-proxy.md)|  
  
## <a name="see-also"></a>См. также  
 [Подготовка к переносу сервера федерации AD FS 2,0](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к миграции прокси-сервера AD FS 2,0 федерации](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенесите сервер федерации AD FS 2,0](migrate-the-ad-fs-fed-server.md)   
 [Перенесите прокси-сервер AD FS 2,0 федерации](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)