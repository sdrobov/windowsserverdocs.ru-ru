---
title: Создание метода нестандартную проверку подлинности для AD FS в Windows Server
description: Этот сценарий описывает создание метода нестандартную проверку подлинности для AD FS в Windows Server.
author: billmath
ms.author: billmath
manager: daveba
ms.date: 05/23/2019
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: a638ec25be4fc99b4eccd1d9fa541e640ef9e15c
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280656"
---
# <a name="build-a-custom-authentication-method-for-ad-fs-in-windows-server"></a>Создание метода нестандартную проверку подлинности для AD FS в Windows Server

В этом пошаговом руководстве приводятся инструкции по реализации метода нестандартную проверку подлинности для AD FS в Windows Server 2012 R2. Дополнительные сведения см. в разделе [дополнительных методов проверки подлинности](https://msdn.microsoft.com/library/dn758113\(v=msdn.10\)).


> [!WARNING]
> Пример, в котором вы можете создавать здесь является&nbsp;только в целях обучения. &nbsp;Эти инструкции предназначены для реализации самый простой и наиболее минимальным возможным предоставление необходимые элементы модели.&nbsp; Нет проверки подлинности серверной части, ошибка при обработке или данные конфигурации. 
> <P></P>



## <a name="setting-up-the-development-box"></a>Настройка поле разработки

В этом пошаговом руководстве используется Visual Studio 2012.  Можно создать проект, используя любую среду разработки, можно создать класс .NET для Windows. Так как проект должен быть предназначен .NET 4.5 **BeginAuthentication** и **TryEndAuthentication** методы используют тип **System.Security.Claims.Claim**, являющийся частью .NET 4.5.There версии Framework является одной ссылки, необходимые для проекта:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Ссылку на dll</strong></p></td>
<td><p><strong>Где ее найти</strong></p></td>
<td><p><strong>Требуется для</strong></p></td>
</tr>
<tr class="even">
<td><p>Microsoft.IdentityServer.Web.dll</p></td>
<td><p>Библиотека dll находится в %windir%\ADFS на сервере Windows Server 2012 R2, на котором установлены службы федерации Active Directory.</p>
<p></p>
<p>Эта библиотека dll должны копироваться на компьютере разработчика и явную ссылку в проекте создается.</p></td>
<td><p>Типы интерфейсов, включая IAuthenticationContext, IProofData</p></td>
</tr>
</tbody>
</table>


## <a name="create-the-provider"></a>Создание поставщика

1.  В Visual Studio 2012: Выберите файл -\>New -\>проекта...

2.  Выберите библиотеку классов и убедитесь, что вы используете .NET 4.5.

    ![Создание поставщика](media/ad-fs-build-custom-auth-method/Dn783423.71a57ae1-d53d-462b-a846-5b3c02c7d3f2(MSDN.10).jpg "Создание поставщика")

3.  Создайте копию **Microsoft.IdentityServer.Web.dll** из папки % windir %\\служб федерации Active Directory на сервере Windows Server 2012 R2, где установлен AD FS и вставьте его в папке проекта на компьютере разработки.

4.  В **обозревателе решений**, щелкните правой кнопкой мыши **ссылки** и **добавить ссылку...**

5.  Перейдите к локальной копии **Microsoft.IdentityServer.Web.dll** и **добавить...**

6.  Нажмите кнопку **ОК** для подтверждения новую ссылку:

    ![Создание поставщика](media/ad-fs-build-custom-auth-method/Dn783423.f18df353-9259-4744-b4b6-dd780ce90951(MSDN.10).jpg "Создание поставщика")

    Вы должны теперь настроить для разрешения всех типов, необходимых для поставщика. 

7.  Добавьте новый класс в проект (щелкните правой кнопкой мыши проект, **добавить... Класс...** ) и присвойте ему имя, например **MyAdapter**, как показано ниже:

    ![Создание поставщика](media/ad-fs-build-custom-auth-method/Dn783423.6b6a7a8b-9d66-40c7-8a86-a2e3b9e14d09(MSDN.10).jpg "Создание поставщика")

8.  В новом файле MyAdapter.cs замените существующий код следующим:

        using System;
         using System.Collections.Generic;
         using System.Linq;
         using System.Text;
         using System.Threading.Tasks;
         using System.Globalization;
         using System.IO;
         using System.Net;
         using System.Xml.Serialization;
         using Microsoft.IdentityServer.Web.Authentication.External;
         using Claim = System.Security.Claims.Claim;

         namespace MFAadapter
         {
         class MyAdapter : IAuthenticationAdapter
         {

         }
         }

    Теперь вы сможете F12 (щелкните правой кнопкой мыши — перейти к определению) на IAuthenticationAdapter для просмотра набора элементов требуемому интерфейсу. 

    Затем можно сделать простой реализации из них.

9.  Замените все содержимое класса следующим:

        namespace MFAadapter
         {
         class MyAdapter : IAuthenticationAdapter
         {
         public IAuthenticationAdapterMetadata Metadata
         {
         //get { return new <instance of IAuthenticationAdapterMetadata derived class>; }
         }

         public IAdapterPresentation BeginAuthentication(Claim identityClaim, HttpListenerRequest request, IAuthenticationContext authContext)
         {
         //return new instance of IAdapterPresentationForm derived class

         }

         public bool IsAvailableForUser(Claim identityClaim, IAuthenticationContext authContext)
         {
         return true; //its all available for now

         }

         public void OnAuthenticationPipelineLoad(IAuthenticationMethodConfigData configData)
         {
         //this is where AD FS passes us the config data, if such data was supplied at registration of the adapter

         }

         public void OnAuthenticationPipelineUnload()
         {

         }

         public IAdapterPresentation OnError(HttpListenerRequest request, ExternalAuthenticationException ex)
         {
         //return new instance of IAdapterPresentationForm derived class

         }

         public IAdapterPresentation TryEndAuthentication(IAuthenticationContext authContext, IProofData proofData, HttpListenerRequest request, out Claim[] outgoingClaims)
         {
         //return new instance of IAdapterPresentationForm derived class

         }

         }
         }

10. Мы еще не готовы для создания еще... Существуют две дополнительные интерфейсы для перехода.

    Добавьте два дополнительных класса в проект: один — для метаданных, а другой для представления формы.  Можно добавить их в том же файле, как приведенный выше класс.

        class MyMetadata : IAuthenticationAdapterMetadata
         {

         }

         class MyPresentationForm : IAdapterPresentationForm
         {

         }

11. Затем можно добавить обязательные члены для каждого. Во-первых, метаданные (с полезными встроенных комментариев)

        class MyMetadata : IAuthenticationAdapterMetadata
         {
         //Returns the name of the provider that will be shown in the AD FS management UI (not visible to end users)
         public string AdminName
         {
         get { return "My Example MFA Adapter"; }
         }

         //Returns an array of strings containing URIs indicating the set of authentication methods implemented by the adapter 
         /// AD FS requires that, if authentication is successful, the method actually employed will be returned by the
         /// final call to TryEndAuthentication(). If no authentication method is returned, or the method returned is not
         /// one of the methods listed in this property, the authentication attempt will fail.
         public virtual string[] AuthenticationMethods 
         {
         get { return new[] { "http://example.com/myauthenticationmethod1", "http://example.com/myauthenticationmethod2" }; }
         }

         /// Returns an array indicating which languages are supported by the provider. AD FS uses this information
         /// to determine the best language\locale to display to the user.
         public int[] AvailableLcids
         {
         get
         {
         return new[] { new CultureInfo("en-us").LCID, new CultureInfo("fr").LCID};
         }
         }

         /// Returns a Dictionary containing the set of localized friendly names of the provider, indexed by lcid. 
         /// These Friendly Names are displayed in the "choice page" offered to the user when there is more than 
         /// one secondary authentication provider available.
         public Dictionary<int, string> FriendlyNames
         {
         get
         {
         Dictionary<int, string> _friendlyNames = new Dictionary<int, string>();
         _friendlyNames.Add(new CultureInfo("en-us").LCID, "Friendly name of My Example MFA Adapter for end users (en)");
         _friendlyNames.Add(new CultureInfo("fr").LCID, "Friendly name translated to fr locale");
         return _friendlyNames;
         }
         }

         /// Returns a Dictionary containing the set of localized descriptions (hover over help) of the provider, indexed by lcid. 
         /// These descriptions are displayed in the "choice page" offered to the user when there is more than one 
         /// secondary authentication provider available.
         public Dictionary<int, string> Descriptions
         {
         get 
         {
         Dictionary<int, string> _descriptions = new Dictionary<int, string>();
         _descriptions.Add(new CultureInfo("en-us").LCID, "Description of My Example MFA Adapter for end users (en)");
         _descriptions.Add(new CultureInfo("fr").LCID, "Description translated to fr locale");
         return _descriptions; 
         }
         }

         /// Returns an array indicating the type of claim that the adapter uses to identify the user being authenticated.
         /// Note that although the property is an array, only the first element is currently used.
         /// MUST BE ONE OF THE FOLLOWING
         /// "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"
         /// "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
         /// "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"
         /// "http://schemas.microsoft.com/ws/2008/06/identity/claims/primarysid"
         public string[] IdentityClaims
         {
         get { return new[] { "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" }; }
         }

         //All external providers must return a value of "true" for this property.
         public bool RequiresIdentity
         {
         get { return true; }
         }
        }

    Далее, форме презентации:

        class MyPresentationForm : IAdapterPresentationForm
         {
         /// Returns the HTML Form fragment that contains the adapter user interface. This data will be included in the web page that is presented
         /// to the cient.
         public string GetFormHtml(int lcid)
         {
         string htmlTemplate = Resources.FormPageHtml; //todo we will implement this
         return htmlTemplate;
         }

         /// Return any external resources, ie references to libraries etc., that should be included in 
         /// the HEAD section of the presentation form html. 
         public string GetFormPreRenderHtml(int lcid)
         {
         return null;
         }

         //returns the title string for the web page which presents the HTML form content to the end user
         public string GetPageTitle(int lcid)
         {
         return "MFA Adapter";
         }


~~~
     }
~~~

12. Обратите внимание, «todo» **Resources.FormPageHtml** элемент выше. 

   Вы можете исправить ее в минуты, но сначала давайте добавить окончательный требуется операторов return, исходя из только что реализованный типов, к классу начальной MyAdapter.  Чтобы сделать это, добавьте элементы в *курсив* ниже для существующей реализацией IAuthenticationAdapter:

       Класс MyAdapter: IAuthenticationAdapter     {     public IAuthenticationAdapterMetadata Metadata     {     //get { return new <instance of IAuthenticationAdapterMetadata derived class>; }     get { return new MyMetadata(); }     }

        public IAdapterPresentation BeginAuthentication(Claim identityClaim, HttpListenerRequest request, IAuthenticationContext authContext)
        {
        //return new instance of IAdapterPresentationForm derived class
        return new MyPresentationForm();
        }

        public bool IsAvailableForUser(Claim identityClaim, IAuthenticationContext authContext)
        {
        return true; //its all available for now
        }

        public void OnAuthenticationPipelineLoad(IAuthenticationMethodConfigData configData)
        {
        //this is where AD FS passes us the config data, if such data was supplied at registration of the adapter

        }

        public void OnAuthenticationPipelineUnload()
        {

        }

        public IAdapterPresentation OnError(HttpListenerRequest request, ExternalAuthenticationException ex)
        {
        //return new instance of IAdapterPresentationForm derived class
        return new MyPresentationForm();
        }

        public IAdapterPresentation TryEndAuthentication(IAuthenticationContext authContext, IProofData proofData, HttpListenerRequest request, out Claim[] outgoingClaims)
        {
        //return new instance of IAdapterPresentationForm derived class
        outgoingClaims = new Claim[0];
        return new MyPresentationForm();
        }

        }

13. Теперь для файла ресурсов, содержащую фрагмент html. Создайте новый текстовый файл в папке проекта со следующим содержимым:

       <div id="loginArea">
        <form method="post" id="loginForm" >
        <!-- These inputs are required by the presentation framework. Do not modify or remove -->
        <input id="authMethod" type="hidden" name="AuthMethod" value="%AuthMethod%"/>
        <input id="context" type="hidden" name="Context" value="%Context%"/>
        <!-- End inputs are required by the presentation framework. -->
        <p id="pageIntroductionText">Это содержимое предоставляется пример адаптера многофакторной проверки Подлинности. Запрос входных данных должны быть представлены ниже.</p>
        <label for="challengeQuestionInput" class="block">Текст вопроса</label>
        <input id="challengeQuestionInput" name="ChallengeQuestionAnswer" type="text" value="" class="text" placeholder="Answer placeholder" />
        <div id="submissionArea" class="submitMargin">
        <input id="submitButton" type="submit" name="Submit" value="Submit" onclick="return AuthPage.submitAnswer()"/>
        </div>
        </form>
        <div id="intro" class="groupMargin">
        <p id="supportEmail">Сведения о поддержке</p>
        </div>
        <script type="text/javascript" language="JavaScript">
        //<![CDATA[
        function AuthPage() { }
        AuthPage.submitAnswer = function () { return true; };
        //]]>
        </script></div>

14. Выберите **проекта -\>добавить компонент... Ресурсы** файл и назовите файл **ресурсы**и нажмите кнопку **добавить:**

   ![Создание поставщика](media/ad-fs-build-custom-auth-method/Dn783423.3369ad8f-f65f-4f36-a6d5-6a3edbc1911a(MSDN.10).jpg "Создание поставщика")

15. Затем в **Resources.resx** файл, выберите **добавить ресурс... Добавление существующего файла**.  Перейдите в текстовый файл (содержащий фрагмент html) сохраненной выше.

   Убедитесь, что ваш код GetFormHtml разрешает имя нового ресурса правильно, префикс имени файла (RESX-файл) ресурсы, за которым следует имя самого ресурса.

       public string GetFormHtml(int lcid)    {     string htmlTemplate = Resources.MfaFormHtml; //Resxfilename.resourcename     return htmlTemplate;    }

   Теперь можно создавать.

## <a name="build-the-adapter"></a>Создание адаптера

Адаптер должен быть построен в сборки со строгим именем .NET, которая может устанавливаться в глобальный кэш СБОРОК в Windows.  Для этого в проекте Visual Studio, выполните следующие действия:

1.  Щелкните правой кнопкой мыши имя проекта в обозревателе решений и щелкните **свойства**.

2.  На **подписывание** вкладке **подписать сборку** и выберите **\<New... \>** под **выберите файл ключа строгого имени:**  Введите имя файла ключа и пароль и нажмите кнопку **ОК**.  Затем убедитесь, **подписать сборку** проверяется и **только отложенная подпись** не установлен.  Свойства **подписывание** страница должна выглядеть следующим образом:

    ![сборки поставщика](media/ad-fs-build-custom-auth-method/Dn783423.0b1a1db2-d64e-4bb8-8c01-ef34296a2668(MSDN.10).jpg "сборки поставщика")

3.  Затем выполните сборку решения.

## <a name="deploy-the-adapter-to-your-ad-fs-test-machine"></a>Развертывание адаптера на компьютере тестирования AD FS

Прежде чем внешнего поставщика может быть вызвана AD FS, он должны регистрироваться в системе.  Поставщики адаптер должен предоставить установщик, который выполняет необходимые для установки действий, включая установку в глобальный кэш СБОРОК, а установщик должен поддерживать регистрацию в AD FS.  Если это не будет сделано, администратор должен выполнить следующие действия Windows PowerShell.  Включить отладку и тестирование в лабораторной среде можно использовать следующие действия.

### <a name="prepare-the-test-ad-fs-machine"></a>Подготовьте компьютер тестирования AD FS

Скопируйте файлы и добавить в глобальный кэш СБОРОК.

1.  Убедитесь, что у вас есть Windows Server 2012 R2 компьютера или виртуальной машины.

2.  Установите службу роли AD FS и настроить ферму с по крайней мере один узел.

    Подробные инструкции для настройки сервера федерации в лабораторной среде, см. в разделе [Windows Server 2012 R2 AD FS Deployment Guide](https://msdn.microsoft.com/library/dn486820\(v=msdn.10\)).

3.  Скопируйте инструментов Gacutil.exe на сервер.

    Gacutil.exe можно найти в **% homedrive %\\Program Files (x86)\\пакеты SDK для Microsoft\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools\\** на компьютере под управлением Windows 8.  Необходимо будет **gacutil.exe** сам файл, а также **1033**, **en US**и других папок локализованный ресурс ниже **NETFX 4.0 Tools** расположение.

4.  Скопируйте файлы поставщика (один или несколько строгое имя со знаком DLL-файлы) в одной папке с **gacutil.exe** (расположение является исключительно для удобства)

5.  Добавьте файлы .dll в глобальный кэш сборок, на каждом сервере федерации AD FS в ферме:

    Пример: с помощью командной строки программы GACutil.exe добавить библиотеку dll в глобальный кэш сборок: `C:\>.\gacutil.exe /if .\<yourdllname>.dll`

    Чтобы просмотреть Результирующая запись в глобальный кэш СБОРОК:`C:\>.\gacutil.exe /l <yourassemblyname>`

6.  

### <a name="register-your-provider-in-ad-fs"></a>Регистрация поставщика в AD FS

После выше предварительным требованиям, откройте командное окно Windows PowerShell на сервере федерации и введите следующие команды (Обратите внимание, что при использовании фермы серверов федерации, который использует внутреннюю базу данных Windows, необходимо выполнить эти команды основной сервер федерации в ферме):

1.  `Register-AdfsAuthenticationProvider –TypeName YourTypeName –Name “AnyNameYouWish” [–ConfigurationFilePath (optional)]`

    Где YourTypeName — это имя строгий тип .NET: «YourDefaultNamespace.YourIAuthenticationAdapterImplementationClassName имя_сборки, версия = YourAssemblyVersion, язык и региональные параметры = neutral, PublicKeyToken = YourPublicKeyTokenValue, processorArchitecture = MSIL»

    Регистрирует внешний поставщик в AD FS, с именем, предоставленного как AnyNameYouWish выше.

2.  Перезапустите службу AD FS (например с помощью оснастки служб Windows).

3.  Выполните следующую команду: `Get-AdfsAuthenticationProvider`.

    Он показан поставщика как одного из поставщиков в системе.

    Пример.

        PS C:\>$typeName = "MFAadapter.MyAdapter, MFAadapter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e675eb33c62805a0, processorArchitecture=MSIL”
        PS C:\>Register-AdfsAuthenticationProvider -TypeName $typeName -Name “MyMFAAdapter”
        PS C:\>net stop adfssrv
        PS C:\>net start adfssrv

    Если у вас есть служба регистрации устройств в вашей среде AD FS включена, также выполните следующее:  `PS C:\>net start drs`

    Чтобы проверить зарегистрированный поставщик, используйте следующую команду:`PS C:\>Get-AdfsAuthenticationProvider`.

    Он показан поставщика как одного из поставщиков в системе.

### <a name="create-the-ad-fs-authentication-policy-that-invokes-your-adapter"></a>Создать политику проверки подлинности AD FS, которая вызывает адаптер

#### <a name="create-the-authentication-policy-using-the-ad-fs-management-snap-in"></a>Создание политики проверки подлинности, используя оснастку управления AD FS

1.  Откройте оснастку управления AD FS (с помощью диспетчера сервера **средства** меню).

2.  Нажмите кнопку **политики проверки подлинности**.

3.  В центральной области в разделе **многофакторной проверки подлинности**, нажмите кнопку **изменить** ссылку справа от **глобальные параметры**.

4.  В разделе **выберите Дополнительные методы проверки подлинности** в нижней части страницы, установите флажок для AdminName вашего поставщика. Щелкните **Применить**.

5.  Для предоставления «триггер» для вызова многофакторной проверки Подлинности с помощью адаптера, в разделе **расположения** выберите оба варианта **экстрасети** и **интрасети**, например. Нажмите кнопку **ОК**. (Чтобы настроить триггеры по проверяющей стороне, см. в разделе «Создание политики проверки подлинности с помощью Windows PowerShell» ниже.)

6.  Проверьте результаты, используя следующие команды:

    Сначала с помощью `Get-AdfsGlobalAuthenticationPolicy`. Вы должны увидеть поставщику имя как одно из значений AdditionalAuthenticationProvider.

    Затем с помощью `Get-AdfsAdditionalAuthenticationRule`. Вы увидите правила для экстрасети и интрасети, которые настроены в результате выбранные параметры политики администратора пользовательского интерфейса.

#### <a name="create-the-authentication-policy-using-windows-powershell"></a>Создание политики проверки подлинности, с помощью Windows PowerShell

1.  Во-первых включите поставщик в глобальную политику:

    `PS C:\>Set-AdfsGlobalAuthenticationPolicy -AdditionalAuthenticationProvider “YourAuthProviderName”`


~~~
> [!NOTE]
> Note that the value provided for the AdditionalAuthenticationProvider parameter corresponds to the value you provided for the “Name” parameter in the Register-AdfsAuthenticationProvider cmdlet above and to the “Name” property from Get-AdfsAuthenticationProvider cmdlet output. 
> <P></P>


Example:`PS C:\>Set-AdfsGlobalAuthenticationPolicy –AdditionalAuthenticationProvider “MyMFAAdapter”`
~~~

2. Далее настройте правила глобальный или проверяющая сторона определенному триггеру многофакторной проверки Подлинности.

   Пример 1: чтобы создать глобальное правило, чтобы требовать прохождение MFA для внешних запросов:`PS C:\>Set-AdfsAdditionalAuthenticationRule –AdditionalAuthenticationRules 'c:[type == "http://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork", value == "false"] => issue(type = "http://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod", value = "http://schemas.microsoft.com/claims/multipleauthn" );'`

   Пример 2: создание многофакторной проверки Подлинности правила, чтобы требовать многофакторную Идентификацию для внешние запросы к определенной проверяющей стороной сторонних.  (Обратите внимание, что отдельные поставщики невозможно подключить к отдельным проверяющие стороны в AD FS в Windows Server 2012 R2).

       PS C:\>$rp = Get-AdfsRelyingPartyTrust –Name <Relying Party Name>
       PS C:\>Set-AdfsRelyingPartyTrust –TargetRelyingParty $rp –AdditionalAuthenticationRules 'c:[type == "http://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork", value == "false"] => issue(type = "http://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod", value = "http://schemas.microsoft.com/claims/multipleauthn" );'

### <a name="authenticate-with-mfa-using-your-adapter"></a>Проверка подлинности с помощью многофакторной проверки Подлинности с помощью адаптера

Наконец выполните следующие действия, чтобы протестировать адаптер.

1.  Убедитесь, тип глобальную основную проверку подлинности AD FS работает в режиме проверки подлинности форм для экстрасети и интрасети (Это упрощает вашей демонстрационной для проверки подлинности как пользователь)

    1.  В AD FS оснастки, в разделе **политики проверки подлинности**в **основной проверки подлинности** область, нажмите кнопку **изменить** рядом с полем **глобальные параметры**.

        1.  Или просто нажмите кнопку **основной** вкладку **политики многофакторной идентификации** пользовательского интерфейса.

2.  Убедитесь, **проверки подлинности форм** проверяется единственный параметр метода проверки подлинности интрасети и экстрасети.  Нажмите кнопку **ОК**.

3.  Откройте, инициированном поставщиком Удостоверений единого входа HTML-страницу (https://\<fsname\>/adfs/ls/idpinitiatedsignon.htm) и войдите в систему качестве допустимого пользователя AD в тестовой среде.

4.  Введите учетные данные для основной проверки подлинности.

5.  Вы должны увидеть многофакторной проверки Подлинности форм, отображается страница с проблемой примеры вопросов. 

    При наличии более чем один адаптер, настроенный понятное имя выше появится на странице Выбор многофакторной проверки Подлинности.

    ![Проверка подлинности с адаптером](media/ad-fs-build-custom-auth-method/Dn783423.c98d2712-cbd3-4cb9-ac03-2838b81c4f63(MSDN.10).jpg "проверка подлинности с адаптером")

    ![Проверка подлинности с адаптером](media/ad-fs-build-custom-auth-method/Dn783423.fd3aefc0-ef6c-4a8c-a737-4914c78ff2d2(MSDN.10).jpg "проверка подлинности с адаптером")

Теперь у вас есть действующая реализация интерфейса, и вы знаете, принцип работы модели. Вы можете trym в качестве дополнительных примеров устанавливать точки останова в BeginAuthentication, а также TryEndAuthentication.  Обратите внимание на то, как BeginAuthentication выполняется, когда пользователь вводит сначала формы многофакторной проверки Подлинности, в то время как TryEndAuthentication будет активироваться по каждой отправки формы.

## <a name="update-the-adapter-for-successful-authentication"></a>Обновление адаптера для успешной проверки подлинности

Но wait – пример адаптера будет не проходят проверку подлинности\!  Это обусловлено ничего не в коде возвращает значение null для TryEndAuthentication.

Выполнив указанные выше действия, вы создали реализация основных адаптера и добавляемый сервер AD FS.  Можно получить на страницу многофакторной проверки Подлинности форм, но вы не можете еще прошел проверку подлинности, поскольку правильный логики еще не добавляют в реализации TryEndAuthentication.  Так что давайте добавим.

Вспомните TryEndAuthentication реализации:

    public IAdapterPresentation TryEndAuthentication(IAuthenticationContext authContext, IProofData proofData, HttpListenerRequest request, out Claim[] outgoingClaims)
     {
     //return new instance of IAdapterPresentationForm derived class
     outgoingClaims = new Claim[0];
     return new MyPresentationForm();

     }

Давайте обновим его, он не всегда возвращает MyPresentationForm().  Для этого можно создать один метод простая служебная программа внутри класса:

    static bool ValidateProofData(IProofData proofData, IAuthenticationContext authContext)
     {
     if (proofData == null || proofData.Properties == null || !proofData.Properties.ContainsKey("ChallengeQuestionAnswer"))
     {
     throw new ExternalAuthenticationException("Error - no answer found", authContext);
     }

     if ((string)proofData.Properties["ChallengeQuestionAnswer"] == "adfabric")
     {
     return true;
     }
     else
     {
     return false;
     }
     }

Затем обновите TryEndAuthentication, как показано ниже:

    public IAdapterPresentation TryEndAuthentication(IAuthenticationContext authContext, IProofData proofData, HttpListenerRequest request, out Claim[] outgoingClaims)
     {
     outgoingClaims = new Claim[0];
     if (ValidateProofData(proofData, authContext))
     {
     //authn complete - return authn method
     outgoingClaims = new[] 
     {
     // Return the required authentication method claim, indicating the particulate authentication method used.
     new Claim( "http://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod", 
     "http://example.com/myauthenticationmethod1" )
     };
     return null;
     }
     else
     {
     //authentication not complete - return new instance of IAdapterPresentationForm derived class
     return new MyPresentationForm();
     }
     }

Теперь у вас есть для обновления адаптера в окне "Тест".  Вы необходимо сначала отменить политику AD FS, затем отменить регистрацию из службы федерации Active Directory перезапустите AD FS, то удалить DLL-файл из глобального кэша СБОРОК, затем добавьте новые DLL-файл в глобальный кэш сборок, затем зарегистрировать его в AD FS, перезапустите службы федерации Active Directory и повторной настройки политики AD FS.

## <a name="deploy-and-configure-the-updated-adapter-on-your-test-ad-fs-machine"></a>Развертывание и настройка обновленного адаптера при тестировании машины AD FS

### <a name="clear-ad-fs-policy"></a>Очистить политику AD FS

Очистить все MFA связанные флажки в пользовательском Интерфейсе многофакторной проверки Подлинности, показано ниже, нажмите OK.

![очистить политику](media/ad-fs-build-custom-auth-method/Dn783423.c111b4e7-5b05-413c-8b0f-222a0e91ac1f(MSDN.10).jpg "очистить политику")

### <a name="unregister-provider-windows-powershell"></a>Отменяет регистрацию поставщика (Windows PowerShell)

`PS C:\> Unregister-AdfsAuthenticationProvider –Name “YourAuthProviderName”`

Пример:`PS C:\> Unregister-AdfsAuthenticationProvider –Name “MyMFAAdapter”`

Обратите внимание на то, что значение, которое передается для «Name» — «Name» совпадает со значением, введенным в командлет Register-AdfsAuthenticationProvider.  Это также свойство «Name», которые выходят из Get-AdfsAuthenticationProvider.

Обратите внимание на то, что прежде чем отменить регистрацию "Поставщик", необходимо удалить поставщик из AdfsGlobalAuthenticationPolicy (либо, сняв флажки, выбранные в оснастке управления AD FS, либо с помощью Windows PowerShell.)

Обратите внимание на то, что службы AD FS должна быть перезапущена после выполнения этой операции.

### <a name="remove-assembly-from-gac"></a>Удалить сборку из глобального кэша СБОРОК

1.  Во-первых используйте следующую команду, чтобы найти полное строгое имя операции:`C:\>.\gacutil.exe /l <yourAdapterAssemblyName>`

    Пример:`C:\>.\gacutil.exe /l mfaadapter`

2.  Выполните следующую команду, чтобы удалить его из глобального кэша СБОРОК.`.\gacutil /u “<output from the above command>”`

    Пример:`C:\>.\gacutil /u “mfaadapter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e675eb33c62805a0, processorArchitecture=MSIL”`

### <a name="add-the-updated-assembly-to-gac"></a>Добавить обновленную сборку в глобальный кэш СБОРОК

Убедитесь, что вы сначала вставьте обновленной DLL-файл локально. `C:\>.\gacutil.exe /if .\MFAAdapter.dll`

### <a name="view-assembly-in-the-gac-cmd-line"></a>Представление сборки в глобальном кэше СБОРОК (Командная строка)

`C:\> .\gacutil.exe /l mfaadapter`

### <a name="register-your-provider-in-ad-fs"></a>Регистрация поставщика в AD FS

1.  `PS C:\>$typeName = "MFAadapter.MyAdapter, MFAadapter, Version=1.0.0.1, Culture=neutral, PublicKeyToken=e675eb33c62805a0, processorArchitecture=MSIL”`

2.  `PS C:\>Register-AdfsAuthenticationProvider -TypeName $typeName -Name “MyMFAAdapter1”`

3.  Перезапустите службу AD FS.

### <a name="create-the-authentication-policy-using-the-ad-fs-management-snap-in"></a>Создание политики проверки подлинности, используя оснастку управления AD FS

1.  Откройте оснастку управления AD FS (с помощью диспетчера сервера **средства** меню).

2.  Нажмите кнопку **политики проверки подлинности**.

3.  В разделе **многофакторной проверки подлинности**, нажмите кнопку **изменить** ссылку справа от **глобальные параметры**.

4.  В разделе **выберите Дополнительные методы проверки подлинности**, установите флажок для AdminName вашего поставщика. Щелкните **Применить**.

5.  Чтобы предоставить «триггер» для вызова многофакторной проверки Подлинности с помощью адаптера, в списке расположений выберите оба варианта **экстрасети** и **интрасети**, например. Нажмите кнопку **ОК**.

### <a name="authenticate-with-mfa-using-your-adapter"></a>Проверка подлинности с помощью многофакторной проверки Подлинности с помощью адаптера

Наконец выполните следующие действия, чтобы протестировать адаптер.

1.  Убедитесь, тип глобальную основную проверку подлинности AD FS настраивается как **проверки подлинности форм** для экстрасети и интрасети (Это упрощает для проверки подлинности как пользователь).

    1.  Управление AD FS оснастки, в разделе **политики проверки подлинности**в **основной проверки подлинности** область, нажмите кнопку **изменить** рядом с полем **глобальные параметры**.

        1.  Или просто нажмите кнопку **основной** вкладку в пользовательском Интерфейсе политики многофакторной идентификации.

2.  Убедитесь, **проверки подлинности форм** проверяется единственным вариантом для обоих **экстрасети** и **интрасети** метод проверки подлинности.  Нажмите кнопку **ОК**.

3.  Откройте, инициированном поставщиком Удостоверений единого входа HTML-страницу (https://\<fsname\>/adfs/ls/idpinitiatedsignon.htm) и войдите в систему качестве допустимого пользователя AD в тестовой среде.

4.  Введите учетные данные для основной проверки подлинности.

5.  Вы должны увидеть многофакторной проверки Подлинности форм, страница с текстом запроса примере выводится на экран.

    1.  При наличии более чем один адаптер, настроенный с понятное имя появится на странице Выбор многофакторной проверки Подлинности.

Вы увидите успешного входа в систему, при вводе «adfabric» на странице проверки подлинности многофакторной проверки Подлинности.

![Войдите с помощью адаптера](media/ad-fs-build-custom-auth-method/Dn783423.630d8a91-3bfe-4cba-8acf-03eae21530ee(MSDN.10).jpg "войдите с помощью адаптера")

![Войдите с помощью адаптера](media/ad-fs-build-custom-auth-method/Dn783423.c340fa73-f70f-4870-b8dd-07900fea4469(MSDN.10).jpg "войдите с помощью адаптера")

## <a name="see-also"></a>См. также

#### <a name="other-resources"></a>Прочие ресурсы

[Дополнительные методы проверки подлинности](https://msdn.microsoft.com/library/dn758113\(v=msdn.10\))  
[Управление рисками с помощью дополнительной многофакторной проверки подлинности для уязвимых приложений](https://msdn.microsoft.com/library/dn280949\(v=msdn.10\))

