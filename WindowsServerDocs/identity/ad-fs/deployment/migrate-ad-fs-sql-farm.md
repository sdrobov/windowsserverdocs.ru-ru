---
title: "Перенести ферму SQL server 2.0 федерации AD FS"
description: "Содержит сведения о миграции фермы AD FS 2.0 сервера SQL в Windows Server 2012"
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 8433219850793aa34b646a3bf14cba42d3de4988
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="migrate-an-ad-fs-20-wid-farm"></a>Перенести ферму внутренней базы данных Windows AD FS 2.0  
Этот документ содержит подробные сведения о миграции фермы SQL AD FS 2.0 в Windows Server 2012.


## <a name="migrate-a-sql-server-farm"></a>Миграция фермы SQL Server  
 Чтобы перенести ферму SQL Server до Windows Server 2012, выполните следующие действия.  
  
1.  Для каждого сервера в ферме SQL Server, просмотрите и выполните процедуры, описанные в [миграции фермы SQL Server](prepare-to-migrate-a-sql-server-farm.md).  
  
2.  Удалите из балансировщика нагрузки все серверы фермы SQL Server.  
  
3.  Обновление операционной системы на этом сервере фермы SQL Server с Windows Server 2008 R2 или Windows Server 2008 на Windows Server 2012. Дополнительные сведения см. в разделе [Установка Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx).  
  
> [!IMPORTANT]
>  В результате обновления ОС конфигурация AD FS на этом сервере была утрачена, а затем удаляется 2.0 серверной роли AD FS. Вместо этого установлена роль сервера Windows Server 2012 AD FS, но она не настроена. Необходимо вручную создать исходную конфигурацию AD FS и восстановить остальные параметры AD FS, чтобы завершить миграцию сервера федерации.  
  
4.  Создайте исходную конфигурацию AD FS на этом сервере фермы SQL Server с помощью командлетов AD FS Windows PowerShell для добавления сервера в существующую ферму.  
  
> [!IMPORTANT]
>  Чтобы создать исходную конфигурацию AD FS, при использовании SQL Server для хранения базы данных конфигурации AD FS, необходимо использовать Windows PowerShell.  

  - Откройте Windows PowerShell и выполните следующую команду: `$fscredential = Get-Credential`.  
  - Введите имя и пароль учетной записи службы, записанные в ходе подготовки к миграции фермы SQL Server.  
  - Выполните следующую команду: `Add-AdfsFarmNode -ServiceAccountCredential $fscredential -SQLConnectionString "Data Source=<Data Source>;Integrated Security=True"`, где `Data Source` — это значение источника данных в значении строки подключения политики магазина в следующем файле: `%programfiles%\Active Directory Federation Services 2.0\Microsoft.IdentityServer.Servicehost.exe.config`.  
  
5.  Добавьте сервер, который вы только что обновленный до Windows Server 2012 в балансировщик нагрузки.  
  
6.  Повторите шаги 2 – 6 для остальных узлов на ферме SQL Server.  
  
7.  Когда все серверы фермы SQL Server будут обновлены до Windows Server 2012, восстановите остальные пользовательские настройки AD FS, например хранилища настраиваемых атрибутов.  

## <a name="next-steps"></a>Дальнейшие действия
 [Подготовка к миграции сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к миграции прокси-сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенос сервера AD FS 2.0 Federation](migrate-the-ad-fs-fed-server.md)   
 [Перенос прокси-сервера AD FS 2.0 Federation](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос 1.1 веб-агенты AD FS](migrate-the-ad-fs-web-agent.md)



