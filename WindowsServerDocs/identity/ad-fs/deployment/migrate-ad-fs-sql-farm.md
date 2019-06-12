---
title: Миграция фермы AD FS 2.0 federation server SQL
description: Предоставляет сведения о миграции фермы AD FS 2.0 сервера SQL в Windows Server 2012
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: afecbf80d78688b66b2392647ea3195be95e9f54
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66445621"
---
# <a name="migrate-an-ad-fs-20-wid-farm"></a>Перенос в ферму AD FS 2.0 WID  
Этот документ содержит подробные сведения о переносе приложений в ферму AD FS 2.0 SQL в Windows Server 2012.


## <a name="migrate-a-sql-server-farm"></a>Миграция фермы SQL Server  
 Чтобы перенести ферму SQL Server до Windows Server 2012, выполните следующую процедуру.  
  
1.  Для каждого сервера в ферме SQL Server, просмотрите и выполните процедуры, описанные в [миграции фермы SQL Server](prepare-to-migrate-a-sql-server-farm.md).  
  
2.  Удалите из балансировщика нагрузки все серверы фермы SQL Server.  
  
3.  Обновление операционной системы на этом сервере фермы SQL Server из Windows Server 2008 R2 или Windows Server 2008 до Windows Server 2012. Дополнительные сведения см. в разделе [Установка Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx).  
  
> [!IMPORTANT]
>  В результате обновления операционной системы конфигурация AD FS на этом сервере была утрачена, а роли AD FS 2.0 сервера удаляется. Вместо этого установить роль сервера Windows Server 2012 AD FS, но она не настроена. Необходимо вручную создать исходную конфигурацию AD FS и восстановить остальные параметры AD FS, чтобы завершить миграцию сервера федерации.  
  
4. Создайте исходную конфигурацию AD FS на этом сервере фермы SQL Server с помощью командлетов AD FS Windows PowerShell, чтобы добавить сервер в существующую ферму.  
  
> [!IMPORTANT]
>  Чтобы создать исходную конфигурацию AD FS, если вы используете SQL Server для хранения базы данных конфигурации AD FS, необходимо использовать Windows PowerShell.  

  - Откройте Windows PowerShell и выполните следующую команду: `$fscredential = Get-Credential`.  
  - Введите имя и пароль учетной записи службы, записанные в ходе подготовки фермы серверов SQL к миграции.  
  - Выполните следующую команду: `Add-AdfsFarmNode -ServiceAccountCredential $fscredential -SQLConnectionString "Data Source=<Data Source>;Integrated Security=True"`, где `Data Source` — это значение источника данных в значении строки подключения хранилища политики в следующем файле: `%programfiles%\Active Directory Federation Services 2.0\Microsoft.IdentityServer.Servicehost.exe.config`.  
  
5. Добавьте сервер, обновленный до Windows Server 2012 в подсистему балансировки нагрузки.  
  
6. Повторите шаги 2 – 6 для остальных узлов в ферме SQL Server.  
  
7. Когда все серверы фермы SQL Server будут обновлены до Windows Server 2012, восстановите остальные пользовательские настройки AD FS, например хранилища настраиваемых атрибутов.  

## <a name="next-steps"></a>Следующие шаги
 [Подготовка к миграции сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к миграции прокси-сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенос сервера AD FS 2.0 Federation](migrate-the-ad-fs-fed-server.md)   
 [Перенос прокси-сервера AD FS 2.0 Federation](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)



