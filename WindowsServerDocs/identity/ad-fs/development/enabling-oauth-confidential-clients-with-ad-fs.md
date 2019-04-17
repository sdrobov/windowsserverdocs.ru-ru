---
ms.assetid: 5a64e790-6725-4099-aa08-8067d57c3168
title: "Создание приложения стороне сервера с помощью конфиденциальных клиентов OAuth с AD FS 2016"
description: 
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 175c683f9097aeba4c1f06e8671183476c98aa3f
ms.sourcegitcommit: c16a2bf1b8a48ff267e71ff29f18b5e5cda003e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="build-a-server-side-application-using-oauth-confidential-clients-with-ad-fs-2016"></a>Создание приложения стороне сервера с помощью конфиденциальных клиентов OAuth с AD FS 2016

>Область применения: Windows Server 2016

Построенная на начальной поддержку Oauth в AD FS в Windows Server 2012 R2, AD FS 2016 внедрена поддержка клиентов поддержания собственные секрет, например, приложение или служба выполняется на веб-сервере.  Такие клиенты называются конфиденциальных клиентов.    
Ниже приведен схема веб-приложение работает на веб-сервере, а также принятие конфиденциальных клиента для Служб федерации Active Directory.  
  
## <a name="pre-requisites"></a>Необходимые компоненты  
Ниже перечислены необходимые условия, которые необходимы перед выполнением этого документа. В этом документе предполагается, что была установлена AD FS и создала ферму AD FS.  
  
-   Подписка на Azure AD (бесплатная пробная версия подходит)  
  
-   Средства клиент GitHub  
  
-   AD FS в Windows Server 2016 TP4 или более поздней версии  
  
-   Visual Studio 2013 или более поздней версии.  
  
## <a name="create-an-application-group-in-ad-fs-2016"></a>Создание группы приложения в AD FS 2016  
Приведенные в следующем разделе описывается настройка группы приложений в AD FS 2016.  
  
#### <a name="create-the-application-group"></a>Создание группы приложений  
  
1.  В оснастку управления AD FS, щелкните правой кнопкой мыши на группами приложений и выберите **добавить группу приложения**.  
  
2.  В мастере группы приложения для имени введите **ADFSOAUTHCC** и в разделе **автономные приложения** выберите **серверное приложение или веб-сайт** шаблона.  Нажмите кнопку **Далее**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_2.PNG)  
  
3.  Копировать **идентификатор клиента** значение.  Он будет использоваться позже в качестве значения для **ida: ClientId** в файле web.config приложения.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_3.PNG)  
  
4.  Введите следующие данные для **URI перенаправления:** - **https://localhost:44323**.  Нажмите кнопку **добавить**. Нажмите кнопку **Далее**.  
  
5.  На **настроить учетные данные приложения** экрана, установите флажок в **создать общий секрет**и скопируйте секрет.  Это будет использоваться позже в качестве значения для **ida: AppKey** в файле web.config приложения.  Нажмите кнопку **Далее**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_4.PNG)  
  
6.  На **Сводка** нажмите кнопку **Далее**.  
  
7.  На **Complete** нажмите кнопку **закрыть**.  
  
8.  Теперь в новую группу приложений щелкните правой кнопкой мыши и выберите **свойства**.  
  
9. На **свойства ADFSOAUTHCC** щелкните **добавить приложение**.  
  
10. На **добавить новое приложение для примера приложения** выберите **веб-API**и нажмите кнопку **Далее**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_6.PNG)  
  
11. На **Настройка веб-API** введите следующие данные для **идентификатор** - **https://contoso.com/WebApp**.  Нажмите кнопку **добавить**. Нажмите кнопку **Далее**.  Это значение будет использоваться позже для **ida: GraphResourceId** в файле web.config приложения.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_9.PNG)  
  
12. На **выберите политики управления доступом** выберите **разрешить всем пользователям** и нажмите кнопку **Далее**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_7.PNG)  
  
13. На **Настройка разрешений приложения** экране, убедитесь, что**user_impersonation** выбран и нажмите кнопку **Далее**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_8.PNG)  
  
14. На **Сводка** нажмите кнопку **Далее**.  
  
15. На **Complete** нажмите кнопку **закрыть**.  
  
16. На **свойства ADFSOAUTHCC** щелкните **ОК**.  
  
## <a name="upgrade-the-database"></a>Обновление базы данных  
Visual Studio 2015 использовалась при создании этого пошагового руководства.   Чтобы получить в примере, работе с Visual Studio 2015 необходимо обновить файл базы данных.  Для этого используйте следующую процедуру.  
  
В этом разделе описывается, как загрузить этот пример веб-API и обновления базы данных в Visual Studio 2015.   Мы используем пример Azure AD, который является [здесь](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-useridentity).  
  
Чтобы скачать пример с проектом, используйте Git Bash и введите следующую команду:  
  
```  
git clone https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-useridentity.git  
```  
  
![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_10.PNG)  
  
#### <a name="to-upgrade-the-database-file"></a>Чтобы обновить файл базы данных  
  
1.  Откройте проект в Visual Studio, будет всплывающее окно, сообщающее о том, что приложение требует SQL Server 2102, экспресс-выпуск или необходимо будет обновить базу данных.  Нажмите кнопку ОК.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_12.PNG)  
  
2.  Далее компиляции приложения, установив сборки -> собрать решение в верхней части.  Это позволяет восстановить все пакеты NuGet.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_13.PNG)  
  
3.  Теперь в верхней части экрана, выбрать **представление** -> **обозреватель серверов**.  Как только откроется окно, в разделе **подключения к данным**, щелкните правой кнопкой мыши **DefaultConnection** и выберите **изменить подключение**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_14.PNG)  
  
4.  На **изменить подключение**выберите **Дополнительно**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_15.PNG)  
  
5.  В дополнительных свойствах найдите источника данных и используйте раскрывающийся список, чтобы изменить его из **(LocalDb\v11.0)** для **MSSQLLocalDB (LoaclDB)**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_16.PNG)  
  
6.  Нажмите кнопку ОК. Нажмите кнопку ОК.  Щелкните Да для обновления базы данных.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_17.PNG)  
  
7.  После завершения этого действия, более справа, скопировать значение в поле рядом с пунктом **строку подключения.**  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_18.PNG)  
  
8.  Теперь откройте файл Web.config и замените значение в connectionString со значением, куда вы скопировали выше.  Сохраните файл Web.config.  
  
    > [!NOTE]  
    > Указанные выше действия необходимы, чтобы мы могли получить новый connectionString.  В противном случае когда мы запускаем Update-Database ниже завершится ошибкой.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_19.PNG)  
  
9. В верхней части Visual Studio, выберите **представление** -> **другие окна** -> **консоль диспетчера пакетов**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_20.PNG)  
  
10. Внизу, в консоли диспетчера пакетов введите: `Enable-Migrations`и нажмите клавишу ВВОД.  
  
    > [!NOTE]  
    > Если сообщение об ошибке, информирующего о Enable-Migrations не распознается как командлет, введите EntityFramework Install-Package обновление EntityFramework.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_21.PNG)  
  
11. Внизу, в консоли диспетчера пакетов введите: `Add-Migration <anynamehere>`и нажмите клавишу ВВОД.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_22.PNG)  
  
12. Внизу, в консоли диспетчера пакетов введите: `Update-Database`и нажмите клавишу ВВОД.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_23.PNG)  
  
## <a name="modify-the-webapi-in-visual-studio"></a>Изменение WebApi в Visual Studio  
  
#### <a name="to-modify-the-sample-web-api"></a>Чтобы изменить веб-образец API  
  
1.  Откройте примера с помощью Visual Studio.  
  
2.  Откройте файл web.config.  Измените следующие значения:  
  
    -   IDA: ClientId - введите значение из #3 выше.  
  
    -   IDA: AppKey - введите значение из #5 выше.  
  
    -   IDA: GraphResourceId - введите значение от #11 выше.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_24.PNG)  
  
3.  Откройте файл Startup.Auth.cs под App_Start и внесите следующие изменения:  
  
    -   Закомментируйте следующие строки:  
  
        ```  
        //private static string aadInstance = ConfigurationManager.AppSettings["ida:AADInstance"];  
        //private static string tenant = ConfigurationManager.AppSettings["ida:Tenant"];  
        //public static readonly string Authority = String.Format(CultureInfo.InvariantCulture, aadInstance, tenant);  
        ```  
  
        ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_25.PNG)  
  
    -   Добавьте следующее в его место.  
  
        ```  
        public static readonly string Authority = "https://<your_fsname>/adfs";  
        ```  
  
        где < your_fsname > заменяется часть url службы федерации, например adfs.contoso.com DNS  
  
        ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_26.PNG)  
  
4.  Откройте файл UserProfileController.cs и внесите следующие изменения:  
  
    -   Закомментируйте следующее:  
  
        ```  
        //authContext = new AuthenticationContext(Startup.Authority, new TokenDbCache(userObjectID));  
        ```  
  
    -   Замените оба вхождений следующее:  
  
        ```  
        authContext = new AuthenticationContext(Startup.Authority, false, new TokenDbCache(userObjectID));  
        ```  
  
        ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_27.PNG)  
  
    -   Закомментируйте следующее:  
  
        ```  
        //authContext = new AuthenticationContext(Startup.Authority);  
        ```  
  
    -   Замените оба вхождений следующее:  
  
        ```  
        authContext = new AuthenticationContext(Startup.Authority, false);  
        ```  
  
        ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_28.PNG)  
  
    -   Теперь закомментируйте все экземпляры следующее:  
  
        ```  
        Uri redirectUri = new Uri(Request.Url.GetLeftPart(UriPartial.Authority.ToString() + "/OAuth");  
        ```  
  
    -   Замените все экземпляры следующее:  
  
        ```  
        Uri redirectUri = new Uri(Request.Url.GetLeftPart(UriPartial.Authority.ToString());  
        ```  
  
        ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_34.PNG)  
  
## <a name="test-the-solution"></a>Проверьте решение  
В этом разделе мы позволит проверить решение конфиденциальных клиента.  Используйте следующую процедуру, чтобы протестировать решение.  
  
#### <a name="testing-the-confidential-client-solution"></a>Проверка решения конфиденциальных клиента  
  
1.  В верхней части Visual Studio убедитесь, что установлен Internet Explorer, а затем нажмите кнопку зеленая стрелка.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_36.png)  
  
2.  Как только ASP.Net страницу, выберите команду **зарегистрировать**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_31.PNG)  
  
3.  Введите имя пользователя и пароль и нажмите кнопку **зарегистрировать**.  Это создает локальную учетную запись в базе данных SQL.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_31.PNG)  
  
4.  Уведомления теперь ASP.NET сайта появляется сообщение Hello bsimon!.  Нажмите кнопку **профиль**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_32.PNG)  
  
5.  Это отображает страницу без все сведения и указано, что мы должны щелкните здесь входа в систему.  Нажмите кнопку **здесь**.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_33.PNG)  
  
6.  Теперь предложит входа в систему для службы федерации Active Directory.  
  
    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_35.PNG)  
  
## <a name="next-steps"></a>Дальнейшие действия
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  

