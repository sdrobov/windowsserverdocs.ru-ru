---
ms.assetid: d282bb4e-38a0-4c7c-83d8-f6ea89278057
title: Создание веб-приложения, с помощью OpenID Connect с AD FS 2016
description: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 74a493e6568b71a05116140ec67586d36f439aa8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882665"
---
# <a name="build-a-web-application-using-openid-connect-with-ad-fs-2016"></a>Создание веб-приложения, с помощью OpenID Connect с AD FS 2016

>Область применения. Windows Server 2016

Основываясь на первоначально поддержка Oauth в AD FS в Windows Server 2012 R2, AD FS 2016 добавлена поддержка использования входа OpenId Connect.  
  
## <a name="pre-requisites"></a>Предварительные требования  
Ниже приведен список предварительных требований, которые требуются перед выполнением этого документа. В этом документе предполагается, что для установки AD FS, так и для создания фермы AD FS.  
  
-   Клиентские средства GitHub  
  
-   AD FS в Windows Server 2016 TP4 или более поздней версии  
  
-   Visual Studio 2013 или более поздней версии.  
  
## <a name="create-an-application-group-in-ad-fs-2016"></a>Создание группы приложений в AD FS 2016  
Ниже описывается, как настроить группы приложений в AD FS 2016.  
  
#### <a name="create-application-group"></a>Создать группу приложений  
  
1.  В оснастке управления AD FS, щелкните правой кнопкой мыши на группы приложений и выберите **добавить группу приложений**.  
  
2.  В мастере группы приложений для имени введите **ADFSSSO** и в разделе **автономными приложениями** выберите **серверное приложение или веб-сайт** шаблона.  Нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_1.PNG)  
  
3.  Копировать **идентификатор клиента** значение.  Он будет использоваться позже как значение для ida: ClientId, в файле web.config приложения.  
  
4.  Введите следующую команду для **URI перенаправления:** - **https://localhost:44320/**.  Нажмите кнопку **Добавить**. Нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_2.PNG)  
  
5.  На **настроить учетные данные приложения** экрана, установите флажок в **создать общий секрет** и скопируйте секрет. Нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_3.PNG)  
  
6.  На **Сводка** щелкните **Далее**.  
  
7.  На **завершить** щелкните **закрыть**.  
  
8.  Новая группа приложения правой кнопкой мыши таблицу и выберите **свойства**.  
  
9. На **свойства ADFSSSO** щелкните **добавить приложение**.  
  
10. На **добавить новое приложение, к примеру приложения** выберите **веб-API** и нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_4.PNG)  
  
11. На **настроить веб-API** экрана, введите следующую команду для **идентификатор** - **https://contoso.com/WebApp**.  Нажмите кнопку **Добавить**. Нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_7.PNG) 
    
12. На **Выбор политики управления доступом** выберите **разрешение для каждого** и нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_Confidential_7.PNG)  
  
13. На **Настройка разрешений приложения** экрана, убедитесь, что **openid** выбран и нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_7.PNG)  
  
14. На **Сводка** щелкните **Далее**.  
  
15. На **завершить** щелкните **закрыть**.  
  
16. На **свойства образца приложения** щелкните **ОК**.  
  
## <a name="download-and-modify-mvp-app-to-authenticate-via-openid-connect-and-ad-fs"></a>Загрузите и измените MVP приложение для проверки подлинности с помощью OpenId Connect и AD FS  
В этом разделе описывается скачать пример веб-API и изменить его в Visual Studio.   Мы будем использовать пример Azure AD, [здесь](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect).  
  
Загрузите пример проекта, использование Git Bash и введите следующую команду:  
  
```  
git clone https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect  
```  
  
![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_8.PNG)  
  
#### <a name="to-modify-the-app"></a>Чтобы изменить приложение  
  
1.  Откройте пример, с помощью Visual Studio.  
  
2.  Скомпилируйте приложение таким образом, чтобы все отсутствующие пакеты NuGet восстанавливаются.  
  
3.  Откройте файл web.config.  Измените указанные ниже значения, поэтому внешний вид, как показано ниже:  
  
    ```  
    <add key="ida:ClientId" value="8219ab4a-df10-4fbd-b95a-8b53c1d8669e" />  
    <add key="ida:ADFSDiscoveryDoc" value="https://adfs.contoso.com/adfs/.well-known/openid-configuration" />  
    <!--<add key="ida:Tenant" value="[Enter tenant name, e.g. contoso.onmicrosoft.com]" />      
    <add key="ida:ResourceID" value="https://contoso.com/WebApp"  
    <add key="ida:AADInstance" value="https://login.microsoftonline.com/{0}" />-->  
    <add key="ida:PostLogoutRedirectUri" value="https://localhost:44320/" />  
    ```  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_9.PNG)  
  
4.  Откройте файл Startup.Auth.cs и внесите следующие изменения:  
  
    -   Закомментируйте следующие:  
  
        ```  
        //public static readonly string Authority = String.Format(CultureInfo.InvariantCulture, aadInstance, tenant);  
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
  
    -   Дальше вниз, измените параметры по промежуточного слоя OpenId Connect, как показано ниже:  
  
        ```  
        app.UseOpenIdConnectAuthentication(  
            new OpenIdConnectAuthenticationOptions  
            {  
                ClientId = clientId,  
                //Authority = authority,  
                MetadataAddress = metadataAddress,  
                RedirectUri = postLogoutRedirectUri,  
                PostLogoutRedirectUri = postLogoutRedirectUri 
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

