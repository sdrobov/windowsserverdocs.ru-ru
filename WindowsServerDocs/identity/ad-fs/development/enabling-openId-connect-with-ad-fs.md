---
ms.assetid: d282bb4e-38a0-4c7c-83d8-f6ea89278057
title: Создание веб-приложения с помощью OpenID Connect с AD FS 2016 и более поздние версии
description: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: dbd42941f8952fc7f649636d2f3645f941240d49
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66190424"
---
# <a name="build-a-web-application-using-openid-connect-with-ad-fs-2016-and-later"></a>Создание веб-приложения с помощью OpenID Connect с AD FS 2016 и более поздние версии

## <a name="pre-requisites"></a>Предварительные требования  
Ниже приведен список предварительных требований, которые требуются перед выполнением этого документа. В этом документе предполагается, что для установки AD FS, так и для создания фермы AD FS.  

-   Клиентские средства GitHub  

-   AD FS в Windows Server 2016 TP4 или более поздней версии  

-   Visual Studio 2013 или более поздней версии.  

## <a name="create-an-application-group-in-ad-fs-2016-and-later"></a>Создание группы приложений в AD FS 2016 и более поздние версии
Ниже описываются способы настройки приложения в AD FS 2016 и более поздних версий.  

#### <a name="create-application-group"></a>Создать группу приложений  

1.  В оснастке управления AD FS, щелкните правой кнопкой мыши на группы приложений и выберите **добавить группу приложений**.  

2.  В мастере группы приложений для имени введите **ADFSSSO** и в разделе **клиентские / серверные приложения** выберите **веб-браузер, доступ к веб-приложения** шаблона.  Нажмите кнопку **Далее**.

    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_1.PNG)  

3.  Копировать **идентификатор клиента** значение.  Он будет использоваться позже как значение для ida: ClientId, в файле web.config приложения.  

4.  Введите следующую команду для **URI перенаправления:**  -  **https://localhost:44320/** .  Нажмите кнопку **Добавить**. Нажмите кнопку **Далее**.  

    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_2.PNG)  

5.  На **Сводка** щелкните **Далее**.  

    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_3.PNG)

6.  На **завершить** щелкните **закрыть**.  

## <a name="download-and-modify-sample-application-to-authenticate-via-openid-connect-and-ad-fs"></a>Загрузите и измените пример приложения для проверки подлинности с помощью OpenID Connect и AD FS  
В этом разделе описывается скачать пример веб-приложения и изменить его в Visual Studio.   Мы будем использовать пример Azure AD, [здесь](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect).  

Загрузите пример проекта, использование Git Bash и введите следующую команду:  

```  
git clone https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect  
```  

![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_8.PNG)  

#### <a name="to-modify-the-app"></a>Чтобы изменить приложение  

1.  Откройте пример, с помощью Visual Studio.  

2.  Перестройте приложение таким образом, чтобы все отсутствующие пакеты NuGet восстанавливаются.  

3.  Откройте файл web.config.  Измените указанные ниже значения, поэтому внешний вид, как показано ниже:  

    ```  
    <add key="ida:ClientId" value="[Replace this Client Id from #3 in above section]" />  
    <add key="ida:ADFSDiscoveryDoc" value="https://[Your ADFS hostname]/adfs/.well-known/openid-configuration" />  
    <!--<add key="ida:Tenant" value="[Enter tenant name, e.g. contoso.onmicrosoft.com]" />      
    <add key="ida:AADInstance" value="https://login.microsoftonline.com/{0}" />-->  
    <add key="ida:PostLogoutRedirectUri" value="[Replace this with Redirect URI from #4 in the above section]" />  
    ```  

    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_9.PNG)  

4.  Откройте файл Startup.Auth.cs и внесите следующие изменения:  

    -   Закомментируйте следующие:  

        ```  
        //string Authority = String.Format(CultureInfo.InvariantCulture, aadInstance, tenant);  
        ```  

    -   Настроить логику инициализации OpenId Connect по промежуточного слоя со следующими изменениями.  

        ```  
        private static string clientId = ConfigurationManager.AppSettings["ida:ClientId"];  
        //private static string aadInstance = ConfigurationManager.AppSettings["ida:AADInstance"];  
        //private static string tenant = ConfigurationManager.AppSettings["ida:Tenant"];  
        private static string metadataAddress = ConfigurationManager.AppSettings["ida:ADFSDiscoveryDoc"];  
        private static string postLogoutRedirectUri = ConfigurationManager.AppSettings["ida:PostLogoutRedirectUri"];  
        ```  

        ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_10.PNG)  

    -   Дополнительно, измените параметры по промежуточного слоя OpenId Connect, как показано ниже:  

        ```  
        app.UseOpenIdConnectAuthentication(  
            new OpenIdConnectAuthenticationOptions  
            {  
                ClientId = clientId,  
                //Authority = authority,  
                MetadataAddress = metadataAddress,  
                PostLogoutRedirectUri = postLogoutRedirectUri,
                RedirectUri = postLogoutRedirectUri
        ```  

        ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_11.PNG)  

        Путем изменения указанных выше мы делаем следующее:  

        -   Вместо использования полномочия для связи данных о надежного издателя, мы укажите расположение документа обнаружения непосредственно через MetadataAddress  

        -   Azure AD не требует наличия URI перенаправления в запросе, но не служб федерации Active Directory. Таким образом нам нужно добавить его здесь  

## <a name="verify-the-app-is-working"></a>Убедитесь, что приложение работает  
После внесения указанных выше изменений, нажмите клавишу F5.  Это приведет к появлению на странице примеров.  Нажмите эту кнопку, при входе.  

![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_12.PNG)  

Будут перенаправляться на странице входа AD FS.  Действуйте и войдите в систему.  

![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_13.PNG)  

После успешного выполнения вы увидите сообщение о том, что теперь вы вошли.  

![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_14.PNG)  

## <a name="next-steps"></a>Следующие шаги
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
