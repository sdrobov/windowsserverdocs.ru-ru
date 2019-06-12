---
title: Настройка географической избыточности с помощью репликации SQL Server
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: active-directory-federation-services
ms.author: billmath
ms.assetId: 7b9f9a4f-888c-4358-bacd-3237661b1935
ms.openlocfilehash: 00880d06835fad08538f634fdf2868146fc23b1a
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66442927"
---
# <a name="setup-geographic-redundancy-with-sql-server-replication"></a>Настройка географической избыточности с помощью репликации SQL Server


> [!IMPORTANT]  
> Если вы хотите создать ферму AD FS и использовать SQL Server для хранения данных конфигурации, можно использовать SQL Server 2008 или более поздней версии.
  
Если вы используете SQL Server как база данных конфигурации AD FS, можно настроить географически\-избыточность для фермы AD FS с помощью репликации SQL Server. Географическая\-избыточности производит репликацию данных между двумя географически отдаленных сайтах, чтобы приложения можно переключаться с одного сайта на другой. Таким образом, в случае сбоя одного узла, вы сможете получить все данные конфигурации, доступные на втором сайте. Дополнительные сведения см. в разделе «SQL Server географической избыточности раздела» в [федерации сервера фермы с помощью SQL Server](../design/Federation-Server-Farm-Using-SQL-Server.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
Установка и Настройка фермы серверов SQL. Дополнительные сведения см. в разделе [ https://technet.microsoft.com/evalcenter/hh225126.aspx ](https://technet.microsoft.com/evalcenter/hh225126.aspx). На начальной SQL Server убедитесь, что служба агента SQL Server запущена и указан автоматический запуск.  
  
## <a name="create-the-second-replica-sql-server-for-geo-redundancy"></a>Создайте вторую \(реплики\) SQL Server для географически\-избыточности  
  
1. Установка SQL Server \(Дополнительные сведения см. в разделе [ https://technet.microsoft.com/evalcenter/hh225126.aspx ](https://technet.microsoft.com/evalcenter/hh225126.aspx). Скопируйте полученные файлы скрипта CreateDB.sql и SetPermissions.sql реплики SQL server.  
  
2. Убедитесь, что служба агента SQL Server запущена и указан автоматический запуск  
  
3. Запустите **Экспорт\-AdfsDeploymentSQLScript** на основном узле AD FS для создания файлов CreateDB.sql и SetPermissions.sql.  Например:`PS:\>Export-AdfsDeploymentSQLScript -DestinationFolder . –ServiceAccountName CONTOSO\gmsa1$`.  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql2.png)
  
4. Скопируйте скрипты на сервер-получатель.  Откройте скрипт CreateDB.sql в **SQL Management Studio** и нажмите кнопку **Execute**.
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql4.png)

5. Откройте скрипт SetPermissions.sql в **SQL Management Studio** и нажмите кнопку **Execute**.
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql6.png) 

   

> [!NOTE]
> Также можно использовать следующую команду в командной строке. 
> 
>    `c:\>sqlcmd –i CreateDB.sql`  
> 
>    `c:\>sqlcmd –i SetPermissions.sql` 
> 
> ## <a name="create-publisher-settings-on-the-initial-sql-server"></a>Создание настройки издателя на исходный SQL Server  
  
1. Из SQL Server Management studio в разделе **репликации**, щелкните правой кнопкой мыши **Локальные публикации** и выберите **новой публикации... ** 
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql7.png) </br>  

2. На экране мастера создания публикаций выберите **Далее**.</br>
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql8.png) </br> 
  
3. На **распространителя** странице выберите локальный сервер в качестве распространителя и нажмите кнопку **Далее**.  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql9.png) </br>   

4. На **моментального снимка** папки введите \\\SQL1\repldata вместо папки по умолчанию. \(Примечание. Возможно, для создания этой общей папке самостоятельно\).  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql10.png) </br>   
  
5. Выберите **AdfsConfigurationV3** базы данных публикации и нажмите кнопку **Далее**.  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql11.png) </br>
  
6. На **тип публикации**, выберите **публикация слиянием** и нажмите кнопку **Далее**.  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql12.png) </br>
  
7. На **типы подписчиков**, выберите **SQL Server 2008 или более поздней версии** и нажмите кнопку **Далее**.  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql13.png) </br> 

8. На **статьи** странице выберите **таблиц** узел, чтобы выбрать все таблицы, затем **отмены\-проверьте SyncProperties** таблицы \(, не следует репликация\)</br>
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql14.png) </br>    
  
9. На **статьи** выберите **определяемых пользователем функций** узел, чтобы выбрать все определяемые пользователем функции и нажмите кнопку **Далее**...  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql15.png) </br>    

10. На **проблемы в статьях** странице щелкните **Далее**.  
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql16.png) </br>   

11. На **фильтрация строк таблицы** щелкните **Далее**.  
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql17.png) </br>   
12. На **агент моментальных снимков** странице, выберите значения по умолчанию, Интерпретация и 14 дней, щелкните **Далее**.  
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql18.png) </br>   
    Может потребоваться создать учетную запись домена для агента SQL. Следуйте инструкциям в [имя входа SQL, Настройка учетной записи домена CONTOSO\\sqlagent](Set-up-Geographic-Redundancy-with-SQL-Server-Replication.md#sqlagent) создать имя входа SQL для этого нового пользователя AD и назначить специальные разрешения.  
  
13. На **Безопасность агента** щелкните **параметры безопасности** и введите имя пользователя\/пароль учетной записи домена \(не Управляемой\) создан для агента SQL и Нажмите кнопку **ОК**.  Нажмите кнопку **Далее**.  
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql19.png) </br>  

14. На **действия мастера** щелкните **Далее**.   
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql20.png) </br>

15. На **завершения работы мастера** странице, введите имя для публикации и нажмите кнопку **Готово**. 
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql21.png) </br>  

16. После создания публикации вы увидите состояние успеха.  Нажмите кнопку **Закрыть**.
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql22.png) </br>  

17. Назад в SQL Server Management Studio, щелкните правой кнопкой мыши новой публикации и нажмите кнопку **запустить монитор репликации**.  
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql23.png) </br> 
  
## <a name="create-subscription-settings-on-the-replica-sql-server"></a>Создание параметров подписки на реплике SQL Server  
Убедитесь, что создан настройки издателя на исходный SQL Server, как описано выше и затем выполните следующую процедуру:  
  
1. В реплике SQL Server, из SQL Server Management studio в разделе **репликации**, щелкните правой кнопкой мыши **Локальные подписки** и выберите **новую подписку...** . ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql24.png) </br>  

2. На **мастера создания подписки** щелкните **Далее**.
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql25.png) </br>   
  
3. На **публикации** странице, выберите издателя из раскрывающегося списка.  Разверните **AdfsConfigurationV3** выберите имя публикации, созданной ранее и нажмите кнопку **Далее**.  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql26.png) </br> 
  
4. На **расположение агента слияния** выберите **выполнять каждый агент на своем подписчике \(подписки по запросу\)**  \(по умолчанию\) и нажмите кнопку  **Далее**.  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql27.png) </br> Это, а также тип подписки ниже, определяет логики устранения конфликтов. \(Дополнительные сведения см. в разделе [обнаружение и разрешение конфликтов репликации слиянием](https://technet.microsoft.com/library/ms151191.aspx). </br>
 
5. На **подписчиков** выберите **AdfsConfigurationV3** базы данных подписчика и нажмите кнопку **Далее**.  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql28.png) </br> 
  
6. На **Безопасность агента слияния** щелкните **...**  и введите имя пользователя и пароль учетной записи домена \(не Управляемой\) созданный для агента SQL и нажмите кнопку с многоточием **Далее**.
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql30.png) </br> 
  
7. На **расписание синхронизации**, выберите **непрерывное выполнение** и нажмите кнопку **Далее**. 
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql31.png) </br> 
 
8. На **инициализация подписок**, нажмите кнопку **Далее**.  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql32.png) </br> 
  
9. На **тип подписки**, выберите **клиента** и нажмите кнопку **Далее**.  
  
   Связанные с этим проблемы описаны [здесь](https://technet.microsoft.com/library/ms151191.aspx) и [здесь](https://technet.microsoft.com/library/ms151170.aspx).  По сути мы берем разрешение конфликта простой «первый для Побеждает издатель», и нам не нужно повторно опубликовать на другие подписчики.  
   ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql33.png) </br>
   
10. На **действия мастера** странице **создания подписки** проверяется и нажмите кнопку **Далее**. 
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql34.png) </br>

11. На **завершения работы мастера** щелкните **Готово**. 
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql35.png) </br>

12. После завершения процесса создания подписки вы увидите, что успех. Нажмите кнопку **Закрыть**. 
    ![Настройка географической избыточности](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql36.png) </br>
  
## <a name="verify-the-process-of-initialization-and-replication"></a>Убедитесь, что процесс инициализации и репликации  
  
1.  На сервере-источнике SQL, правой кнопкой мыши\-щелкните **репликации** узел и нажмите кнопку **запустить монитор репликации**.  
  
2.  В **монитора репликации**, нажмите на публикацию.  
  
3.  На **все подписки** вкладке, щелкните правой кнопкой мыши и **Просмотр сведений о**.  
  
    Вы сможете см. в разделе большого числа записей в разделе **действия** для начальной репликации.  
  
4.  Кроме того, можно найти в разделе **агента SQL Server\\заданий** узел, чтобы увидеть задание\(s\) запланировано для выполнения операций публикации\/подписки.  Только локальные задания отображаются, поэтому обязательно проверьте на издателе и на подписчике, для устранения неполадок.  Справа\-щелкните задание и выберите **Просмотр журнала** для просмотра журнала выполнения и результатов.  
  
## <a name="sqlagent"></a>Настройка имени входа SQL для учетной записи домена CONTOSO\\sqlagent  
  
1.  Создайте новое имя входа на основной экземпляр и реплика SQL Server, под названием CONTOSO\\sqlagent \(имя нового пользователя домена, создания и настройки на **Безопасность агента** страницы в процедурам, описанным выше.\)  
  
2.  В SQL Server, правой кнопкой мыши\-щелкните имя входа, вы создали и выберите свойства, а затем в разделе **сопоставления** вкладку "," Карта имя пользователя для **AdfsConfiguration** и **AdfsArtifact**  баз данных с открытым и базой данных\_genevaservice ролей. Также сопоставляются с этим именем входа базы данных распространителя и добавить db\_роль владельца для распространения и adfsconfiguration таблиц.  Сделать это, применимую на основной и реплика SQL server. Дополнительные сведения см. в разделе [модель безопасности агента репликации](https://technet.microsoft.com/library/ms151868.aspx).  
  
3.  Присвойте соответствующие чтения учетной записи домена и разрешения на запись в общей папке, который настроен в качестве распространителя.  Убедитесь в том, что значение чтения и записи разрешения как на общих папок и разрешения локального файла.  
  
## <a name="configure-ad-fs-nodes-to-point-to-the-sql-server-replica-farm"></a>Настройка узла службы федерации Active Directory\(s\) указывал на ферме реплики SQL Server  
Теперь, когда вы настроили гео-избыточность, чтобы она указывала на ферме SQL Server реплики с помощью возможностей выпуска standard AD FS «присоединиться» фермы, либо в пользовательском Интерфейсе мастера конфигурации AD FS или Windows PowerShell можно настроить узлов фермы AD FS.  
  
Если вы используете пользовательский Интерфейс мастера конфигурации AD FS, выберите **Добавление сервера федерации в ферму серверов федерации**. **Не** выберите **создание первого сервера федерации в ферме серверов федерации**.  
  
Если вы используете Windows PowerShell, запустите **добавить\-AdfsFarmNode**. **Не** запуска **установить\-AdfsFarm**.  
  
При запросе укажите имя узла и экземпляра SQL Server, реплика **не** начальной SQL server.  
