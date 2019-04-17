---
title: "Настройка географической избыточности с помощью репликации SQL Server"
description: 
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: active-directory-federation-services
ms.author: billmath
ms.assetId: 7b9f9a4f-888c-4358-bacd-3237661b1935
ms.openlocfilehash: a9f29c1eb19a8241eac5afb5c87581e6c988c3c8
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="setup-geographic-redundancy-with-sql-server-replication"></a>Настройка географической избыточности с помощью репликации SQL Server

>Область применения: Windows Server 2016, Windows Server 2012 R2

> [!IMPORTANT]  
> Если вы хотите создать ферму AD FS и использовать SQL Server для хранения данных конфигурации, можно использовать SQL Server 2008 или более поздней версии.
  
При использовании SQL Server в качестве базы данных конфигурации AD FS можно настроить geo\ избыточности для фермы AD FS с помощью репликации SQL Server. Избыточность Geo\ репликации данных между двумя сайтами географически удаленном, чтобы приложения можно переключиться с одного узла на другой. Таким образом, в случае сбоя одного узла, вы сможете получить все доступные данные конфигурации на втором сайте. Дополнительные сведения см. раздел «географической избыточности для SQL Server» в [федерации сервер фермы с помощью SQL Server](../design/Federation-Server-Farm-Using-SQL-Server.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
Установка и Настройка фермы серверов SQL. Дополнительные сведения см. в разделе [https://technet.microsoft.com/evalcenter/hh225126.aspx](https://technet.microsoft.com/evalcenter/hh225126.aspx). На начальной SQL Server убедитесь, что служба агента SQL Server запущена и запускается автоматически.  
  
## <a name="create-the-second-replica-sql-server-for-geo-redundancy"></a>Создание второй \(replica\) SQL Server для обеспечения избыточности geo\  
  
1.  Установка SQL Server \ (Дополнительные сведения см. в разделе [https://technet.microsoft.com/evalcenter/hh225126.aspx](https://technet.microsoft.com/evalcenter/hh225126.aspx). Скопируйте полученные файлы сценарий CreateDB.sql и SetPermissions.sql реплики SQL server.  
  
2.  Убедитесь, что запущена служба агента SQL Server и запускается автоматически  
  
3.  Запустите **этого AdfsDeploymentSQLScript** на первичном узле AD FS для создания файлов CreateDB.sql и SetPermissions.sql.  Например:`PS:\>Export-AdfsDeploymentSQLScript -DestinationFolder . –ServiceAccountName CONTOSO\gmsa1$`.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql2.png)
  
4.  Копирование сценариев сервера-получателя.  Откройте сценарий CreateDB.sql в **SQL Management Studio** и нажмите кнопку **выполнение**.
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql4.png)

5. Откройте SetPermissions.sql сценария в в **SQL Management Studio** и нажмите кнопку **выполнение**.
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql6.png) 

   

>[!NOTE]
>Можно также использовать следующие из командной строки. 
>
>    `c:\>sqlcmd –i CreateDB.sql`  
>  
>    `c:\>sqlcmd –i SetPermissions.sql` 
> 
## <a name="create-publisher-settings-on-the-initial-sql-server"></a>Создание параметров издателя на исходный сервер SQL Server  
  
1.  В SQL Server Management Studio в разделе **репликации**, щелкните правой кнопкой мыши **Локальные публикации** и выберите **публикацию... **
![ Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql7.png) </br>  

2.  На экране мастер создания публикаций щелкните **Далее**.</br>
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql8.png) </br> 
  
3.  На **распространителя** выберите локальный сервер в качестве распространителя и нажмите кнопку **Далее**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql9.png) </br>   

4.  На **моментального снимка** папки введите \\\SQL1\repldata вместо папку по умолчанию. \ (Примечание: может понадобиться создание yourself\ этого общего ресурса).  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql10.png) </br>   
  
5.  Выберите **AdfsConfigurationV3** базы данных публикации и нажмите кнопку **Далее**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql11.png) </br>
  
6.  На **тип публикации**, выберите **слиянием** и нажмите кнопку **Далее**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql12.png) </br>
  
7.  На **типы подписчиков**, выберите **SQL Server 2008 или более поздней версии** и нажмите кнопку **Далее**.  
 ![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql13.png) </br> 

8.  На **статьи** выберите **таблиц** узел, чтобы выбрать все таблицы, затем **проверки SyncProperties** таблице \ (это не должен быть replicated\)</br>
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql14.png) </br>    
  
9.  На **статьи** выберите **пользовательских функций** узел для выбора всех пользовательских функций и нажмите кнопку **Далее**..  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql15.png) </br>    

10. На **статья проблемы** щелкните **Далее**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql16.png) </br>   

11. На **фильтрация строк таблицы** щелкните **Далее**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql17.png) </br>   
12. На **агента моментальных снимков** страницы, выберите настройки по умолчанию, Интерпретация и 14 дней, нажмите кнопку **Далее**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql18.png) </br>   
Может потребоваться создать учетную запись домена для данного агента SQL. Используйте действия, описанные в [имени входа SQL, настройте для учетной записи домена CONTOSO\\sqlagent](Set-up-Geographic-Redundancy-with-SQL-Server-Replication.md#sqlagent) создать имя входа SQL для этого нового пользователя AD и назначить специальные разрешения.  
  
13. На **Безопасность агента** щелкните **параметры безопасности** и username\ и пароль учетной записи домена \ (не GMSA\) создан для агента SQL и нажмите кнопку **ОК**.  Нажмите кнопку **Далее**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql19.png) </br>  

14. На **действия мастера** щелкните **Далее**.   
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql20.png) </br>

15. На **завершения работы мастера** введите имя для публикации и нажмите кнопку **Готово**. 
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql21.png) </br>  

16. После создания публикации вы увидите, что состояние успешно.  Нажмите кнопку **закрыть**.
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql22.png) </br>  

17. Вернитесь в SQL Server Management Studio, щелкните правой кнопкой мыши новую публикацию и нажмите кнопку **запустить монитор репликации**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql23.png) </br> 
  
## <a name="create-subscription-settings-on-the-replica-sql-server"></a>Создайте параметры подписки на репликации SQL Server  
Убедитесь, что создана параметров издателя на исходный сервер SQL Server, как описано выше и затем выполните следующую процедуру.  
  
1.  На репликации SQL Server в SQL Server Management studio в разделе **репликации**, щелкните правой кнопкой мыши **Локальные подписки** и выберите **новой подписки... **. ![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql24.png) </br>  

2.  На **мастер создания подписки** щелкните **Далее**.
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql25.png) </br>   
  
3.  На **публикации** выберите издателя из раскрывающегося списка.  Разверните **AdfsConfigurationV3** выберите имя публикации, созданной выше и нажмите кнопку **Далее**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql26.png) </br> 
  
4.  На **расположение агента слияния** выберите **выполнять каждый агент на его подписчика \(pull subscriptions\)** \(the default\) и нажмите кнопку **Далее**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql27.png) </br> Это, а также тип подписки ниже, определяет логику разрешения конфликтов. \ (Дополнительные сведения см. в разделе [Выявление и устранение конфликтов репликации слиянием](https://technet.microsoft.com/library/ms151191.aspx). </br>
 
5.  На **подписчиков** выберите **AdfsConfigurationV3** подписчика базы данных и нажмите кнопку **Далее**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql28.png) </br> 
  
6.  На **Безопасность агента слияния** щелкните **... ** и введите имя пользователя и пароль учетной записи домена \ (не GMSA\) создать для агента SQL, используя поле многоточия и и выберите **Далее**.
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql30.png) </br> 
  
7.  На **расписание синхронизации**, выберите **запуска постоянно** и нажмите кнопку **Далее**. 
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql31.png) </br> 
 
8.  На **инициализация подписок**, нажмите кнопку **Далее**.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql32.png) </br> 
  
9.  На **тип подписки**, выберите **клиента** и нажмите кнопку **Далее**.  
  
    Описаны последствия этого [здесь](https://technet.microsoft.com/library/ms151191.aspx) и [здесь](https://technet.microsoft.com/library/ms151170.aspx).  По существу мы принимаем разрешение конфликта простой «сначала wins издателя», и нам не нужно повторно для других подписчиков.  
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql33.png) </br>
   
10. На **действия мастера** Убедитесь **создания подписки** проверяется и нажмите кнопку **Далее**. 
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql34.png) </br>

11. На **завершения работы мастера** щелкните **Готово**. 
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql35.png) </br>

12. После завершения процесса создания подписки, вы должны увидеть успех. Нажмите кнопку **закрыть**. 
![Настройка географической избыточности](media\Set-up-Geographic-Redundancy-with-SQL-Server-Replication\sql36.png) </br>
  
## <a name="verify-the-process-of-initialization-and-replication"></a>Убедитесь, что процесс инициализации и репликации  
  
1.  На основном сервере SQL щелкните правой кнопкой мыши **репликации** и выберите команду **запустить монитор репликации**.  
  
2.  В **монитор репликации**, щелкните публикацию.  
  
3.  На **все подписки** вкладку, щелкните правой кнопкой мыши и **сведения о представлении**.  
  
    Можно в разделе много записей в разделе **действия** для начальной репликации.  
  
4.  Кроме того, можно найти в разделе **SQL Server Agent\\Jobs** узел, чтобы увидеть job\(s\) запланирована для выполнения операций publication\ и подписки.  Только локальный задания отображаются, поэтому убедитесь, что проверка на издателем и подписчиком для устранения неполадок.  Щелкните правой кнопкой мыши задание и выберите **просмотреть журнал** просмотреть журнал выполнения и результаты.  
  
## <a name="sqlagent"></a>Настройка имени входа SQL для учетной записи домена CONTOSO\\sqlagent  
  
1.  Создайте учетную запись для входа на основной и реплика SQL Server, называется CONTOSO\\sqlagent \ (имя нового пользователя домена создаются и настраиваются на **Безопасность агента** страницы в описанных выше процедур. \)  
  
2.  В SQL Server, щелкните правой кнопкой мыши имя входа создан, а затем выбрать свойства, в разделе **сопоставления пользователей** вкладку, сопоставить имя пользователя для **AdfsConfiguration** и **AdfsArtifact** баз данных с помощью общедоступных и db\_genevaservice ролей. Также сопоставить это имя входа для базы данных распространителя и добавьте роль db\_owner для распространения и adfsconfiguration таблицы.  Для этого применяется на основной и реплика SQL server. Дополнительные сведения см. в разделе [модель безопасности агента репликации](https://technet.microsoft.com/library/ms151868.aspx).  
  
3.  Соответствующий чтение учетной записи домена и разрешения на запись в общую папку, настроен как распространитель.  Убедитесь, что значение чтения и записи разрешения на разрешения для общей папки и разрешения для локальных файлов.  
  
## <a name="configure-ad-fs-nodes-to-point-to-the-sql-server-replica-farm"></a>Настройка node\(s\) Служб федерации Active Directory, чтобы он указывал на ферме SQL Server реплики  
После того как вы настроили географическая избыточность, узлов фермы AD FS можно настроить для указания реплики фермы SQL Server standard AD FS «соединение» фермы возможности использования, либо из пользовательского интерфейса мастера конфигурации AD FS или с помощью Windows PowerShell.  
  
Если вы используете пользовательский Интерфейс мастера конфигурации AD FS, выберите **добавить сервер федерации в ферме серверов федерации**. **НЕ выбирайте** выберите **создание первого сервера федерации в ферме серверов федерации**.  
  
Если вы используете Windows PowerShell, запустите **надстройку AdfsFarmNode**. **НЕ выбирайте** запуска **Install\ AdfsFarm**.  
  
При появлении запроса, введите имя узла и экземпляра реплики базы данных SQL Server, **не** начальной SQL server.  
