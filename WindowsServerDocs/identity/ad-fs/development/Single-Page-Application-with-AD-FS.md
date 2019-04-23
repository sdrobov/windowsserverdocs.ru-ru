---
title: Создавайте одностраничные веб-приложения с помощью OAuth и ADAL. JS с AD FS 2016
description: Пошаговое руководство, в котором содержатся инструкции по проверке подлинности в AD FS с помощью ADAL для JavaScript, обеспечение безопасности приложение angularjs — версия основе одностраничное приложение
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 06/12/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: active-directory-federation-services
ms.openlocfilehash: 78ab9f5d7c3e75650a4efb171d3b9281c56c63d3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59865305"
---
# <a name="build-a-single-page-web-application-using-oauth-and-adaljs-with-ad-fs-2016"></a>Создавайте одностраничные веб-приложения с помощью OAuth и ADAL. JS с AD FS 2016

>Область применения. Windows Server 2016

Это пошаговое руководство содержит инструкции для проверки подлинности в AD FS с помощью ADAL для JavaScript, обеспечение безопасности приложение angularjs — версия, на основе одностраничное приложение, реализовано с серверной частью веб-API ASP.NET.

В этом случае при входе пользователя в систему интерфейс JavaScript использует [библиотеку аутентификации Active Directory для JavaScript (ADAL. JS)](https://github.com/AzureAD/azure-activedirectory-library-for-js) и неявное предоставление авторизации для получения маркера идентификатора (id_token) из Azure AD. Маркер кэшируется, и клиент присоединяет его к запросу как маркер носителя при выполнении вызовов к его веб-API серверной части, которая защищена с помощью по промежуточного слоя OWIN.

>ПРЕДУПРЕЖДЕНИЕ! Пример, в котором вы можете создавать здесь — только в образовательных целях. Эти инструкции предназначены для реализации самый простой и наиболее минимальным возможным предоставление необходимые элементы модели. Пример могут не включать все аспекты обработки ошибок и другие связанные функциональные возможности.

>[!NOTE]
>В этом пошаговом руководстве применяется **только** для сервера AD FS 2016 и более поздних версий 

## <a name="overview"></a>Обзор
В этом примере мы создадим поток проверки подлинности, где проверки подлинности клиента одностраничного приложения с AD FS для обеспечения безопасного доступа к ресурсам веб-API в серверной части. Ниже приведена общая последовательность проверки подлинности


![Проверки подлинности AD FS](media/Single-Page-Application-with-AD-FS/authenticationflow.PNG)

При использовании в одностраничное приложение, пользователь переходит в начальное расположение, из там, где запуск страницы и коллекцию файлов JavaScript и HTML-представления загружаются. Необходимо настроить Active Directory проверки подлинности Library (ADAL) знать важнейшую информацию о своем приложении, т. е. экземпляр AD FS, но идентификатор клиента, таким образом, чтобы оно может направить проверку подлинности в AD FS.

Если ADAL видит триггер для проверки подлинности, он использует сведения, предоставляемые приложением и направляет проверки подлинности службу маркеров безопасности AD FS.  Одностраничные приложения, который зарегистрировался в качестве общедоступного клиента в AD FS, автоматически настраивается для неявного потока предоставления. Результаты запроса авторизации в маркер идентификатора, который возвращается в приложение с помощью #fragment. Последующие вызовы к серверной части веб-API будет нести этот маркер Идентификации как маркер носителя в заголовке, чтобы получить доступ к веб-API.

## <a name="setting-up-the-development-box"></a>Настройка поле разработки
В этом пошаговом руководстве используется Visual Studio 2015. В проекте используются библиотеки ADAL JS. Дополнительные сведения о см. в статье ADAL [.NET библиотеки проверки подлинности Active Directory.](https://msdn.microsoft.com/library/azure/mt417579.aspx)

## <a name="setting-up-the-environment"></a>Настройка среды
В этом пошаговом руководстве мы будем использовать базовой установки:

1.  КОНТРОЛЛЕР ДОМЕНА: Контроллер домена для домена, в котором будет размещаться AD FS
2.  Сервер AD FS: Сервер AD FS для домена
3.  Компьютер разработки: Компьютере, где установлена среда Visual Studio и будут разрабатываться в нашем примере

Можно Если вы хотите использовать только две машины. Одно для контроллера домена или AD FS, а другой — для разработки в примере.

Как настроить контроллер домена и AD FS выходит за рамки этой статьи. Для развертывания, Дополнительные сведения см.

- [Развертывание AD DS](../../ad-ds/deploy/AD-DS-Deployment.md) 
- [Развертывание AD FS](../AD-FS-Deployment.md)



## <a name="clone-or-download-this-repository"></a>Клонируйте или скачайте этот репозиторий
Мы используем пример приложения, созданный для интеграции Azure AD в одностраничное приложение AngularJS и его изменения для вместо защиты ресурсов серверной части с помощью AD FS.

Из оболочки или командной строки:

    git clone https://github.com/Azure-Samples/active-directory-angularjs-singlepageapp.git

## <a name="about-the-code"></a>Сведения о коде
Ниже перечислены основные файлы, содержащие логику проверки подлинности.

**App.js** - внедряет зависимостей модуля ADAL, предоставляет значения конфигурации приложения, используемые ADAL для управления взаимодействия протокола, упомянутые в AAD и указывает, какие маршруты не должны быть доступны без предыдущей проверки подлинности.

**index.HTML** -содержит ссылку на библиотеку adal.js

**HomeController.js**-показано, как воспользоваться преимуществами методов login() и logOut() в ADAL.

**UserDataController.js** -показано, как извлечь сведения о пользователе из кэшированного маркера "id_token".

**Startup.Auth.cs** -содержит конфигурацию для веб-API для использования служб федерации Active Directory для проверки подлинности носителя.

## <a name="registering-the-public-client-in-ad-fs"></a>Регистрация общедоступного клиента в AD FS
В этом примере веб-API настроен для прослушивания в https://localhost:44326/. Группы приложений **веб-браузер, доступ к веб-приложения** можно использовать для настройки неявное предоставление потока приложения.

1. Откройте консоль управления AD FS и щелкните **добавить группу приложений**. В **мастере добавления группы приложений** введите имя приложения, описание и выберите **веб-браузер, доступ к веб-приложения** шаблон из **клиент-сервер приложения** разделе, как показано ниже  <br>![Создание новой группы приложений](media/Single-Page-Application-with-AD-FS/appgroup_step1.png)

2. На следующей странице **собственное приложение**, укажите идентификатор клиента приложения и URI перенаправления, как показано ниже  <br>![Создание новой группы приложений](media/Single-Page-Application-with-AD-FS/appgroup_step2.png)

3. На следующей странице **применяются политики управления доступом** оставить разрешения как *разрешение для каждого*

4. Странице "Сводка" должен выглядеть аналогично приведенному ниже  <br>![Создание новой группы приложений](media/Single-Page-Application-with-AD-FS/appgroup_step3.png)

5. Щелкните **Далее** для завершения добавления группы приложений, а затем закройте мастер.

## <a name="modifying-the-sample"></a>Изменение примера
Настройте ADAL JS

Откройте **app.js** файлов и изменить **adalProvider.init** определение:

    adalProvider.init(
        {
            instance: 'https://fs.contoso.com/', // your STS URL
            tenant: 'adfs',                      // this should be adfs
            clientId: 'https://localhost:44326/', // your client ID of the
            //cacheLocation: 'localStorage', // enable this for IE, as sessionStorage does not work for localhost.
        },
        $httpProvider
        );

|Конфигурация|Описание
|--------|--------
|instance|URL-адрес службы маркеров безопасности, например https://fs.contoso.com/
|tenant|Сохраните их как «служб федерации Active Directory»
|clientID|Это идентификатор клиента, указанный при настройке общедоступного клиента для одностраничного приложения

## <a name="configure-webapi-to-use-ad-fs"></a>Настройка веб-API, на использование AD FS
Откройте **Startup.Auth.cs** в образце и добавьте следующий код в начале: 

    using System.IdentityModel.Tokens;

Удалить:

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
|ValidAudience|Это позволит настроить значение «audience», будут проверяться в токене
|ValidIssuer|Это позволит настроить значение "издатель, будут проверяться в токене
|MetadataEndpoint|Это указывает на сведения о метаданных вашей службы маркеров безопасности

## <a name="add-application-configuration-for-ad-fs"></a>Добавление конфигурации приложения для служб AD FS
Изменение параметров, как показано ниже:

    <appSettings>
    <add key="ida:Audience" value="https://localhost:44326/" />
    <add key="ida:AdfsMetadataEndpoint" value="https://fs.contoso.com/federationmetadata/2007-06/federationmetadata.xml" />
    <add key="ida:Issuer" value="https://fs.contoso.com/adfs" />
      </appSettings>

## <a name="running-the-solution"></a>При запуске решения
Очистить решение, перестройте решение и запустите его. Если вы хотите увидеть подробную трассировку, запустите Fiddler и обеспечить возможность расшифровки HTTPS.

Обозреватель загрузит SPA, и откроется следующий экран:

![Регистрация клиента](media/Single-Page-Application-with-AD-FS/singleapp3.PNG)

Щелкните имя входа.  Список дел запустит процесс проверки подлинности и ADAL JS будет направлять проверку подлинности в AD FS

![Имя входа](media/Single-Page-Application-with-AD-FS/singleapp4a.PNG)

В Fiddler вы увидите токен, возвращаемых как часть URL-адрес в фрагменте #.

![Fiddler](media/Single-Page-Application-with-AD-FS/singleapp5a.PNG)

Можно теперь вызывается серверная часть API, чтобы добавить элементы списка поручений для пользователя, вошедшего в систему:

![Fiddler](media/Single-Page-Application-with-AD-FS/singleapp6.PNG)

## <a name="next-steps"></a>Следующие шаги
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
