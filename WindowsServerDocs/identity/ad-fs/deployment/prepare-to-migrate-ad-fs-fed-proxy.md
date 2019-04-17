---
title: "Подготовка к миграции прокси-сервера AD FS 2.0 Federation"
description: "Содержит сведения о подготовке к миграции прокси-сервера AD FS в Windows Server 2012."
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: f207993580e6fd06c9ff185e58e5b7e81af60252
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="prepare-to-migrate-the-ad-fs-20-federation-server-proxy"></a>Подготовка к миграции прокси-сервера AD FS 2.0 Federation

Чтобы подготовиться к миграции прокси-сервер AD FS 2.0 federation server до Windows Server 2012, необходимо экспортировать и выполнить резервное копирование данных конфигурации AD FS с этого прокси-сервера.  Действия, описанные в этом разделе относятся к сценарию с одним сервером федерации прокси-сервера или нескольких прокси-серверов федерации.  
  
 Чтобы экспортировать данные конфигурации AD FS, выполните следующие задачи:  
  
-   [Шаг 1: Экспорт параметров службы прокси-сервера](#step-1-export-proxy-service-settings)  
  
-   [Шаг 2: Резервное копирование пользовательских настроек веб-страницы](#step-2-back-up-webpage-customizations)  
  
##  <a name="step-1-export-proxy-service-settings"></a>Шаг 1: Экспорт параметров службы прокси-сервера  
 Чтобы экспортировать параметры службы прокси-сервера федерации, выполните следующую процедуру.  
  
### <a name="to-export-proxy-service-settings"></a>Экспорт параметров службы прокси-сервера  
  
1.  Экспортируйте сертификат Secure Sockets Layer (SSL) и его закрытый ключ в PFX-файл. Дополнительные сведения см. в разделе [Экспорт части сертификата аутентификации сервера с закрытым ключом](export-the-private-key-portion-of-a-server-authentication-certificate.md).  
  
> [!NOTE]
>  Этот шаг является необязательным, так как этот сертификат сохраняется во время обновления операционной системы.  
  
2.  Экспортируйте свойства прокси-сервера AD FS 2.0 федерации в файл. Это можно сделать с помощью Windows PowerShell.  
  
Откройте Windows PowerShell и выполните следующую команду, чтобы добавить командлеты AD FS в сеанс Windows PowerShell: `PSH:>add-pssnapin “Microsoft.adfs.powershell”`. Затем выполните следующую команду для экспорта свойств прокси-сервера федерации в файл:`PSH:> Get-ADFSProxyProperties | out-file “.\proxyproperties.txt”`.  
  
3.  Убедитесь, что вам известны данные учетной записи администратора сервера федерации AD FS или учетной записи службы, под которой выполняется служба федерации AD FS.  Эти сведения необходимы для настройки доверия прокси-сервера.  
  
 При выполнении этого шага осуществляется сбор следующих сведений, необходимых для настройки прокси-сервера федерации AD FS:  
  
-   Имя службы федерации AD FS  
  
-   Имя учетной записи домена, которая необходима для настройки доверия прокси-сервера  
  
-   Адрес и порт прокси-сервера HTTP (если прокси-сервер HTTP между прокси-сервера федерации AD FS и серверами федерации AD FS)  
  
##  <a name="step-2-back-up-webpage-customizations"></a>Шаг 2: Резервное копирование пользовательских настроек веб-страницы  
 Чтобы выполнить резервное копирование пользовательских настроек веб-страницы, скопируйте веб-страниц прокси AD FS и **web.config** из каталога, сопоставленного виртуальному пути **«/ adfs/ls»** в службах IIS.  По умолчанию он находится в **%systemdrive%\inetpub\adfs\ls** каталога.  
  
## <a name="next-steps"></a>Дальнейшие действия
 [Подготовка к миграции сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к миграции прокси-сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенос сервера AD FS 2.0 Federation](migrate-the-ad-fs-fed-server.md)   
 [Перенос прокси-сервера AD FS 2.0 Federation](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос 1.1 веб-агенты AD FS](migrate-the-ad-fs-web-agent.md)