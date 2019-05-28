---
title: Создание собственного клиентского приложения с помощью общедоступных клиентов OAuth с AD FS 2016 или более поздней версии
description: Пошаговое руководство, в котором содержатся инструкции, создание собственного клиента приложения, используя общедоступный клиентов OAuth и AD FS 2016 или более поздней версии
author: billmath
ms.author: billmath
ms.reviewer: anandy
manager: mtillman
ms.date: 07/17/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: active-directory-federation-services
ms.openlocfilehash: e85a97fa08e4c77588b17aee08ee03e0b897a74c
ms.sourcegitcommit: c8cc0b25ba336a2aafaabc92b19fe8faa56be32b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65976837"
---
# <a name="build-a-native-client-application-using-oauth-public-clients-with-ad-fs-2016-or-later"></a>Создание собственного клиентского приложения с помощью общедоступных клиентов OAuth с AD FS 2016 или более поздней версии

## <a name="overview"></a>Обзор

В этой статье показано, как создавать исходное приложение, которое взаимодействует с веб-API, защищенного с помощью AD FS 2016 или более поздней версии.

1. .Net TodoListClient WPF-приложение использует библиотеку проверки подлинности Active Directory (ADAL) для получения маркера доступа JWT из Azure Active Directory (Azure AD) через протокол OAuth 2.0
2. Маркер доступа используется как токен носителя для проверки подлинности пользователя при вызове конечной точки /todolist TodoListService веб-API.
 Мы с помощью примера приложения для Azure AD здесь и затем изменить его для AD FS 2016 или более поздней версии.

![Обзор приложения](media/native-client-with-ad-fs-2016/appoverview.png)

## <a name="pre-requisites"></a>Предварительные требования
Ниже приведен список предварительных требований, которые требуются перед выполнением этого документа. В этом документе предполагается, что для установки AD FS, так и для создания фермы AD FS.

* Клиентские средства GitHub
* AD FS в Windows Server 2016 или более поздней версии
* Visual Studio 2013 или более поздней версии

## <a name="creating-the-sample-walkthrough"></a>Создание Пошаговое руководство по примеру

### <a name="create-the-application-group-in-ad-fs"></a>Создание группы приложений в AD FS

1. В оснастке управления AD FS, щелкните правой кнопкой мыши **группы приложений** и выберите **добавить группу приложений**.

2. В мастере группы приложений для имени введите любое имя, которое вы предпочитаете, например NativeToDoListAppGroup. Выберите **собственное приложение, доступ к веб-API** шаблона. Нажмите кнопку **Далее**.
 ![Добавление группы приложений](media/native-client-with-ad-fs-2016/addapplicationgroup1.png)

3. На **собственное приложение** странице, обратите внимание, идентификатор, созданный AD FS. Это идентификатор, с которой AD FS будет распознавать общедоступного клиентского приложения. Копировать **идентификатор клиента** значение. Он будет использоваться позже в качестве значения для **ida: ClientId** в коде приложения. При желании можно присвоить любой пользовательский идентификатор. URI перенаправления — это любое значение пароля, поместите примере https://ToDoListClient ![собственного приложения](media/native-client-with-ad-fs-2016/addapplicationgroup2.png)

4. На **настроить веб-API** странице, установите значение идентификатора для веб-API. Например, это должно быть значение **URL-адрес SSL** где должен работать под управлением веб-приложения. Это значение можно получить, щелкнув в свойства проекта TooListServer в решении. Это будет использоваться позже как **todo:TodoListResourceId** значение в **App.config** файла собственного клиентского приложения, а также как **todo:TodoListBaseAddress**.
![Веб-API](media/native-client-with-ad-fs-2016/addapplicationgroup3.png)

5. Пройдите **применяются политики управления доступом** и **Настройка разрешений приложения** со значениями по умолчанию на месте. Странице "Сводка" должна выглядеть следующим.
![Сводка](media/native-client-with-ad-fs-2016/addapplicationgroupsummary.png)

Нажмите кнопку Далее и завершите работу мастера.

### <a name="add-the-nameidentifier-claim-to-the-list-of-claims-issued"></a>Добавьте утверждение NameIdentifier список утверждений, выпущенных
Пример приложения использует значение в утверждение NameIdentifier в разных местах. В отличие от Azure AD службы федерации Active Directory выдает утверждение NameIdentifier по умолчанию. Таким образом нам нужно добавить правило утверждения выдавать утверждение NameIdentifier, таким образом, приложение может использовать правильное значение. В этом примере имя пользователя выдается в качестве значения NameIdentifier для пользователя в маркере.
Чтобы настроить правило для утверждений, откройте группу приложений, который только что создали и дважды щелкните на веб-API. Выберите вкладку "правила преобразования выдачи" и затем нажмите кнопку Добавить правило. Тип правила для утверждений выберите пользовательское правило утверждения, а затем добавьте правило для утверждений, как показано ниже.

```  
c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"]
 => issue(store = "Active Directory", types = ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier"), query = ";givenName;{0}", param = c.Value);
```

![Правило утверждения NameIdentifier](media/native-client-with-ad-fs-2016/addnameidentifierclaimrule.png)

### <a name="modify-the-application-code"></a>Изменение кода приложения

В этом разделе описывается скачать пример веб-API и изменить его в Visual Studio.   Мы будем использовать пример Azure AD, [здесь](https://github.com/Azure-Samples/active-directory-dotnet-native-desktop).  

Загрузите пример проекта, использование Git Bash и введите следующую команду:  

```  
git clone https://github.com/Azure-Samples/active-directory-dotnet-native-desktop  
```  

#### <a name="modify-todolistclient"></a>Изменить ToDoListClient

Этот проект в решении представляет собственного клиентского приложения. Нам нужно убедиться, что клиентское приложение знает:

1. С чего начать прохождения пользователем проверки подлинности при необходимости?
2. Что такое идентификатор этот клиент должен указать для центра проверки подлинности (AD FS)?
3. Что такое идентификатор ресурса, который мы запрашиваем маркер доступа?
4. Что такое базовый адрес веб-API?

Следующие изменения кода необходимо, чтобы получить указанные выше сведения для собственного клиентского приложения.

**App.config**

* Добавьте ключ **ida: центр** со значением, изображающие службы AD FS. Например: https://fs.contoso.com/adfs/ 
* Изменить **ida: ClientId** ключа со значением из **идентификатор клиента** в **собственное приложение** страницы во время создания группы приложений в AD FS. Например 3f07368b-6efd-4f50-a330-d93853f4c855
* Изменить **todo:todo:TodoListResourceId** со значением из **идентификатор** в **настроить веб-API** страницы во время создания группы приложений в AD FS. Например: https://localhost:44321/ 
* Изменить **todo:TodoListBaseAddress** со значением из **идентификатор** в **настроить веб-API** страницы во время создания группы приложений в AD FS. Например: https://localhost:44321/ 
* Установите для параметра **ida: RedirectUri** со значением из **URI перенаправления** в **собственное приложение** страницы во время создания группы приложений в AD FS. Например: https://ToDoListClient 
* Для более удобного чтения можно удалить / комментарий ключ для **ida: клиента** и **ida: AADInstance**.

  ![Конфигурации приложения.](media/native-client-with-ad-fs-2016/app_configfile.PNG)


**MainWindow.xaml.cs**

* Закомментируйте строку для aadInstance, как показано ниже

        // private static string aadInstance = ConfigurationManager.AppSettings["ida:AADInstance"];

* Добавьте значение для центра, как показано ниже

        private static string authority = ConfigurationManager.AppSettings["ida:Authority"];

* Удалите строку для создания **центра** значение из aadInstance и клиента

        private static string authority = String.Format(CultureInfo.InvariantCulture, aadInstance, tenant);

* В функции **MainWindow**, изменить экземпляр authContext для

        authContext = new AuthenticationContext(authority,false);

    ADAL не поддерживает проверку AD FS в качестве центра сертификации, и таким образом, нам приходится передавать флаг значение false для параметра validateAuthority.

  ![Главное окно](media/native-client-with-ad-fs-2016/mainwindow.PNG)

#### <a name="modify-todolistservice"></a>Изменить TodoListService
Изменения в этом проекте —, файл Web.config и Startup.Auth.cs требуется два файла. Чтобы получить правильные значения параметров, нужно изменить файл Web.Config. Чтобы установить веб-API для проверки подлинности AD FS, а не Azure AD, нужно изменить Startup.Auth.cs.

**Web.config**

* Комментарий ключ **ida: клиента** как нам не нужен
* Добавьте ключ для **ida: центр** с значение, указывающее, полное ДОМЕННОЕ имя федерации службы, пример, https://fs.contoso.com/adfs/
* Изменить ключ **ida: аудитории** со значением идентификатора веб-API, указанной в **настроить веб-API** страницы во время добавления группы приложений в AD FS.
* Добавить ключ **ida: AdfsMetadataEndpoint** со значением, соответствующий URL-адрес метаданных федерации AD FS, службу, например: https://fs.contoso.com/federationmetadata/2007-06/federationmetadata.xml

![Файл веб-конфигурации](media/native-client-with-ad-fs-2016/webconfig.PNG)


**Startup.Auth.cs**

Измените функцию ConfigureAuth, как показано ниже

    public void ConfigureAuth(IAppBuilder app)
    {
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
    }

По сути мы настраиваем использовать AD FS и дополнительно указать сведения о метаданных службы федерации Active Directory и для проверки токена проверки подлинности, утверждения "аудитория" должно быть значением, которое требуется веб-API.
Запуск приложения

1. Решение NativeClient-DotNet щелкните правой кнопкой мыши и перейдите к свойствам. Измените запускаемый проект, как показано ниже на несколько запускаемых проектов и настройка TodoListClient и TodoListService запуска.
![Свойства решения](media/native-client-with-ad-fs-2016/solutionproperties.png)

2.  Нажмите кнопку F5 или выберите Отладка > Продолжить в строке меню. Это приведет к запуску собственное приложение и веб-API. Нажмите кнопку "Вход" в собственном приложении, а также появится всплывающее окно интерактивного входа в систему из AD AL и перенаправления для службы AD FS. Введите учетные данные действительного пользователя.
![Вход](media/native-client-with-ad-fs-2016/sign-in.png)

На этом шаге собственное приложение переадресованы в ADFS и у вас есть маркер Идентификации и маркер доступа для веб-API

3.  Введите для этого элемента в текстовом поле и выберите команду Добавить элемент. На этом шаге приложение получает доступ к веб-API, чтобы добавить элемент списка дел и чтобы сделать это, предоставляет маркер доступа к веб-API, полученный из AD FS. Веб-API совпадает со значением аудитории, чтобы убедиться в том, токен предназначено для него и проверяет подпись маркера, используя информацию из метаданных федерации.

![Вход](media/native-client-with-ad-fs-2016/clienttodoadd.png)

## <a name="next-steps"></a>Следующие шаги
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
