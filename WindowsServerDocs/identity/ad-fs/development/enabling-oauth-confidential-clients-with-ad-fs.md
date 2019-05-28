---
ms.assetid: 5a64e790-6725-4099-aa08-8067d57c3168
title: Создание приложения с помощью конфиденциальных клиентов OAuth с AD FS 2016 или более поздней версии на стороне сервера
description: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 220b0b72734d1456e3cf877ebc2ff267a7dd56ad
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66190648"
---
# <a name="build-a-server-side-application-using-oauth-confidential-clients-with-ad-fs-2016-or-later"></a>Создание приложения с помощью конфиденциальных клиентов OAuth с AD FS 2016 или более поздней версии на стороне сервера


AD FS 2016 и более поздние версии поддерживают клиентов, способных сохранять свои собственные секрета, например приложения или службы, на веб-сервере.  Эти клиенты известны как конфиденциальные.
Ниже приведена схема веб-приложения на веб-сервере и работа в качестве конфиденциального клиента к AD FS:  

## <a name="pre-requisites"></a>Предварительные требования  
Ниже приведен список предварительных требований, которые требуются перед выполнением этого документа. В этом документе предполагается, что AD FS был установлен.  

-   Клиентские средства GitHub  

-   AD FS в Windows Server 2016 TP4 или более поздней версии  

-   Visual Studio 2013 или более поздней версии.  

## <a name="create-an-application-group-in-ad-fs-2016-or-later"></a>Создание группы приложений в AD FS 2016 или более поздней версии
В следующем разделе описываются способы настройки приложения в AD FS 2016 или более поздней версии.  

#### <a name="create-the-application-group"></a>Создание группы приложений  

1.  В оснастке управления AD FS, щелкните правой кнопкой мыши на группы приложений и выберите **добавить группу приложений**.  

2.  В мастере группы приложений для **имя** введите **ADFSOAUTHCC** и в разделе **клиентские / серверные приложения** выберите **серверного приложения доступ к веб-API** шаблона.  Нажмите кнопку **Далее**.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_2.PNG)  

3.  Копировать **идентификатор клиента** значение.  Он будет использоваться позже в качестве значения для **ida: ClientId** в файле web.config приложения.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_3.PNG)  

4.  Введите следующую команду для **URI перенаправления:**  -  **https://localhost:44323** .  Нажмите кнопку **Добавить**. Нажмите кнопку **Далее**.  

5.  На **настроить учетные данные приложения** экрана, установите флажок в **создать общий секрет** и скопируйте секрет.  Он будет использоваться позже в качестве значения для **ida: ClientSecret** в файле web.config приложения.  Нажмите кнопку **Далее**.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_4.PNG)   

6. На **настроить веб-API** экрана, введите следующую команду для **идентификатор** -  **https://contoso.com/WebApp** .  Нажмите кнопку **Добавить**. Нажмите кнопку **Далее**.  Это значение будет использоваться позднее для **ida: GraphResourceId** в файле web.config приложения.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_9.PNG)  

7. На **применяются политики управления доступом** выберите **разрешение для каждого** и нажмите кнопку **Далее**.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_7.PNG)  

8. На **Настройка разрешений приложения** экрана, убедитесь, что **openid** и **user_impersonation** установлены и нажмите кнопку **Далее**.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_8.PNG)  

9. На **Сводка** щелкните **Далее**.  

10. На **завершить** щелкните **закрыть**.  

## <a name="upgrade-the-database"></a>Обновление базы данных  
Visual Studio 2015, использованный при создании этого пошагового руководства.   Чтобы получить пример, работа с Visual Studio 2015 необходимо обновить файл базы данных.  Выполните следующие действия.  

В этом разделе описывается скачать пример веб-API и обновить базу данных в Visual Studio 2015.   Мы будем использовать пример Azure AD, [здесь](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-useridentity).  

Загрузите пример проекта, использование Git Bash и введите следующую команду:  

```  
git clone https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-useridentity.git  
```  

![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_10.PNG)  

#### <a name="to-upgrade-the-database-file"></a>Чтобы обновить файл базы данных  

1.  Откройте проект в Visual Studio, будет существовать всплывающее окно, информирующее о том, что приложению требуется SQL Server 2012 Express, или необходимо обновить базу данных.  Нажмите кнопку ОК.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_12.PNG)  

2.  Далее компиляции приложения, выбрав построения "->" Построить решение вверху.  Это позволит восстановить все пакеты NuGet.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_13.PNG)  

3.  Теперь в верхней, выберите **представление** -> **обозревателя серверов**.  Когда откроется окно, в разделе **подключения к данным**, щелкните правой кнопкой мыши **DefaultConnection** и выберите **Изменение подключения**.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_14.PNG)  

4.  На **Изменение подключения**в разделе **имя файла базы данных (новой или существующей)** выберите **Обзор** и предоставить **path\filename.mdf**. Нажмите кнопку **Да** на диалоговое окно.

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_6.PNG)

5.  На **Изменение подключения**выберите **Дополнительно**.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_15.PNG)  

6.  В свойствах, найдите источник данных и используйте раскрывающийся список, чтобы изменить его из **(LocalDb\v11.0)** для **(LocalDB) \MSSQLLocalDB**.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_16.PNG)  

7.  Нажмите кнопку ОК. Нажмите кнопку ОК.  Нажмите "Да", чтобы обновить базу данных.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_17.PNG)  

8.  После завершения этой операции, более чем в правой части, скопируйте значение в поле рядом с полем **строку подключения.**  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_18.PNG)  

9.  Теперь откройте файл Web.config и замените значение в connectionString со значением, скопированный ранее.  Сохраните файл Web.config.  

    > [!NOTE]  
    > Описанные выше действия необходимы, чтобы мы могли получить новые строки подключения.  В противном случае при запуске обновления базы данных ниже возникнет ошибка.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_19.PNG)  

10. В верхней части Visual Studio, выберите **представление** -> **Other Windows** -> **консоль диспетчера пакетов**.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_20.PNG)  

11. Внизу, в консоли диспетчера пакетов введите: `Enable-Migrations` и нажмите клавишу ВВОД.  

    > [!NOTE]  
    > Если вы получаете сообщение об ошибке: Enable-Migrations не распознается как командлет, введите Install-Package EntityFramework, чтобы обновить EntityFramework.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_21.PNG)  

12. Внизу, в консоли диспетчера пакетов введите: `Add-Migration <anynamehere>` и нажмите клавишу ВВОД.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_22.PNG)  

13. Внизу, в консоли диспетчера пакетов введите: `Update-Database` и нажмите клавишу ВВОД.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_23.PNG)  

## <a name="modify-the-webapi-in-visual-studio"></a>Изменить веб-API в Visual Studio  

#### <a name="to-modify-the-sample-web-api"></a>Чтобы изменить пример веб-API  

1.  Откройте пример, с помощью Visual Studio.  

2.  Откройте файл web.config.  Измените следующие значения:  

    -   IDA: ClientId — введите значение из #3 в предыдущем разделе группы приложений создание.  

    -   IDA: ClientSecret — введите значение из #5 в предыдущем разделе группы приложений создание.  

    -   IDA: GraphResourceId - введите значение из #6 в предыдущем разделе группы приложений создание.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_24.PNG)  

3.  Откройте файл Startup.Auth.cs под App_Start и внесите следующие изменения:  

    -   Закомментируйте следующие строки:  

        ```  
        //private static string aadInstance = ConfigurationManager.AppSettings["ida:AADInstance"];  
        //private static string tenant = ConfigurationManager.AppSettings["ida:Tenant"];  
        //public static readonly string Authority = String.Format(CultureInfo.InvariantCulture, aadInstance, tenant);  
        ```  

    -   Добавьте следующую строку на его место:  

        ```  
        public static readonly string Authority = "https://<your_fsname>/adfs";  
        ```  

        где < your_fsname > замещается часть url службы федерации, например adfs.contoso.com DNS  

        ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_25.PNG)  

4.  Откройте файл UserProfileController.cs и внесите следующие изменения:  

    -   Закомментируйте следующие:  

        ```  
        //authContext = new AuthenticationContext(Startup.Authority, new TokenDbCache(userObjectID));  
        ```  

    -   Измените оба вхождения со следующими:  

        ```  
        authContext = new AuthenticationContext(Startup.Authority, false, new TokenDbCache(userObjectID));  
        ```  

        ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_27.PNG)  

    -   Закомментируйте следующие:  

        ```  
        //authContext = new AuthenticationContext(Startup.Authority);  
        ```  

    -   Измените оба вхождения со следующими:  

        ```  
        authContext = new AuthenticationContext(Startup.Authority, false);  
        ```  

        ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_28.PNG)  

    -   Теперь закомментируйте все экземпляры из следующих:  

        ```  
        Uri redirectUri = new Uri(Request.Url.GetLeftPart(UriPartial.Authority).ToString() + "/OAuth");  
        ```  

    -   Замените все вхождения следующее:  

        ```  
        Uri redirectUri = new Uri(Request.Url.GetLeftPart(UriPartial.Authority).ToString());  
        ```  

        ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_34.PNG)  

## <a name="test-the-solution"></a>Тестирование решения  
В этом разделе мы будем тестировать решение конфиденциального клиента.  Используйте следующую процедуру для тестирования решения.  

#### <a name="testing-the-confidential-client-solution"></a>Тестирование решения конфиденциального клиента  

1.  В верхней части Visual Studio убедитесь, что установлен Internet Explorer и щелкните зеленую стрелку.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_36.png)  

2.  Когда появится страница ASP.Net, щелкните **зарегистрировать** в верхнем правом углу страницы.  Введите имя пользователя и пароль и нажмите кнопку **зарегистрировать** кнопки.  Это создает локальную учетную запись в базе данных SQL.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_31.PNG)  

4.  Обратите внимание, что теперь веб-сайте ASP.NET говорит Hello abby@contoso.com!.  Нажмите кнопку **профиль**.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_32.PNG)  

5.  Это откроет страницу без все сведения и говорит, что мы должны щелкните здесь, чтобы войти.  Нажмите кнопку **здесь**.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_33.PNG)  

6.  Теперь быть отображается запрос на вход в службы AD FS.  

    ![AD FS Oauth](media/Enabling-Oauth-Confidential-Clients-with-AD-FS-2016/AD_FS_Confidential_35.PNG)  

## <a name="next-steps"></a>Следующие шаги
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
