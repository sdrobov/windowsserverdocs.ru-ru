---
ms.assetid: 5052f13c-ff35-471d-bff5-00b5dd24f8aa
title: "Построение многоуровневого приложения с помощью On-Behalf-Of (OBO) с помощью OAuth с AD FS 2016"
description: 
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 8940cde2b78ce3ead499263e6fba0fbe28aae695
ms.sourcegitcommit: c16a2bf1b8a48ff267e71ff29f18b5e5cda003e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="build-a-multi-tiered-application-using-on-behalf-of-obo-using-oauth-with-ad-fs-2016"></a>Построение многоуровневого приложения с помощью On-Behalf-Of (OBO) с помощью OAuth с AD FS 2016

>Область применения: Windows Server 2016

Это пошаговое руководство содержит инструкции по реализации от имени представляет (OBO) проверки подлинности с помощью Служб федерации Active Directory в Windows Server 2016 TP5.  O Дополнительные сведения о проверке подлинности OBO прочтите [сценарии AD FS для разработчиков](../../ad-fs/overview/AD-FS-Scenarios-for-Developers.md)

>Предупреждение: Пример, в котором вы можете создать здесь — только для образовательных целей. Эти инструкции предназначены для простейший, наиболее минимальной реализации, можно предоставлять необходимые элементы модели. Пример не может содержать все аспекты обработка ошибок и другие связанные функциональные возможности и содержит только на получение успешной проверки подлинности OBO.

## <a name="overview"></a>Обзор

В этом примере мы будут создавать процесса проверки подлинности, в которой клиент будет обращаться к веб-службы среднего уровня и веб-службы, затем будет действовать от имени клиента с проверкой подлинности, чтобы получить маркер доступа.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO28.PNG)

Ниже приведен порядок проверки подлинности, будут добиться образца
1. Клиент проходит проверку подлинности для AD FS авторизации конечной точки и запрашивает кода авторизации
2. Конечная точка авторизации возвращает клиенту код проверки подлинности
3. Клиент, использующую код проверки подлинности и представляется его к конечной точке токена AD FS для запроса маркер доступа для среднего уровня веб-службы, как WebAPI
4. Службы федерации Active Directory возвращает маркер доступа Mid уровня веб-службы. Для дополнительных функций средней уровня службе требуется доступ к внутреннему WebAPI
5. Клиент использует маркер доступа для использования среднего уровня службы.
6. Средний уровень службы предоставляет маркер доступа к конечной точке токена AD FS и запросы маркер доступа для внутренних WebAPI от имени представляет с проверкой подлинности пользователя
7. Службы федерации Active Directory возвращает маркер доступа для внутреннего WebAPI среднего уровня службы actiing как клиент
8. Средний уровень службы использует маркер доступа, предоставляемые AD FS в шаге 7 для доступа к внутреннему WebAPI как клиент и выполнять необходимые функции

## <a name="sample-structure"></a>Пример структуры

Пример будет состоит из трех модулей


Модуль | Описание
-------|------------
ToDoClient | Собственный клиент, с которым взаимодействует пользователь
ToDoService | Средней веб-уровня API, который выступает в качестве клиента для внутреннего WebAPI
WebAPIOBO | Серверная часть веб-api, который используется для выполнения необходимых операций, когда пользователь добавляет ToDoItem ToDoService




## <a name="setting-up-the-development-box"></a>Настройка поле разработки

Это руководство по применению использует Visual Studio 2015. В проекте интенсивно используется библиотеки проверки подлинности Active Directory (ADAL). Чтобы узнать, прочтите ADAL [.NET библиотеки проверки подлинности Active Directory](https://msdn.microsoft.com/library/azure/mt417579.aspx)

В примере также используется v11.0 SQL LocalDB. Установите SQL LocalDB до работать в примере.

## <a name="setting-up-the-environment"></a>Настройка среды
Мы будем работать с базовой установки:

1. **Контроллер домена**: контроллер домена для домена, в котором будут размещаться службы федерации Active Directory
2. **Сервера AD FS**: сервера AD FS для домена
3. **Компьютер разработчика**: компьютера, где установлена среда Visual Studio и будет разработка выборка

Можно Если вы хотите использовать только два компьютера. Один для контроллера домена или служб федерации Active Directory, а другой — для разработки в примере.

Как настроить контроллер домена и AD FS выходит за рамки этой статьи. Развертывание Дополнительные сведения см. в разделе:

- [Развертывание AD DS](../../ad-ds/deploy/AD-DS-Deployment.md)
- [Развертывание AD FS](../AD-FS-Deployment.md)

Пример, основанных на образце OBO от Azure, созданные Vittorio Bertocci и доступных [здесь](https://github.com/Azure-Samples/active-directory-dotnet-webapi-onbehalfof). Следуйте инструкциям для клонировать проекта на компьютере для разработки и создать копию образец, чтобы начать работу с.

## <a name="clone-or-download-this-repository"></a>Клонировать или скачать этот репозиторий

Из оболочки или командной строки:

    git clone https://github.com/Azure-Samples/active-directory-dotnet-webapi-onbehalfof.git

## <a name="modifying-the-sample"></a>Изменение образца

Сразу после открытия решения WebAPI-OnBehalfOf-DotNet.sln Обратите внимание, что у вас есть два проекты в решении-

* **ToDoListClient**: это послужит OpenID клиента, который пользователь будет взаимодействовать с
* **ToDoListService**: это будут приложение промежуточного уровня веб-сервера — службы, будут взаимодействовать с другой внутреннего WebAPI OBO аутентификацию пользователя

Как видно, необходимо добавить другой проект более поздней версии, который будет действовать как ресурс, который будет получать доступ к ToDoListService среднего уровня.

### <a name="configuring-ad-fs-for-the-client-and-webserver-app"></a>Настройка AD FS для клиента и веб-сервер приложения

В текущей форме пример проверки подлинности настраивается должен сделать это с Azure AD. Мы хотим изменить механизм проверки подлинности и direct его по отношению к AD FS развертывается локально. Чтобы сделать это, необходимо настроить AD FS для распознавания клиент и веб-сервер приложения, у нас есть в примере.

**Создание группы приложений**

Откройте оснастку управления AD FS MMC и добавить новую группу приложений. Выберите шаблон собственного приложения WebAPI.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO2.PNG)

Нажмите кнопку Далее, и вам будет предложен страницу для предоставления сведений о приложении клиента. Предоставьте соответствующее имя клиенту приложение в AD FS. Скопируйте идентификатор клиента и сохраните его, где вы можете получить доступ к позже, когда это требуется в конфигурации приложения в visual studio.

>Примечание: URI перенаправления может быть любой произвольный URI как она действительно не используется в случае основной клиентов

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO11.PNG)

Нажмите кнопку Далее, и вам будет предложен страницу для предоставления сведений о WebAPI. Присвойте подходящее имя для входа службы федерации Active Directory для WebAPI и введите URI перенаправления в качестве URI, см в Visual Studio для ToDoListService

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO16.PNG)

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO18.PNG)

Нажмите кнопку Далее, и вы увидите страницу выберите политики управления доступом. Убедитесь, что вы видеть «Разрешить всем пользователям» в разделе политики.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO1.PNG)

Нажмите кнопку Далее, и откроется страница разрешений приложения Настройка. На этой странице выберите области разрешенных как openid (выбрана по умолчанию) и user_impersonation. Область «user_impersonation» необходима возможность успешно запросе маркера доступа от имени представляет с AD FS.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO12.PNG)

Нажмите кнопку Далее будет отображаться страница сводки. Пройдите остальные шаги мастера и окончания конфигурации.

Чтобы включить проверку подлинности от имени представляет, необходимо убедиться, что службы федерации Active Directory возвращает маркер доступа с областью user_impersonation клиенту. Измените выдачи утверждений для ToDoListServiceWebApi для включения три настраиваемые правила:

    @RuleName = "All claims"
    c:[]
    => issue(claim = c);

    @RuleName = "Issue open id scope"
    => issue(Type = "https://schemas.microsoft.com/identity/claims/scope", Value = "openid");

    @RuleName = "Issue user_impersonation scope"
    => issue(Type = "https://schemas.microsoft.com/identity/claims/scope", Value = "user_impersonation");

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO10.PNG)

**Добавление ToDoListService в качестве клиента к группе приложений**

На этом этапе мы требуются дополнительные записи в AD FS для приложения веб-сервер выступать в качестве клиента и не только как ресурс. Откройте группу приложений, который вы только что создали и щелкните Добавить приложение.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO15.PNG)

Появится страница «Добавление нового приложения в MySampleGroup». На этой странице выберите «Приложение или веб-сайта сервера» в качестве автономного приложения

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO19.PNG)

Затем нажмите кнопку Далее, и вам будет предложен страницы, чтобы предоставить сведения о приложении. Введите подходящее имя для записи конфигурации в разделе "имя". Убедитесь, что идентификатор клиента такой же, как идентификатор для ToDoListServiceWebAPI

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO20.PNG)

Нажмите кнопку Далее, и вам будет предложен страницы, чтобы настроить учетные данные приложения. Щелкните «Создать общий секрет». Вам будут предоставлены секрет, который создается автоматически. Скопируйте секрет в каком-либо месте, как это потребуется, пока мы настраиваем ToDoListService в visual studio.


![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO17.PNG)

Нажмите кнопку Далее и завершите работу мастера.

### <a name="modifying-the-todolistclient-code"></a>Изменение кода ToDoListClient

#### <a name="modify-the-application-config"></a>Изменение конфигурации приложения

Перейти к вы находитесь в ToDoListClient проект в решение WebAPI OnBehalfOf DotNet. Откройте файл App.config и внесите следующие изменения

* Ввод ключа ida: клиента комментарий
* Для ida: RedirectURI введите произвольный код URI, который вы указали во время настройки MySampleGroup_ClientApplication в AD FS.
* Для ключа ida: ClientID предоставляет клиенту идентификатор идентификатор, который AD FS предоставило во время настройки MySampleGroup_ClientApplication.
* Для ida: ToDoListResourceID предоставить идентификатор ресурса, предоставленный во время настройки ToDoListServiceWebApi в AD FS
* Комментарий ключа ida: AADInstance
* Введите идентификатор ресурса ToDoListServiceWebApi ida: ToDoListBaseAddress. Это будет использоваться при вызове ToDoList WebAPI.
* Добавьте ida: центра ключей и предоставить значение в качестве URI для Служб федерации Active Directory.

Ваш **appSettings** в App.Config должен выглядеть примерно так:

    <appSettings>
    <!--<add key="ida:Tenant" value="[Enter tenant name, e.g. contoso.onmicrosoft.com]" />-->
    <add key="ida:ClientId" value="c7f7b85c-497c-4589-877f-b17a0bd13398" />
    <add key="ida:RedirectUri" value="https://arbitraryuri.com/" />
    <add key="ida:TodoListResourceId" value="https://localhost:44321/" />
    <!--<add key="ida:AADInstance" value="https://login.microsoftonline.com/{0}" />-->
    <add key="ida:TodoListBaseAddress" value="https://localhost:44321" />
    <add key="ida:Authority" value="https://fs.anandmsft.com/adfs/"/>
    </appSettings>

#### <a name="modifying-the-code"></a>Изменение кода

**MainWindow.xaml.cs**

Комментарий строке чтения данных клиента из файла конфигурации приложения

    //private static string aadInstance = ConfigurationManager.AppSettings["ida:AADInstance"];
    //private static string tenant = ConfigurationManager.AppSettings["ida:Tenant"];

Измените значение строки центра

    private static string authority = ConfigurationManager.AppSettings["ida:Authority"];

Изменить код для чтения правильные значения ToDoListResourceId и ToDoListBaseAddress

    private static string todoListResourceId = ConfigurationManager.AppSettings["ida:TodoListResourceId"];
    private static string todoListBaseAddress = ConfigurationManager.AppSettings["ida:TodoListBaseAddress"];

В функцию MainWindow() изменить инициализации authcontext как:

    authContext = new AuthenticationContext(authority, false);

### <a name="adding-the-backend-resource"></a>Добавление внутреннего ресурса

Чтобы завершить поток от имени представляет, необходимо создать внутреннего ресурса, будут осуществлять доступ к ToDoListService от имени представляет пользователя, прошедшего проверку. Выбор внутренних ресурсов может варьироваться в соответствии с требованием, но в данном примере вы можете создать основные WebAPI.

* Щелкните правой кнопкой мыши решение «WebAPI OnBehalfOf DotNet» в обозревателе решений и выберите Add -> Новый проект
* Выберите шаблон ASP.NET веб-приложения

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO4.PNG)

* На следующей строке выберите команду «Изменить проверки подлинности»
* Выберите «Рабочие и учебные учетные записи» и в правом раскрывающемся списке выберите «Локально»
* Введите путь federationmetadata.xml для развертывания Служб федерации Active Directory и предоставить URI-адрес приложения (предоставляют какого-либо URI на данный момент, и можно будет изменить позже) и нажмите кнопку ОК, чтобы добавить в проект в решение.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO9.PNG)

* Щелкните правой кнопкой мыши контроллеров в обозревателе решений в новый проект, созданный. Выберите "Добавить" -> контроллера
* Выбор шаблона, выберите «Очистить контроллера - веб-API 2» и нажмите кнопку ОК.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO3.PNG)

* Присвойте имя соответствующего контроллера

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO13.PNG)

* Добавьте следующий код в контроллере


        using System;
        using System.Collections.Generic;
        using System.Linq;
        using System.Net;
        using System.Net.Http;
        using System.Web.Http;
        namespace WebAPIOBO.Controllers
        {
            public class WebAPIOBOController : ApiController
            {
                public IHttpActionResult Get()
                {
                    return Ok("WebAPI via OBO");
                }
            }
        }

Этот код просто возвратит строку, если любой пользователь переводит запрос Get для WebAPI WebAPIOBO

### <a name="adding-the-new-backend-webapi-to-ad-fs"></a>Добавление нового внутреннего WebAPI в AD FS

Откройте группу MySampleGroup приложений. Нажмите кнопку Добавить приложения и выберите шаблон веб-API и нажмите кнопку Далее.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO6.PNG)

На странице Настройка веб-API предоставляют соответствующее имя для входа WebAPI и идентификатор. Идентификатор должен быть значение SSL URL-адрес из WebAPIOBO проекта в visual studio (аналогично делалось для BackendWebAPIAdfsAdd).

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO8.PNG)

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO7.PNG)

Следуйте дальнейшим дальнейшим инструкциям мастера же, как мы в случае настройки ToDoListService WebAPI. В конце группы вашего приложения должен выглядеть ниже:

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO5.PNG)


### <a name="modifying-the-todolistservice-code"></a>Изменение кода ToDoListService

#### <a name="modifying-the-application-config"></a>Изменение конфигурации приложения

* Откройте файл Web.config
* Измените следующие разделы

| Ключ | Значение |
|:-----|:-------|
|IDA: аудитории| Идентификатор ToDoListService как назначенные AD FS во время настройки ToDoListService WebAPI, например, https://localhost:44321/|
|IDA: ClientID| Идентификатор ToDoListService как назначенные AD FS во время настройки ToDoListService WebAPI, например, https://localhost:44321/ </br>**Очень важно, ida: аудитории и ida: ClientID соответствуют друг другу**|
|IDA: ClientSecret| Это секрет, который AD FS в случае, если настройки клиента ToDoListService в AD FS|
|IDA: ADFSMetadata| URL-адрес для вашей службы федерации Active Directory метаданные, например https://fs.anandmsft.com/federationmetadata/2007-06/federationmetadata.xml|
|IDA: OBOWebAPIBase| Это базовый адрес, который мы будем использовать для вызова внутренних API, например https://localhost:44300|
|IDA: центра| URL-адрес для службы AD FS, например https://fs.anandmsft.com/adfs/|


Все другие ida: XXXXXXX ключи в **appsettings** узел может быть или закомментированы

#### <a name="change-authentication-from-azure-ad-to-ad-fs"></a>Изменения проверки подлинности с Azure AD или AD FS

* Откройте файл Startup.Auth.cs
* Удалить следующий код

        app.UseWindowsAzureActiveDirectoryBearerAuthentication(
            new WindowsAzureActiveDirectoryBearerAuthenticationOptions
            {
                Audience = ConfigurationManager.AppSettings["ida:Audience"],
                Tenant = ConfigurationManager.AppSettings["ida:Tenant"],
                TokenValidationParameters = new TokenValidationParameters{ SaveSigninToken = true }
            });

с помощью

        app.UseActiveDirectoryFederationServicesBearerAuthentication(
            new ActiveDirectoryFederationServicesBearerAuthenticationOptions
            {
                MetadataEndpoint = ConfigurationManager.AppSettings["ida:AdfsMetadataEndpoint"],
                TokenValidationParameters = new TokenValidationParameters()
                {
                    SaveSigninToken = true,
                    ValidAudience = ConfigurationManager.AppSettings["ida:Audience"]
                }
            });

#### <a name="modifying-the-todolistcontroller"></a>Изменение ToDoListController

Добавьте ссылку на System.Web. Расширения. Измените члены класса, заменив в следующем фрагменте кода

    //
    // The Client ID is used by the application to uniquely identify itself to Azure AD.
    // The App Key is a credential used by the application to authenticate to Azure AD.
    // The Tenant is the name of the Azure AD tenant in which this application is registered.
    // The AAD Instance is the instance of Azure, for example public Azure or Azure China.
    // The Authority is the sign-in URL of the tenant.
    //
    private static string aadInstance = ConfigurationManager.AppSettings["ida:AADInstance"];
    private static string tenant = ConfigurationManager.AppSettings["ida:Tenant"];
    private static string clientId = ConfigurationManager.AppSettings["ida:ClientId"];
    private static string appKey = ConfigurationManager.AppSettings["ida:AppKey"];

    //
    // To authenticate to the Graph API, the app needs to know the Grah API's App ID URI.
    // To contact the Me endpoint on the Graph API we need the URL as well.
    //
    private static string graphResourceId = ConfigurationManager.AppSettings["ida:GraphResourceId"];
    private static string graphUserUrl = ConfigurationManager.AppSettings["ida:GraphUserUrl"];
    private const string TenantIdClaimType = "https://schemas.microsoft.com/identity/claims/tenantid";

с помощью

    //
    // The Client ID is used by the application to uniquely identify itself to Azure AD.
    // The client secret is the credentials for the WebServer Client

    private static string clientId = ConfigurationManager.AppSettings["ida:ClientId"];
    private static string clientSecret = ConfigurationManager.AppSettings["ida:ClientSecret"];
    private static string authority = ConfigurationManager.AppSettings["ida:Authority"];

    // Base address of the WebAPI
    private static string OBOWebAPIBase = ConfigurationManager.AppSettings["ida:OBOWebAPIBase"];

**Изменение утверждения, используемого в имени**

С AD FS выпуска Nmae утверждения, но не выпуска NameIdentifier утверждения. В примере используется NameIdentifier однозначно ключ в ToDo элементов. Для простоты можно безопасно удалить NameIdentifier с утверждение на имя в коде. Найти и заменить все вхождения NameIdentifier с именем.

**Изменение процедуры Post и CallGraphAPIOnBehalfOfUser()**

Скопируйте и вставьте приведенный ниже код в ToDoListController.cs и замените код для публикации и CallGraphAPIOnBehalfOfUser

    // POST api/todolist
    public async Task Post(TodoItem todo)
    {
        if (!ClaimsPrincipal.Current.FindFirst("https://schemas.microsoft.com/identity/claims/scope").Value.Contains("user_impersonation"))
        {
            throw new HttpResponseException(new HttpResponseMessage { StatusCode = HttpStatusCode.Unauthorized, ReasonPhrase = "The Scope claim does not contain 'user_impersonation' or scope claim not found" });
        }

        //
        // Call the WebAPIOBO On Behalf Of the user who called the To Do list web API.
        //
        string augmentedTitle = null;
        string custommessage = await CallGraphAPIOnBehalfOfUser();
        if (custommessage != null)
        {
            augmentedTitle = String.Format("{0}, Message: {1}", todo.Title, custommessage);
        }
        else
        {
            augmentedTitle = todo.Title;
        }

        if (null != todo && !string.IsNullOrWhiteSpace(todo.Title))
        {
            db.TodoItems.Add(new TodoItem { Title = augmentedTitle, Owner = ClaimsPrincipal.Current.FindFirst(ClaimTypes.Name).Value });
            db.SaveChanges();
        }
    }

    public static async Task<string> CallGraphAPIOnBehalfOfUser()
    {
        string accessToken = null;
        AuthenticationResult result = null;
        AuthenticationContext authContext = null;
        HttpClient httpClient = new HttpClient();
        string custommessage = "";

        //
        // Use ADAL to get a token On Behalf Of the current user.  To do this we will need:
        //      The Resource ID of the service we want to call.
        //      The current user's access token, from the current request's authorization header.
        //      The credentials of this application.
        //      The username (UPN or email) of the user calling the API
        //
        ClientCredential clientCred = new ClientCredential(clientId, clientSecret);
        var bootstrapContext = ClaimsPrincipal.Current.Identities.First().BootstrapContext as System.IdentityModel.Tokens.BootstrapContext;
        string userName = ClaimsPrincipal.Current.FindFirst(ClaimTypes.Upn) != null ? ClaimsPrincipal.Current.FindFirst(ClaimTypes.Upn).Value : ClaimsPrincipal.Current.FindFirst(ClaimTypes.Email).Value;
        string userAccessToken = bootstrapContext.Token;
        UserAssertion userAssertion = new UserAssertion(bootstrapContext.Token, "urn:ietf:params:oauth:grant-type:jwt-bearer", userName);

        string userId = ClaimsPrincipal.Current.FindFirst(ClaimTypes.Name).Value;
        authContext = new AuthenticationContext(authority, false);

        // In the case of a transient error, retry once after 1 second, then abandon.
        // Retrying is optional.  It may be better, for your application, to return an error immediately to the user and have the user initiate the retry.
        bool retry = false;
        int retryCount = 0;

        do
        {
            retry = false;
            try
            {
                result = authContext.AcquireToken(OBOWebAPIBase, clientCred, userAssertion);
                accessToken = result.AccessToken;
            }
            catch (AdalException ex)
            {
                if (ex.ErrorCode == "temporarily_unavailable")
                {
                    // Transient error, OK to retry.
                    retry = true;
                    retryCount++;
                    Thread.Sleep(1000);
                }
            }
        } while ((retry == true) && (retryCount < 1));

        if (accessToken == null)
        {
            // An unexpected error occurred.
            return (null);
        }

        // Once the token has been returned by ADAL, add it to the http authorization header, before making the call to access the To Do list service.
        httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", result.AccessToken);

        // Call the WebAPIOBO.
        HttpResponseMessage response = await httpClient.GetAsync(OBOWebAPIBase + "/api/WebAPIOBO");


        if (response.IsSuccessStatusCode)
        {
            // Read the response and databind to the GridView to display To Do items.
            string s = await response.Content.ReadAsStringAsync();
            JavaScriptSerializer serializer = new JavaScriptSerializer();
            custommessage = serializer.Deserialize<string>(s);
            return custommessage;
        }
        else
        {
            custommessage = "Unsuccessful OBO operation : " + response.ReasonPhrase;
        }
        // An unexpected error occurred calling the Graph API.  Return a null profile.
        return (null);
    }

## <a name="running-the-solution"></a>Под управлением решения


По умолчанию visual studio настроен для запуска один проект, когда вы достигнете отладки для запуска.

* Щелкните правой кнопкой мыши решение и выберите пункт Свойства.
* На странице свойств выберите несколько автозагружаемых проектов и изменяют действие, чтобы запустить для всех трех элементов.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO14.PNG)

Нажмите клавишу F5 и выполнения решения

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO24.PNG)

Нажмите кнопку входа. Вам нужно будет выполнить вход с помощью Служб федерации Active Directory

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO25.PNG)

По окончании входа, добавьте элемент ToDo в списке. За кулисами мы будем делать операции Post к ToDoListService, как дальнейшей будет Post на веб-WebAPIOBO API.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO26.PNG)

При успешной операции вы увидите, что элемент добавлен в список с дополнительные сообщения из внутреннего веб-API, который выполнялся с помощью OBO auth потока.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO27.PNG)

Также можно просматривать подробные трассировок на Fiddler. Запустите Fiddler и включить HTTPS расшифровки. Вы увидите, что мы делаем двух запросов к конечной точке /adfs/oautincludes.
В первом взаимодействии мы представить код доступа к конечной точке токена и получить маркер доступа для https://localhost:44321/ ![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO22.PNG)

В второй взаимодействие с маркера конечной точки, можно увидеть, что у нас есть **requested_token_use** задать в качестве **on_behalf_of** и мы используем для среднего уровня веб-службу, т. е. https://localhost:44321/ как утверждение, чтобы получить маркер от имени представляет получить маркер доступа.
![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO23.PNG)

## <a name="next-steps"></a>Дальнейшие действия
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
