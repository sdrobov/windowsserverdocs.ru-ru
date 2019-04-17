---
ms.assetid: d282bb4e-38a0-4c7c-83d8-f6ea89278057
title: "Создание веб-приложения с помощью подключения OpenID с AD FS 2016"
description: 
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: f8040b19576ac9de4ced43e6313cad69276a3d27
ms.sourcegitcommit: c16a2bf1b8a48ff267e71ff29f18b5e5cda003e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="build-a-web-application-using-openid-connect-with-ad-fs-2016"></a>Создание веб-приложения с помощью подключения OpenID с AD FS 2016

>Область применения: Windows Server 2016

Построенная на начальной поддержку Oauth в AD FS в Windows Server 2012 R2, AD FS 2016 внедрена поддержка с помощью подключения OpenId входа.  
  
## <a name="pre-requisites"></a>Необходимые компоненты  
Ниже перечислены необходимые условия, которые необходимы перед выполнением этого документа. В этом документе предполагается, что была установлена AD FS и создала ферму AD FS.  
  
-   Подписка на Azure AD (бесплатная пробная версия подходит)  
  
-   Средства клиент GitHub  
  
-   AD FS в Windows Server 2016 TP4 или более поздней версии  
  
-   Visual Studio 2013 или более поздней версии.  
  
## <a name="create-an-application-group-in-ad-fs-2016"></a>Создание группы приложения в AD FS 2016  
Приведенные в следующем разделе описывается настройка группы приложений в AD FS 2016.  
  
#### <a name="create-application-group"></a>Создание группы приложений  
  
1.  В оснастку управления AD FS, щелкните правой кнопкой мыши на группами приложений и выберите **добавить группу приложения**.  
  
2.  В мастере группы приложения для имени введите **ADFSSSO** и в разделе **автономные приложения**выберите **серверное приложение или веб-сайт** шаблона.  Нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_1.PNG)  
  
3.  Копировать **идентификатор клиента** значение.  Он будет использоваться позже как значение для ida: ClientId в файле web.config приложения.  
  
4.  Введите следующие данные для **URI перенаправления:** - **https://localhost:44320/**.  Нажмите кнопку **добавить**. Нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_2.PNG)  
  
5.  На **настроить учетные данные приложения** экрана, установите флажок в **создать общий секрет** и скопируйте секрет. Нажмите кнопку **Далее**  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_3.PNG)  
  
6.  На **Сводка** нажмите кнопку **Далее**.  
  
7.  На **Complete** нажмите кнопку **закрыть**.  
  
8.  Теперь в новую группу приложений щелкните правой кнопкой мыши и выберите **свойства**.  
  
9. На **свойства ADFSSSO** щелкните **добавить приложение**.  
  
10. На **добавить новое приложение для примера приложения** выберите **веб-API** и нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_4.PNG)  
  
11. На **Настройка веб-API** введите следующие данные для **идентификатор** - **https://contoso.com/WebApp**.  Нажмите кнопку **добавить**. Нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_7.PNG)  
  
12. На **выберите политики управления доступом** выберите **разрешить всем пользователям** и нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_Confidential_7.PNG)  
  
13. На **Настройка разрешений приложения** экране, убедитесь, что **openid** выбран и нажмите кнопку **Далее**.  
  
    ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_7.PNG)  
  
14. На **Сводка** нажмите кнопку **Далее**.  
  
15. На **Complete** нажмите кнопку **закрыть**.  
  
16. На **свойства приложения пример** щелкните **ОК**.  
  
## <a name="download-and-modify-mvp-app-to-authenticate-via-openid-connect-and-ad-fs"></a>Загрузка и изменение MVP приложения на проверку подлинности посредством OpenId подключения и AD FS  
В этом разделе описывается, как загрузить этот пример веб-API и измените его в Visual Studio.   Мы используем пример Azure AD, который является [здесь](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect).  
  
Чтобы скачать пример с проектом, используйте Git Bash и введите следующую команду:  
  
```  
git clone https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect  
```  
  
![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_8.PNG)  
  
#### <a name="to-modify-the-app"></a>Чтобы изменить приложение  
  
1.  Откройте примера с помощью Visual Studio.  
  
2.  Скомпилируйте приложение, чтобы все отсутствующие NuGets восстанавливаются.  
  
3.  Откройте файл web.config.  Измените следующие значения, поэтому внешний вид, как показано ниже:  
  
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
  
    -   Закомментируйте следующее:  
  
        ```  
        //public static readonly string Authority = String.Format(CultureInfo.InvariantCulture, aadInstance, tenant);  
        ```  
  
    -   Настроить подключения OpenId по промежуточного слоя логике инициализации следующие изменения:  
  
        ```  
        private static string clientId = ConfigurationManager.AppSettings["ida:ClientId"];  
        //private static string aadInstance = ConfigurationManager.AppSettings["ida:AADInstance"];  
        //private static string tenant = ConfigurationManager.AppSettings["ida:Tenant"];  
        private static string metadataAddress = ConfigurationManager.AppSettings["ida:ADFSDiscoveryDoc"];  
        private static string postLogoutRedirectUri = ConfigurationManager.AppSettings["ida:PostLogoutRedirectUri"];  
        ```  
  
        ![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_10.PNG)  
  
    -   Дальше вниз, измените параметры подключения OpenId по промежуточного слоя, как показано ниже:  
  
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
  
        Изменяя выше мы представляем следующие.  
  
        -   Вместо того чтобы использовать центр сертификации для обмена данными данные о доверенных издателей, мы расположение обнаружения doc напрямую через MetadataAddress  
  
        -   Azure AD не реализуется наличие redirect_uri в запросе, но не служб федерации Active Directory. Таким образом необходимо добавить его здесь  
  
## <a name="verify-the-app-is-working"></a>Убедитесь, что приложение работает  
Если были внесены изменения, нажмите клавишу F5.  Будет создан образец страницы.  Щелкните на вход.  
  
![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_12.PNG)  
  
Можно будет повторно направленной на страницу входа Служб федерации Active Directory.  Смелее, зарегистрируйтесь в системе.  
  
![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_13.PNG)  
  
После успешного вы увидите, что вы вошли.  
  
![AD FS OpenID](media/Enabling-OpenId-Connect-with-AD-FS-2016/AD_FS_OpenID_14.PNG)  
  
## <a name="next-steps"></a>Дальнейшие действия
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  

