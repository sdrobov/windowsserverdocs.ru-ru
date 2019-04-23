---
ms.assetid: 5052f13c-ff35-471d-bff5-00b5dd24f8aa
title: Создание многоуровневого приложения, с помощью On-Behalf-Of (OBO) с помощью OAuth с AD FS 2016
description: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 33d0bfa4139f16c90f3d79f5b61188b4d311538b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858945"
---
# <a name="build-a-multi-tiered-application-using-on-behalf-of-obo-using-oauth-with-ad-fs-2016"></a>Создание многоуровневого приложения, с помощью On-Behalf-Of (OBO) с помощью OAuth с AD FS 2016

>Область применения. Windows Server 2016

В этом пошаговом руководстве приведены инструкции по реализации on-behalf-of (OBO) проверки подлинности с помощью AD FS в Windows Server 2016 TP5. Дополнительные сведения о проверке подлинности от ИМЕНИ см. в статье [сценарии AD FS для разработчиков](../../ad-fs/overview/AD-FS-Scenarios-for-Developers.md)

>ПРЕДУПРЕЖДЕНИЕ! Пример, в котором вы можете создавать здесь — только в образовательных целях. Эти инструкции предназначены для реализации самый простой и наиболее минимальным возможным предоставление необходимые элементы модели. Пример могут не включать все аспекты обработки ошибок и другие связанные функциональные возможности и фокусируется только на получение успешной проверки подлинности от ИМЕНИ.

## <a name="overview"></a>Обзор

В этом примере мы создадим поток проверки подлинности, в которой клиент будет осуществлять доступ к веб-службы среднего уровня и веб-служба затем будет действовать от имени прошедшего проверку подлинности клиента, чтобы получить маркер доступа.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO28.png)

Ниже приведен процесс проверки подлинности, в которой будет достигнуть образца
1. Клиент проходит проверку подлинности конечной точки авторизации AD FS и запрашивает код авторизации
2. Конечная точка авторизации возвращает код проверки подлинности для клиента
3. Клиент использует код проверки подлинности и предоставляет их в конечную точку маркера AD FS для запроса маркера доступа для веб-службы среднего уровня как веб-API
4. AD FS возвращает токен доступа для веб-службы среднего уровня. Для получения дополнительных возможностей службы среднего уровня требуется доступ к веб-API серверной части
5. Клиент использует маркер доступа для использования службы среднего уровня.
6. Служба среднего уровня предоставляет маркер доступа для конечной точки маркера AD FS и запросы маркер доступа для веб-API серверной части on-behalf-of прошедшего проверку подлинности пользователя
7. AD FS возвращает токен доступа для веб-API серверной части службы среднего уровня actiing как клиент
8. Служба среднего уровня использует маркер доступа, предоставляемые AD FS на шаге 7, для доступа к серверной части веб-API, как клиент и выполнения необходимых функций

## <a name="sample-structure"></a>Пример структуры

Пример будет состоять из трех модулей


Модуль | Описание
-------|------------
ToDoClient | Собственный клиент, с которым взаимодействует пользователь
ToDoService | Промежуточный веб-API, который выступает в качестве клиента для веб-API серверной части
WebAPIOBO | Серверной части веб-api, который используется для выполнения необходимые операции, когда пользователь добавляет элемент ToDoItem ToDoService




## <a name="setting-up-the-development-box"></a>Настройка поле разработки

В этом пошаговом руководстве используется Visual Studio 2015. Проект интенсивно использует библиотеку проверки подлинности Active Directory (ADAL). Дополнительные сведения о см. в статье ADAL [.NET библиотеки проверки подлинности Active Directory](https://msdn.microsoft.com/library/azure/mt417579.aspx)

В примере также используется v11.0 SQL LocalDB. Установите SQL LocalDB до работы на примере кода.

## <a name="setting-up-the-environment"></a>Настройка среды
Мы будем работать с базовой установки:

1. **КОНТРОЛЛЕР ДОМЕНА**: Контроллер домена для домена, в котором будет размещаться AD FS
2. **Сервер AD FS**: Сервер AD FS для домена
3. **Компьютер разработки**: Компьютере, где установлена среда Visual Studio и будут разрабатываться в нашем примере

Можно Если вы хотите использовать только две машины. Одно для контроллера домена и ADFS, а другой — для разработки в примере.

Как настроить контроллер домена и AD FS выходит за рамки этой статьи. Для развертывания, Дополнительные сведения см.

- [Развертывание AD DS](../../ad-ds/deploy/AD-DS-Deployment.md)
- [Развертывание AD FS](../AD-FS-Deployment.md)

Образец, исходя из существующего образца OBO от Azure, созданные Витторио Берточчи и доступных [здесь](https://github.com/Azure-Samples/active-directory-dotnet-webapi-onbehalfof). Следуйте инструкциям, чтобы клонировать проект на компьютере разработки и создать копию примера приложения, чтобы приступить к работе с.

## <a name="clone-or-download-this-repository"></a>Клонируйте или скачайте этот репозиторий

Из оболочки или командной строки:

    git clone https://github.com/Azure-Samples/active-directory-dotnet-webapi-onbehalfof.git

## <a name="modifying-the-sample"></a>Изменение примера

Сразу же после открытия решения веб-API-OnBehalfOf-DotNet.sln, вы заметите, что у вас есть два проекта в решении-

* **ToDoListClient**: Это будет использоваться в качестве клиента OpenID, который пользователь будет взаимодействует с
* **ToDoListService**: Это будет быть веб-сервер приложения среднего уровня и службы, которая будет взаимодействовать с другой серверной части веб-API от ИМЕНИ пользователя, прошедшего аутентификацию

Как вы видите, нам нужно добавить другой проект позже который будет выступать в качестве ресурса, будут доступны для ToDoListService среднего уровня.

### <a name="configuring-ad-fs-for-the-client-and-webserver-app"></a>Настройка служб AD FS для клиента и веб-сервера приложений

В текущей форме образца проверки подлинности настроен на эти операции выполняются Azure AD. Мы хотим изменить механизм проверки подлинности и direct его к AD FS развернут локально. Чтобы сделать это, нам нужно настроить AD FS для распознавания клиентских и веб-сервер приложений, у нас есть в образце.

**Создание группы приложений**

Откройте оснастку управления AD FS MMC и добавьте новую группу приложений. Выберите шаблон машинный код приложения веб-API.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO2.PNG)

Нажмите кнопку Далее и откроется страница предоставляют сведения о клиентском приложении. Присвойте соответствующее имя для клиентского приложения в AD FS. Скопируйте идентификатор клиента и сохраните его, которые можно открыть позднее, когда это потребуется в файле конфигурации приложения в visual studio.

>Примечание. URI перенаправления может быть любой произвольный URI, так как он действительно не используется в случае собственных клиентов

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO11.PNG)

Нажмите кнопку Далее и откроется страница предоставляют сведения о веб-API. Присвойте подходящее имя для входа AD FS для веб-API и введите URI перенаправления в качестве URI, см. в Visual Studio для ToDoListService

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO16.PNG)

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO18.PNG)

Щелкните Далее, и вы увидите страницу выберите политики контроля доступа. Убедитесь, что вы см. в разделе «Разрешить всем пользователям» в разделе "политика".

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO1.PNG)

Нажмите кнопку Далее и появится на странице Настройка разрешения приложения. На этой странице выберите разрешенные области openid (выбирается по умолчанию) и user_impersonation. Область «user_impersonation» необходима возможность успешного запроса маркера доступа on-behalf-of из AD FS.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO12.PNG)

Нажмите кнопку Далее будет отобразить странице "Сводка". Пройдите остальные шаги мастера и завершить настройку.

Чтобы включить проверку подлинности on-behalf-of, нам нужно убедиться, что AD FS возвращает токен доступа с областью user_impersonation клиенту. Измените выдачи утверждений для ToDoListServiceWebApi включать следующие три пользовательские правила:

    @RuleName = "All claims"
    c:[]
    => issue(claim = c);

    @RuleName = "Issue open id scope"
    => issue(Type = "https://schemas.microsoft.com/identity/claims/scope", Value = "openid");

    @RuleName = "Issue user_impersonation scope"
    => issue(Type = "https://schemas.microsoft.com/identity/claims/scope", Value = "user_impersonation");

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO10.PNG)

**Добавление ToDoListService в качестве клиента в группе приложений**

На этом этапе нам нужно внести дополнительные запись в AD FS для приложения веб-сервер для работы в качестве клиента и не только в качестве ресурса. Откройте группу приложений, которые вы только что создали и выберите команду Добавить приложение.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO15.PNG)

Появится страница «Добавление нового приложения MySampleGroup». На этой странице выберите «Приложение или веб-сайта сервера» в качестве автономного приложения

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO19.PNG)

Нажмите кнопку Далее, и откроется страница для предоставления сведений о приложении. Укажите подходящее имя для данной конфигурации в разделе имя. Убедитесь, что идентификатор клиента как идентификатор ToDoListServiceWebAPI

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO20.PNG)

Нажмите кнопку Далее и вам будет предложена страницу, чтобы настроить учетные данные приложений. Щелкните «Создать общий секрет». Откроется с использованием секрета, который создается автоматически. Скопируйте секрет в некоторое расположение, так как это потребуется, хотя мы настроим ToDoListService в visual studio.


![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO17.PNG)

Щелкните Далее и завершите работу мастера.

### <a name="modifying-the-todolistclient-code"></a>Изменение кода ToDoListClient

#### <a name="modify-the-application-config"></a>Измените файл конфигурации приложения

Перейти к вы все это ToDoListClient проект WebAPI-OnBehalfOf-DotNet. Откройте файл App.config и внесите следующие изменения

* Комментарий ключевой записью ida: клиента
* Для ida: RedirectURI введите произвольный URI, который был указан при настройке MySampleGroup_ClientApplication в AD FS.
* Для ключа ida: ClientID предоставление клиенту идентификатор идентификатор, предоставленный AD FS при настройке MySampleGroup_ClientApplication.
* Для ida: ToDoListResourceID укажите идентификатор ресурса вы присвоили при настройке ToDoListServiceWebApi в AD FS
* Комментарий ключа ida: AADInstance
* Введите идентификатор ресурса ToDoListServiceWebApi ida: ToDoListBaseAddress. Он будет использоваться при вызове веб-API ToDoList.
* Добавление ключа ida: центра и укажите значение в качестве URI для служб AD FS.

Ваш **appSettings** в файле App.Config должен выглядеть примерно следующим образом:

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

Закомментируйте строку, считывание информации клиента из файла конфигурации приложения

    //private static string aadInstance = ConfigurationManager.AppSettings["ida:AADInstance"];
    //private static string tenant = ConfigurationManager.AppSettings["ida:Tenant"];

Измените значение свойства строки право

    private static string authority = ConfigurationManager.AppSettings["ida:Authority"];

Изменить код, чтобы прочитать правильные значения ToDoListResourceId и ToDoListBaseAddress

    private static string todoListResourceId = ConfigurationManager.AppSettings["ida:TodoListResourceId"];
    private static string todoListBaseAddress = ConfigurationManager.AppSettings["ida:TodoListBaseAddress"];

В функции MainWindow() изменить инициализации authcontext как:

    authContext = new AuthenticationContext(authority, false);

### <a name="adding-the-backend-resource"></a>Добавление к внутреннему ресурсу

Чтобы завершить поток on-behalf-of, необходимо создать внутренний ресурс, который будет осуществлять доступ к ToDoListService on-behalf-of авторизованного пользователя. Выбор внутреннего ресурса, можно изменять в соответствии с требованием, но в данном образце можно создать базовый веб-API.

* Щелкните правой кнопкой решение «OnBehalfOf-WebAPI-DotNet» в обозревателе решений и выберите Добавить -> Новый проект
* Выберите шаблон веб-приложения ASP.NET

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO4.PNG)

* На следующей командной строке щелкните «Изменить способ проверки подлинности»
* Выберите «Рабочих и учебных учетных записей» и в раскрывающемся списке справа выберите «On-Premises»
* Введите путь federationmetadata.xml для развертывания AD FS и укажите URI приложения (укажите любой URI сейчас, и можно будет изменить позже) и нажмите кнопку ОК, чтобы добавить проект в решение.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO9.PNG)

* Щелкните правой кнопкой мыши контроллеров в обозревателе решений в новый проект, созданный. Выберите "Добавить" -> контроллер
* На выбор шаблона, выберите «Веб-API 2 контроллер — пустой» и нажмите кнопку ОК.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO3.PNG)

* Присвойте имя соответствующего контроллера

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO13.PNG)

* Добавьте следующий код в контроллер


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

Этот код просто будет возвращать строку, если любой пользователь помещает запрос Get для WebAPIOBO веб-API

### <a name="adding-the-new-backend-webapi-to-ad-fs"></a>Добавление новой серверной части веб-API в AD FS

Откройте группу MySampleGroup приложения. Щелкните Добавить приложение и выберите шаблон веб-API и нажмите кнопку Далее.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO6.PNG)

На странице "Настройка веб-API" укажите соответствующее имя для записи веб-API и идентификатор. Идентификатор должен быть значение URL-адрес SSL проекта WebAPIOBO в visual studio (как мы сделали BackendWebAPIAdfsAdd аналогично).

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO8.PNG)

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO7.PNG)

Продолжайте работу с мастера так же как когда мы настроили веб-API ToDoListService. В конце вашей группы приложений должен выглядеть следующим образом:

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO5.PNG)


### <a name="modifying-the-todolistservice-code"></a>Изменение кода ToDoListService

#### <a name="modifying-the-application-config"></a>Изменение файла конфигурации приложения

* Откройте файл Web.config
* Измените следующие разделы

| Ключ | Значение |
|:-----|:-------|
|IDA: аудитории| Идентификатор ToDoListService, предоставленное AD FS при настройке ToDoListService веб-API, например, https://localhost:44321/|
|IDA: ClientID| Идентификатор ToDoListService, предоставленное AD FS при настройке ToDoListService веб-API, например, https://localhost:44321/ </br>**Очень важно, ida: аудитории и ida: ClientID совпадали друг с другом**|
|IDA: ClientSecret| Это секрет, созданный AD FS при настройке клиента ToDoListService в AD FS|
|IDA: ADFSMetadata| Это URL-адрес метаданных службы федерации Active Directory, например https://fs.anandmsft.com/federationmetadata/2007-06/federationmetadata.xml|
|IDA: OBOWebAPIBase| Это базовый адрес, который будет использоваться для вызова серверной части API, например https://localhost:44300|
|IDA: центр| Это URL-адрес для службы AD FS, пример https://fs.anandmsft.com/adfs/|


Все другие ida: XXXXXXX ключи в **appsettings** узел может быть закомментирован или удален

#### <a name="change-authentication-from-azure-ad-to-ad-fs"></a>Изменить способ проверки подлинности из Azure AD в AD FS

* Откройте файл Startup.Auth.cs
* Удалите следующий код

        app.UseWindowsAzureActiveDirectoryBearerAuthentication(
            new WindowsAzureActiveDirectoryBearerAuthenticationOptions
            {
                Audience = ConfigurationManager.AppSettings["ida:Audience"],
                Tenant = ConfigurationManager.AppSettings["ida:Tenant"],
                TokenValidationParameters = new TokenValidationParameters{ SaveSigninToken = true }
            });

на

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

Добавьте ссылку на System.Web.Extensions. Изменить члены класса, заменив приведенный ниже код

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

на

    //
    // The Client ID is used by the application to uniquely identify itself to Azure AD.
    // The client secret is the credentials for the WebServer Client

    private static string clientId = ConfigurationManager.AppSettings["ida:ClientId"];
    private static string clientSecret = ConfigurationManager.AppSettings["ida:ClientSecret"];
    private static string authority = ConfigurationManager.AppSettings["ida:Authority"];

    // Base address of the WebAPI
    private static string OBOWebAPIBase = ConfigurationManager.AppSettings["ida:OBOWebAPIBase"];

**Изменить утверждения, которое используется для имени**

Из AD FS выпуска Nmae утверждения, но не выпуска утверждение NameIdentifier. В примере используется NameIdentifier однозначно ключ в элементы ToDo. Для простоты можно безопасно удалить NameIdentifier, с утверждением имени в коде. Найти и заменить все вхождения NameIdentifier с именем.

**Изменение процедуры Post и CallGraphAPIOnBehalfOfUser()**

Скопируйте и вставьте приведенный ниже код в ToDoListController.cs и замените код для Post и CallGraphAPIOnBehalfOfUser

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
                result = await authContext.AcquireTokenAsync(...);
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

## <a name="running-the-solution"></a>При запуске решения


По умолчанию visual studio настроена для запуска одного проекта, когда будет достигнута отладочные для запуска.

* Щелкните правой кнопкой мыши решение и выберите его свойства.
* На странице свойств выберите несколько запускаемых проектов и изменении действия для запуска для всех трех элементов.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO14.PNG)

Нажмите клавишу F5 и выполнения решения

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO24.PNG)

Нажмите кнопку входа в систему. Вам будет предложено войти с использованием AD FS

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO25.PNG)

После его входа в систему, добавление элемента списка дел в списке. За кулисами мы собираемся выполнить операцию Post для ToDoListService, который далее будете выполнять отправку WebAPIOBO веб-API.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO26.PNG)

При успешной операции вы увидите, что элемент было добавлено в список с дополнительное сообщение из серверной части веб-API, который осуществлялся с помощью потоком проверки подлинности от ИМЕНИ.

![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO27.PNG)

Также вы увидите подробную трассировку в Fiddler. Запустите Fiddler и обеспечить возможность расшифровки HTTPS. Вы увидите, что мы выпускаем два запроса к конечной точке /adfs/oautincludes.
В первой взаимодействия, мы представлен код доступа к конечной точке маркера и получить маркер для доступа https://localhost:44321/ ![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO22.PNG)

На второй взаимодействия с конечной точкой токена, видно, что у нас есть **requested_token_use** задать в качестве **on_behalf_of** и используется маркер доступа, полученный для среднего уровня веб-службы, т. е. https://localhost:44321/ как утверждение для получения маркера on-behalf-of.
![AD FS OBO](media/AD-FS-On-behalf-of-Authentication-in-Windows-Server-2016/ADFS_OBO23.PNG)

## <a name="next-steps"></a>Следующие шаги
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
