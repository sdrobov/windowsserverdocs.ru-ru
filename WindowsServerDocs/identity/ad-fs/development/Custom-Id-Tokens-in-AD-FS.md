---
title: Настройка утверждений для выпущенного в "id_token", при использовании OAuth или OpenID Connect с AD FS 2016 или более поздней версии
description: Технический обзор концепций пользовательский идентификатор маркеров в AD FS 2016 или более поздней версии
author: anandyadavmsft
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.reviewer: anandy
ms.technology: identity-adfs
ms.openlocfilehash: 04573aa13689a0e6744b01a0fbf8b11b622b2706
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66445469"
---
# <a name="customize-claims-to-be-emitted-in-idtoken-when-using-openid-connect-or-oauth-with-ad-fs-2016-or-later"></a>Настройка утверждений для выпущенного в "id_token", при использовании OAuth или OpenID Connect с AD FS 2016 или более поздней версии

## <a name="overview"></a>Обзор
Статья [здесь](native-client-with-ad-fs.md) показано, как создать приложение, которое использует OpenID Connect для входа AD FS. Однако по умолчанию есть только фиксированный набор утверждений, доступных в id_token. AD FS 2016 и более поздние версии поддерживают возможность настроить id_token в сценариях OpenID Connect.

## <a name="when-are-custom-id-token-used"></a>Когда будете пользовательский идентификатор токен, используемый?
В некоторых сценариях может оказаться, что клиентское приложение не имеет ресурс, который пытается получить доступ к. Таким образом не требуется маркер доступа. В таких случаях клиентское приложение по сути необходимо только идентификатор токена, однако с некоторые дополнительные утверждения, чтобы помочь в функциональные возможности.

## <a name="what-are-the-restrictions-on-getting-custom-claims-in-id-token"></a>Каковы ограничения на получение пользовательских утверждений в идентификатор маркера?

### <a name="scenario-1"></a>Сценарий 1

![ограничения](media/Custom-Id-Tokens-in-AD-FS/res1.png)

1.  response_mode задается как form_post
2.  Только общедоступные клиенты могут получить настраиваемые утверждения в идентификатор токена
3.  Идентификатор проверяющей стороны (идентификатор веб-API) должны использовать тот же идентификатор клиента

### <a name="scenario-2"></a>Сценарий 2

![ограничения](media/Custom-Id-Tokens-in-AD-FS/restrict2.png)

С помощью [KB4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472) установленные на серверах AD FS
1.  response_mode задается как form_post
2.  Общедоступные и конфиденциальные клиенты могут получать настраиваемые утверждения в идентификатор токена
3.  Назначьте область allatclaims клиенту — пара RP.
Область можно назначить с помощью командлет Grant-ADFSApplicationPermission, как показано в следующем примере:

``` powershell
Grant-AdfsApplicationPermission -ClientRoleIdentifier "https://my/privateclient" -ServerRoleIdentifier "https://rp/fedpassive" -ScopeNames "allatclaims","openid"
```

## <a name="creating-and-configuring-an-oauth-application-to-handle-custom-claims-in-id-token"></a>Создание и настройка приложения OAuth для обработки пользовательских утверждений в маркере
Выполните следующие шаги для создания и настройки приложения в AD FS для получения маркера Идентификации с помощью настраиваемых утверждений.

### <a name="create-and-configure-an-application-group-in-ad-fs-2016-or-later"></a>Создание и настройка группы приложений в AD FS 2016 или более поздней версии

1. В оснастке управления AD FS, щелкните правой кнопкой мыши на группы приложений и выберите **добавить группу приложений**.

2. В мастере группы приложений для имени введите **ADFSSSO** и между клиентом и сервером приложений установите **собственное приложение, веб-приложении** шаблона. Нажмите кнопку **Далее**.

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap1.png)

3. Копировать **идентификатор клиента** значение.  Он будет использоваться позже как значение для ida: ClientId, в файле web.config приложения.

4. Введите следующую команду для **URI перенаправления:**  -  **https://localhost:44320/** .  Нажмите кнопку **Добавить**. Нажмите кнопку **Далее**.

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap2.png)

5. На **настроить веб-API** экрана, введите следующую команду для **идентификатор** -  **https://contoso.com/WebApp** .  Нажмите кнопку **Добавить**. Нажмите кнопку **Далее**.  Это значение будет использоваться позднее для **ida: ResourceID** в файле web.config приложения.

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap3.png)

6. На **Выбор политики управления доступом** выберите **разрешение для каждого** и нажмите кнопку **Далее**.

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap4.png)

7. На **Настройка разрешений приложения** экрана, убедитесь, что **openid** и **allatclaims** установлены и нажмите кнопку **Далее**.

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap5.png)

8. На **Сводка** щелкните **Далее**.  

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap6.png)

9. На **завершить** щелкните **закрыть**.

10. В оснастке управления AD FS щелкните группы приложений, чтобы получить список всех групп приложений. Щелкните правой кнопкой мыши **ADFSSSO** и выберите **свойства**. Выберите **ADFSSSO - веб-API** и нажмите кнопку **изменить...**

    ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap7.png)

11. На **ADFSSSO - веб-API свойства** выберите **правила преобразования выдачи** вкладку и нажмите кнопку **добавить правило...**

    ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap8.png)

12. На **утверждения мастере добавления правила преобразования** выберите **Отправка утверждений с помощью настраиваемого правила** из раскрывающегося списка и нажмите кнопку **Далее**

    ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap9.png)

13. На **утверждения мастере добавления правила преобразования** введите **ForCustomIDToken** в **имя правила утверждения** и следующие утверждения правила в **настраиваемого правила**. Нажмите кнопку **Готово**

    ```  
    x:[]
    => issue(claim=x);  
    ```

    ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap10.png)

```

>[!NOTE]
>You can also use PowerShell to assign the allatclaims and openid scopes
>``` powershell
Grant-AdfsApplicationPermission -ClientRoleIdentifier "[Client ID from #3 above]" -ServerRoleIdentifier "[Identifier from #5 above]" -ScopeNames "allatclaims","openid"
```

### <a name="download-and-modify-the-sample-application-to-emit-custom-claims-in-idtoken"></a>Загрузка и изменение примера приложения для создания пользовательского утверждения в id_token

В этом разделе описывается скачать пример веб-приложения и изменить его в Visual Studio.   Мы будем использовать пример Azure AD, [здесь](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect).  

Загрузите пример проекта, использование Git Bash и введите следующую команду:  

```  
git clone https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect  
```  

![AD FS OpenID](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_1.PNG)

#### <a name="to-modify-the-app"></a>Чтобы изменить приложение

1.  Откройте пример, с помощью Visual Studio.  

2.  Перестройте приложение таким образом, чтобы все отсутствующие пакеты NuGet восстанавливаются.  

3.  Откройте файл web.config.  Измените указанные ниже значения, поэтому внешний вид, как показано ниже:  

    ```  
    <add key="ida:ClientId" value="[Replace this Client Id from #3 above under section Create and configure an Application Group in AD FS 2016 or later]" />  
    <add key="ida:ResourceID" value="[Replace this with the Web API Identifier from #5 above]"  />
    <add key="ida:ADFSDiscoveryDoc" value="https://[Your ADFS hostname]/adfs/.well-known/openid-configuration" />  
    <!--<add key="ida:Tenant" value="[Enter tenant name, e.g. contoso.onmicrosoft.com]" />      
    <add key="ida:AADInstance" value="https://login.microsoftonline.com/{0}" />-->  
    <add key="ida:PostLogoutRedirectUri" value="[Replace this with the Redirect URI from #4 above]" />  
    ```  

    ![AD FS OpenID](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_2.PNG)  

4.  Откройте файл Startup.Auth.cs и внесите следующие изменения:  

    -   Настроить логику инициализации OpenId Connect по промежуточного слоя со следующими изменениями.  

        ```  
        private static string clientId = ConfigurationManager.AppSettings["ida:ClientId"];  
        //private static string aadInstance = ConfigurationManager.AppSettings["ida:AADInstance"];  
        //private static string tenant = ConfigurationManager.AppSettings["ida:Tenant"];  
        private static string metadataAddress = ConfigurationManager.AppSettings["ida:ADFSDiscoveryDoc"];
        private static string resourceId = ConfigurationManager.AppSettings["ida:ResourceID"];
        private static string postLogoutRedirectUri = ConfigurationManager.AppSettings["ida:PostLogoutRedirectUri"];  
        ```  

    -   Закомментируйте следующие:  

            ```  
            //string Authority = String.Format(CultureInfo.InvariantCulture, aadInstance, tenant);  
            ```

          ![AD FS OpenID](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_3.PNG)

    -   Дополнительно, измените параметры по промежуточного слоя OpenId Connect, как показано ниже:  

        ```  
        app.UseOpenIdConnectAuthentication(  
            new OpenIdConnectAuthenticationOptions  
            {  
                ClientId = clientId,  
                //Authority = authority,  
                Resource = resourceId,
                MetadataAddress = metadataAddress,  
                PostLogoutRedirectUri = postLogoutRedirectUri,
                RedirectUri = postLogoutRedirectUri
        ```  

        ![AD FS OpenID](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_4.PNG)

5.  Откройте файл HomeController.cs и внесите следующие изменения:  

    -   Добавьте следующую строку:  

            ```  
            using System.Security.Claims;  
            ```

    -   Обновление метода About(), как показано ниже:  

        ```  
        [Authorize]
        public ActionResult About()
        {
            ClaimsPrincipal cp = ClaimsPrincipal.Current;
            string userName = cp.FindFirst(ClaimTypes.WindowsAccountName).Value;
            ViewBag.Message = String.Format("Hello {0}!", userName);
            return View();
        }
        ```  

        ![AD FS OpenID](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_5.PNG)

### <a name="test-the-custom-claims-in-id-token"></a>Тестирование пользовательских утверждений в маркере

После внесения указанных выше изменений, нажмите клавишу F5. Это приведет к появлению на странице примеров. Нажмите эту кнопку, при входе.

![AD FS OpenID](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_6.PNG)

Будут перенаправляться на странице входа AD FS. Действуйте и войдите в систему.

![AD FS OpenID](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_7.PNG)

После успешного выполнения вы увидите сообщение о том, что теперь вы вошли.

![AD FS OpenID](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_8.PNG)

Щелкните ссылки. Вы увидите Hello [Username], извлекаемый из заявку в маркере имени пользователя

![AD FS OpenID](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_9.PNG)

## <a name="next-steps"></a>Следующие шаги
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
