---
title: "Создание одной странице веб-приложения с помощью OAuth и ADAL.JS с AD FS 2016"
description: 
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: active-directory-federation-services
ms.openlocfilehash: 7b3d48e1e38baffeb84b1f236efb43cfda5048c0
ms.sourcegitcommit: c16a2bf1b8a48ff267e71ff29f18b5e5cda003e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="build-a-single-page-web-application-using-oauth-and-adaljs-with-ad-fs-2016"></a>Создание одной странице веб-приложения с помощью OAuth и ADAL.JS с AD FS 2016

>Область применения: Windows Server 2016

Это пошаговое руководство содержит инструкции для проверки подлинности от Служб федерации Active Directory, с помощью ADAL для JavaScript, защита AngularJS на основе одностраничное приложение реализуется с помощью внутреннего веб-API ASP.NET.

>Предупреждение: Пример, в котором вы можете создать здесь — только для образовательных целей. Эти инструкции предназначены для простейший, наиболее минимальной реализации, можно предоставлять необходимые элементы модели. Пример не может содержать все аспекты обработка ошибок и другие связанные функциональные возможности.

>[!NOTE]
>В этом пошаговом руководстве относится **только** для сервера AD FS 2016 и более поздней версии 

## <a name="overview"></a>Обзор
В этом примере мы будут создавать процесса проверки подлинности, где проверки подлинности клиента одной странице приложения от AD FS для безопасного доступа к ресурсам WebAPI на внутреннем сервере. Ниже приведен общий порядок проверки подлинности


![Авторизации AD FS](media/Single-Page-Application-with-AD-FS/authenticationflow.PNG)

При использовании одностраничное приложение, пользователь переходит начальное расположение, из при запуске страницы и набор файлов, JavaScript и HTML представления загружаются. Необходимо настроить Active Directory проверки подлинности библиотеки (ADAL) знать критически важных сведений о приложении, т. е. экземпляр AD FS, идентификатор клиента, так что его можно направлять проверку подлинности в AD FS.

Если ADAL видит триггер для проверки подлинности, он использует сведения, предоставляемые приложением и направляет проверку подлинности в AD FS STS.  Одностраничное приложение, зарегистрированного открытого в качестве клиента AD FS, автоматически настраивается для неявного с предоставлением. Запрос авторизации приводит к созданию маркера идентификатор, который возвращается в приложение через #fragment. Дальнейшие вызовы на внутренний сервер WebAPI будет нести этот идентификатор маркер как маркер носителя в заголовке для получения доступа к WebAPI.

## <a name="setting-up-the-development-box"></a>Настройка поле разработки
Это руководство по применению использует Visual Studio 2015. В проекте используется библиотека ADAL JS. Чтобы узнать, прочтите ADAL [.NET библиотеки проверки подлинности Active Directory.](https://msdn.microsoft.com/library/azure/mt417579.aspx)

## <a name="setting-up-the-environment"></a>Настройка среды
В этом пошаговом руководстве мы будем использовать основные настройки:

1.  Контроллер домена: Контроллер домена для домена, в котором будут размещаться службы федерации Active Directory
2.  Сервера AD FS: Сервера AD FS для домена
3.  Компьютер разработчика: Компьютера, где установлена среда Visual Studio и будет разработка наш пример

Можно Если вы хотите использовать только два компьютера. Один для контроллера домена или AD FS, а другой — для разработки в примере.

Как настроить контроллер домена и AD FS выходит за рамки этой статьи. Развертывание Дополнительные сведения см. в разделе:

- [Развертывание AD DS](../../ad-ds/deploy/AD-DS-Deployment.md) 
- [Развертывание AD FS](../AD-FS-Deployment.md)



## <a name="clone-or-download-this-repository"></a>Клонировать или скачать этот репозиторий
Мы будет использовать образец приложения, созданные для интеграции Azure AD в AngularJS одну страницу приложения и измените его вместо защиты внутренних ресурсов с помощью Служб федерации Active Directory.

Из оболочки или командной строки:

    git clone https://github.com/Azure-Samples/active-directory-angularjs-singlepageapp.git

## <a name="about-the-code"></a>О коде
Ниже перечислены основные файлы, содержащие логику проверки подлинности.

**App.js** - вставляет зависимость ADAL модуля предоставляет значения конфигурации приложения, используемые ADAL передвижения на машине протокола взаимодействия с AAD и указывает, какие маршрутов не должны быть доступны без предыдущая проверка подлинности.

**index.HTML** -содержит ссылку на adal.js

**HomeController.js**-показано, как использовать методы login() и logOut() ADAL.

**UserDataController.js** -показано, как извлечь сведения о пользователе из кэшированного id_token.

**Startup.Auth.cs** -содержит конфигурацию WebAPI использовать службы федерации Active Directory для проверки подлинности носителя.

## <a name="registering-the-public-client-in-ad-fs"></a>Регистрация общей клиента в AD FS
В примере WebAPI настроена для прослушивания по https://localhost:44326 или. Группа приложений **веб-браузер, доступ к веб-приложения** можно использовать для настройки неявное предоставление потока приложения.

1. Откройте консоль управления AD FS и выберите команду **добавить группу приложения**. В **мастера добавления групп приложения** введите имя приложения, описание и выберите **веб-браузер, доступ к веб-приложения** шаблона из **клиент-серверные приложения** статьи, как показано ниже
    <br>![Создание новой группы приложений](media/Single-Page-Application-with-AD-FS/appgroup_step1.png)

2. На следующей странице **собственного приложения**, предоставьте идентификатор клиентского приложения и перенаправления URI, как показано ниже
    <br>![Создание новой группы приложений](media/Single-Page-Application-with-AD-FS/appgroup_step2.png)

3. На следующей странице **применение политики управления доступом** оставить разрешения как *разрешить всем пользователям*

4. Страница сводки должен выглядеть ниже
    <br>![Создание новой группы приложений](media/Single-Page-Application-with-AD-FS/appgroup_step3.png)

5. Щелкните **Далее** для завершения добавления группы приложений, а затем закройте мастер.

## <a name="modifying-the-sample"></a>Изменение образца
Настройка ADAL JS

Откройте **app.js** файла и изменить **adalProvider.init** определение:

    adalProvider.init(
        {
            instance: 'https://fs.contoso.com/', // your STS URL
            tenant: 'adfs',                      // this should be adfs
            clientId: 'https://localhost:44326/', // your client ID of the
            //cacheLocation: 'localStorage', // enable this for IE, as sessionStorage does not work for localhost.
        },
        $httpProvider
        );

|Конфигурации|Описание
|--------|--------
|экземпляр|STS URL-адрес, например https://fs.contoso.com/
|клиента|Сохранить его как «adfs»
|clientID|Это идентификатор клиента, указанный при настройке общих клиента для приложения одной странице

## <a name="configure-webapi-to-use-ad-fs"></a>Настройка WebAPI использование AD FS
Откройте **Startup.Auth.cs** в этом примере файл и добавьте следующее в начале: 

    using System.IdentityModel.Tokens;

удаление:

                app.UseWindowsAzureActiveDirectoryBearerAuthentication(
    new WindowsAzureActiveDirectoryBearerAuthenticationOptions
    {
    Audience = ConfigurationManager.AppSettings["ida:Audience"],
    Tenant = ConfigurationManager.AppSettings["ida:Tenant"]
    });

и добавьте:

    app.UseActiveDirectoryFederationServicesBearerAuthentication(
    new ActiveDirectoryFederationServicesBearerAuthenticationOptions
    {
    MetadataEndpoint = ConfigurationManager.AppSettings["ida:AdfsMetadataEndpoint"],
    TokenValidationParameters = new TokenValidationParameters()
    {
    ValidAudience = ConfigurationManager.AppSettings["ida:Audience"],
    ValidIssuer = ConfigurationManager.AppSettings["ida:Issuer"]
    }
    }
    );

|Параметр|Описание
|--------|--------
|ValidAudience|Это настраивает значение «аудитории», будут возвращены от маркера
|ValidIssuer|Это настраивает значение ", будет проверяться в маркер от поставщика
|MetadataEndpoint|Это указывает на сведения метаданных для вашей службы токенов безопасности

## <a name="add-application-configuration-for-ad-fs"></a>Добавление конфигурации приложения для служб AD FS
Измените раздел appsettings, как показано ниже:

    <appSettings>
    <add key="ida:Audience" value="https://localhost:44326/" />
    <add key="ida:AdfsMetadataEndpoint" value="https://fs.contoso.com/federationmetadata/2007-06/federationmetadata.xml" />
    <add key="ida:Issuer" value="https://fs.contoso.com/adfs" />
      </appSettings>

## <a name="running-the-solution"></a>Под управлением решения
Очистить решение, перестройте решение и запустить его. Если вы хотите см. подробные трассировки, запустите Fiddler и включите расшифровки HTTPS.

Обозреватель загрузит SPA и откроется следующий экран:

![Регистрация клиента](media/Single-Page-Application-with-AD-FS/singleapp3.PNG)

Щелкните имя входа.  Список ToDo будет активировано порядок проверки подлинности и ADAL JS будут направлять проверку подлинности в AD FS

![Имя входа](media/Single-Page-Application-with-AD-FS/singleapp4a.PNG)

В Fiddler можно просмотреть маркер возвращенный как часть URL-адрес в фрагменте #.

![Fiddler](media/Single-Page-Application-with-AD-FS/singleapp5a.PNG)

Теперь вызвать внутренних API для добавления элементов списка ToDo для пользователя, вошедшего в систему будет:

![Fiddler](media/Single-Page-Application-with-AD-FS/singleapp6.PNG)

## <a name="next-steps"></a>Дальнейшие действия
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
