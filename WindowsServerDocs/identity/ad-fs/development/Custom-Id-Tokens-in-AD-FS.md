---
title: Настройте утверждения, которые будут выдаваться в id_token при использовании OpenID Connect Connect или OAuth с AD FS 2016 или более поздней версии.
description: Технический обзор концепций маркера настраиваемого идентификатора в AD FS 2016 или более поздней версии.
author: anandyadavmsft
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server
ms.reviewer: anandy
ms.technology: identity-adfs
ms.openlocfilehash: 88ae6837872c5a6cf6bb1d8533a0aa14b82ca573
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71358909"
---
# <a name="customize-claims-to-be-emitted-in-id_token-when-using-openid-connect-or-oauth-with-ad-fs-2016-or-later"></a>Настройте утверждения, которые будут выдаваться в id_token при использовании OpenID Connect Connect или OAuth с AD FS 2016 или более поздней версии.

## <a name="overview"></a>Обзор
В этой [статье показано](native-client-with-ad-fs.md) , как создать приложение, которое использует AD FS для входа в OpenID Connect Connect. Однако по умолчанию в id_token доступен только фиксированный набор утверждений. AD FS 2016 и более поздних выпусков имеют возможность настройки id_token в сценариях OpenID Connect Connect.

## <a name="when-are-custom-id-token-used"></a>Когда используется токен настраиваемого идентификатора?
В некоторых сценариях клиентское приложение может не иметь ресурса, к которому он пытается получить доступ. Поэтому маркер доступа не требуется. В таких случаях клиентскому приложению требуется только маркер идентификатора, но с дополнительными утверждениями, которые могут помочь в функциональности.

## <a name="what-are-the-restrictions-on-getting-custom-claims-in-id-token"></a>Каковы ограничения на получение пользовательских утверждений в маркере идентификации?

### <a name="scenario-1"></a>Сценарий 1

![ограничение](media/Custom-Id-Tokens-in-AD-FS/res1.png)

1.  response_mode задан как form_post
2.  Пользовательские утверждения в маркере идентификации могут получить только открытые клиенты
3.  Идентификатор проверяющей стороны (идентификатор веб-API) должен совпадать с идентификатором клиента

### <a name="scenario-2"></a>Сценарий 2

![ограничение](media/Custom-Id-Tokens-in-AD-FS/restrict2.png)

Установка [KB4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472) на серверах AD FS
1.  response_mode задан как form_post
2.  Как общедоступные, так и конфиденциальные клиенты могут получать настраиваемые утверждения в маркере идентификации.
3.  Назначьте аллатклаимс области для пары "клиент — RP".
Область можно назначить с помощью командлета Grant-Адфсаппликатионпермиссион, как показано в следующем примере:

``` powershell
Grant-AdfsApplicationPermission -ClientRoleIdentifier "https://my/privateclient" -ServerRoleIdentifier "https://rp/fedpassive" -ScopeNames "allatclaims","openid"
```

## <a name="creating-and-configuring-an-oauth-application-to-handle-custom-claims-in-id-token"></a>Создание и настройка приложения OAuth для управления пользовательскими утверждениями в маркере идентификации
Выполните следующие действия, чтобы создать и настроить приложение в AD FS для получения маркера идентификации с настраиваемыми утверждениями.

### <a name="create-and-configure-an-application-group-in-ad-fs-2016-or-later"></a>Создание и настройка группы приложений в AD FS 2016 или более поздней версии

1. В AD FS управления щелкните правой кнопкой мыши группы приложений и выберите команду **Добавить группу приложений**.

2. В мастере группы приложений в поле Имя введите **адфсссо** и в разделе клиент-сервер приложения выберите **собственное приложение, обращающееся к шаблону веб-приложения** . Нажмите кнопку **Далее**.

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap1.png)

3. Скопируйте значение **идентификатора клиента** .  Он будет использоваться позже в качестве значения для Ida: ClientId в файле Web. config приложения.

4. Введите следующую команду для **URI перенаправления:**  -  **https://localhost:44320/** .  Нажмите кнопку **Добавить**. Нажмите кнопку **Далее**.

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap2.png)

5. На экране **Настройка веб-API** введите следующую команду в поле **идентификатор** -  **https://contoso.com/WebApp** .  Нажмите кнопку **Добавить**. Нажмите кнопку **Далее**.  Это значение будет использоваться позже для **Ida: ResourceId** в файле Web. config приложения.

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap3.png)

6. На экране **Выбор политики управления доступом** выберите **разрешение все** и нажмите кнопку **Далее**.

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap4.png)

7. На экране **Настройка разрешений приложения** убедитесь, что выбраны **OpenID Connect** и **Аллатклаимс** , и нажмите кнопку **Далее**.

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap5.png)

8. На экране **Сводка** нажмите кнопку **Далее**.  

   ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap6.png)

9. На экране **Завершение** нажмите кнопку **Закрыть**.

10. В AD FS Управление щелкните группы приложений, чтобы получить список всех групп приложений. Щелкните правой кнопкой мыши **адфсссо** и выберите пункт **свойства**. Выберите **адфсссо-Web API** и нажмите кнопку **изменить...**

    ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap7.png)

11. На экране **Свойства веб-API на адфсссо** выберите вкладку **правила преобразования выдачи** и нажмите кнопку **Добавить правило...**

    ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap8.png)

12. На странице **мастера добавления правила преобразования утверждений** выберите **Отправить утверждения с помощью настраиваемого правила** из раскрывающегося списка и нажмите кнопку **Далее** .

    ![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap9.png)

13. На экране **мастера добавления правила преобразования утверждений** введите **форкустомидтокен** в качестве **имени правила утверждений** и в **настраиваемое правило**— в соответствии с правилом утверждения. Нажмите кнопку **Готово** .

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

### <a name="download-and-modify-the-sample-application-to-emit-custom-claims-in-id_token"></a>Скачивание и изменение примера приложения для создания настраиваемых утверждений в id_token

В этом разделе описывается, как скачать пример веб-приложения и изменить его в Visual Studio.   Мы будем использовать пример Azure AD, приведенный [здесь](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect).  

Чтобы скачать пример проекта, используйте Git Bash и введите следующую команду:  

```  
git clone https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect  
```  

![AD FS OpenID Connect](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_1.PNG)

#### <a name="to-modify-the-app"></a>Изменение приложения

1.  Откройте пример с помощью Visual Studio.  

2.  Перестройте приложение, чтобы восстановить все отсутствующие NuGet.  

3.  Откройте файл Web. config.  Измените следующие значения, чтобы они выглядели следующим образом:  

    ```  
    <add key="ida:ClientId" value="[Replace this Client Id from #3 above under section Create and configure an Application Group in AD FS 2016 or later]" />  
    <add key="ida:ResourceID" value="[Replace this with the Web API Identifier from #5 above]"  />
    <add key="ida:ADFSDiscoveryDoc" value="https://[Your ADFS hostname]/adfs/.well-known/openid-configuration" />  
    <!--<add key="ida:Tenant" value="[Enter tenant name, e.g. contoso.onmicrosoft.com]" />      
    <add key="ida:AADInstance" value="https://login.microsoftonline.com/{0}" />-->  
    <add key="ida:PostLogoutRedirectUri" value="[Replace this with the Redirect URI from #4 above]" />  
    ```  

    ![AD FS OpenID Connect](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_2.PNG)  

4.  Откройте файл Startup.Auth.cs и внесите следующие изменения:  

    -   Настройте логику инициализации по промежуточного слоя OpenID Connect Connect со следующими изменениями:  

        ```  
        private static string clientId = ConfigurationManager.AppSettings["ida:ClientId"];  
        //private static string aadInstance = ConfigurationManager.AppSettings["ida:AADInstance"];  
        //private static string tenant = ConfigurationManager.AppSettings["ida:Tenant"];  
        private static string metadataAddress = ConfigurationManager.AppSettings["ida:ADFSDiscoveryDoc"];
        private static string resourceId = ConfigurationManager.AppSettings["ida:ResourceID"];
        private static string postLogoutRedirectUri = ConfigurationManager.AppSettings["ida:PostLogoutRedirectUri"];  
        ```  

    -   Закомментируйте следующее:  

            ```  
            //string Authority = String.Format(CultureInfo.InvariantCulture, aadInstance, tenant);  
            ```

          ![AD FS OpenID Connect](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_3.PNG)

    -   Далее измените параметры по промежуточного слоя OpenID Connect Connect следующим образом:  

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

        ![AD FS OpenID Connect](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_4.PNG)

5.  Откройте файл HomeController.cs и внесите следующие изменения:  

    -   Добавьте следующую строку:  

            ```  
            using System.Security.Claims;  
            ```

    -   Обновите метод About (), как показано ниже.  

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

        ![AD FS OpenID Connect](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_5.PNG)

### <a name="test-the-custom-claims-in-id-token"></a>Тестирование пользовательских утверждений в маркере идентификации

После внесения приведенных выше изменений нажмите клавишу F5. Откроется пример страницы. Щелкните Вход.

![AD FS OpenID Connect](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_6.PNG)

Вы будете перенаправлены на страницу входа AD FS. Выполните вход.

![AD FS OpenID Connect](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_7.PNG)

После успешного выполнения этой операции вы увидите, что вы вошли в.

![AD FS OpenID Connect](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_8.PNG)

Щелкните ссылку о программе. Вы увидите приветствие [username], которое извлекается из утверждения имени пользователя в маркере идентификации.

![AD FS OpenID Connect](media/Custom-Id-Tokens-in-AD-FS/AD_FS_OpenID_9.PNG)

## <a name="next-steps"></a>Следующие шаги
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
