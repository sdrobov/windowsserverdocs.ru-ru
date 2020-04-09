---
ms.assetid: 882abec8-0189-4f73-99c5-792987168080
title: Расширенная настройка страниц входа AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 01/16/2019
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: ea149e6b9a5fbf5c0671991a61f9bcda35656022
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859987"
---
# <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>Расширенная настройка страниц входа AD FS

  
## <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>Расширенная настройка AD FS подписи\-на страницах  
AD FS в Windows Server 2012 R2 предоставляет встроенные\-поддержку настройки\-входа. В большинстве этих сценариев все, что требуется, — это сборка\-в командлетах Windows PowerShell.  Рекомендуется использовать встроенные\-в командах Windows PowerShell, чтобы настроить стандартные элементы для AD FS подписывания\-при возможности.  Дополнительные сведения см. [в статье Настройка входа пользователя AD FS](AD-FS-user-sign-in-customization.md) .  
  
В некоторых случаях AD FS администраторам может потребоваться предоставить дополнительные входные\-в интерфейсе, которые невозможно выполнить с помощью существующих команд PowerShell, поставляемых в\-Box AD FS. В некоторых случаях его можно \(в соответствии с рекомендациями, приведенными ниже\) для того, чтобы администраторы настроили\-подписи в дальнейшем, добавив дополнительную логику в **OnLoad. js** , предоставляемую AD FS и выполняемую на всех страницах AD FS.  
  
## <a name="things-to-know-before-you-start"></a>Вопросы, которые необходимо изучить перед началом работы  
  
-   Любое изменение, влияющее на перенаправление потоков или изменение параметров протокола, которые AD FS работает с, не поддерживается.
  
-   Исходная программа OnLoad. js, которая поставляется вместе с веб-темой по умолчанию, содержит код, обрабатывающий отрисовку страниц для различных конструктивных параметров. Рекомендуется не вносить изменения в первоначальное содержимое «OnLoad. js», но добавлять код только в существующий объект OnLoad. js, который обрабатывает пользовательскую логику.  
  
-   AD FS поставляется со встроенной\-в веб-теме, которая называется по умолчанию. Нельзя изменить OnLoad. js веб-темы по умолчанию. Чтобы обновить OnLoad. js, необходимо создать и использовать пользовательскую веб-тему для AD FS подписи\-на страницах.  Сведения о создании пользовательской веб-темы см. в статье [Настройка входа пользователя AD FS](AD-FS-user-sign-in-customization.md) .  
  
-   Тот же OnLoad. js будет выполняться на всех страницах ADFS \(например, форма\-на основе входа, страница обнаружения домашней области и т. д.\). Необходимо убедиться, что код в скрипте выполняется только в том виде, в котором он создан, и не будет выполняться непредвиденным образом.  
  
-   При ссылке на любой HTML-элемент убедитесь, что всегда проверяется наличие элемента перед началом работы с элементом. Это обеспечивает надежность и гарантирует, что пользовательская логика не будет выполняться на страницах, не содержащих этот элемент. Можно просто просмотреть исходный код HTML на AD FS под\-на страницах, чтобы просмотреть существующие элементы.  
  
-   Настоятельно рекомендуется проверить настройки в другой среде и протестировать их перед развертыванием на рабочих AD FS серверах. Это снижает вероятность предоставления конечным пользователям таких настроек до проверки.  
  
## <a name="customizing-the-ad-fs-sign-in-experience-by-using-onloadjs"></a>Настройка\-подписывания AD FS с помощью OnLoad. js  
При настройке OnLoad. js для службы AD FS выполните следующие действия.  
  
#### <a name="customizing-onloadjs-for-the-ad-fs-service"></a>Настройка OnLoad. js для службы AD FS  
  
1.  Чтобы добавить пользовательскую логику в OnLoad. js, необходимо сначала создать пользовательскую веб-тему. Тема, которая поставляется\-\-\-Box, называется по умолчанию. Можно экспортировать тему по умолчанию и воспользоваться ей, чтобы быстро приступить к работе. Следующий командлет создает пользовательскую веб-тему, которая дублирует веб-тему по умолчанию:  
  
    ```  
    New-AdfsWebTheme –Name custom –SourceName default  
  
    ```  
  
2.  Затем можно экспортировать пользовательскую или веб-тему по умолчанию, чтобы получить файл OnLoad. js. Чтобы экспортировать веб-тему, используйте следующий командлет:  
  
    ```  
    Export-AdfsWebTheme –Name default –DirectoryPath c:\theme  
  
    ```  
  
    Вы найдете OnLoad. js в папке script в каталоге, указанном выше, и добавьте пользовательскую логику в скрипт, \(просмотреть варианты использования в разделе "пример" ниже\).  
  
3.  Внесите необходимые изменения, чтобы настроить OnLoad. js в соответствии с вашими нуждами.  
  
4.  Обновите тему с помощью измененной OnLoad. js. Используйте следующий командлет, чтобы применить обновление OnLoad. js к пользовательской веб-теме:  

     Для AD FS в Windows Server 2012 R2:  

    ```  
    Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri='/adfs/portal/script/onload.js';path="c:\theme\script\onload.js"}  
  
    ```  
    Для AD FS в Windows Server 2016:

     ```  
    Set-AdfsWebTheme -TargetName custom -OnLoadScriptPath "c:\ADFStheme\script\onload.js"   
  
    ```  
  
5.  Чтобы применить пользовательскую веб-тему к AD FS, используйте следующий командлет:  
  
    ```  
    Set-AdfsWebConfig -ActiveThemeName custom  
    ```  
  
## <a name="additional-customization-examples"></a>Дополнительные примеры настройки  
Ниже приведены примеры пользовательского кода, добавленного в OnLoad. js для настройки точной\-. При добавлении пользовательского кода всегда добавляйте пользовательский код в нижнюю часть OnLoad. js.  
  
### <a name="example-1-change-sign-in-with-organizational-account-string"></a>Пример 1. изменение "вход с использованием учетной записи организации"  
Форма AD FS по умолчанию\-знак\-на странице имеет название "войти с учетной записью вашей организации" над полями ввода пользователя.  
  
Если вы хотите заменить эту строку собственной строкой, можно добавить следующий код в OnLoad. js.  
  
```  
// Sample code to change "Sign in with organizational account" string.  
  
// Check whether the loginMessage element is present on this page.  
var loginMessage = document.getElementById('loginMessage');  
if (loginMessage)  
{  
       // loginMessage element is present, modify its properties.  
       loginMessage.innerHTML = 'Your company description text';  
}  
  
```  
  
### <a name="example-2-accept-sam-account-name-as-a-login-format-on-an-ad-fs-form-based-sign-in-page"></a>Пример 2. принятие SAM\-имени учетной записи в качестве формата входа в AD FS форме\-знак\-на странице  
Форма AD FS по умолчанию\-знак\-на странице поддерживает формат входа в систему имен участников-пользователей \(UPN\) \(, например <strong>johndoe@contoso.com</strong>\) или доменных имен SAM\-JohnDoe **\(.** **contoso.com\\johndoe**\\\) Если все пользователи поступают из одного и того же домена, и им известно только о SAM\-именах учетных записей, может потребоваться поддержка сценария, в котором пользователи могут войти в систему, используя учетные записи SAM\-только именам пользователей. Для поддержки этого сценария можно добавить следующий код в OnLoad. js, просто замените домен "contoso.com" в примере ниже на домен, который вы хотите использовать.  
  
```  
if (typeof Login != 'undefined'){  
    Login.submitLoginRequest = function () {   
    var u = new InputUtil();  
    var e = new LoginErrors();  
    var userName = document.getElementById(Login.userNameInput);  
    var password = document.getElementById(Login.passwordInput);  
    if (userName.value && !userName.value.match('[@\\\\]'))   
    {  
        var userNameValue = 'contoso.com\\' + userName.value;  
        document.forms['loginForm'].UserName.value = userNameValue;  
    }  
  
    if (!userName.value) {  
       u.setError(userName, e.userNameFormatError);  
       return false;  
    }  
  
    if (!password.value)   
    {  
        u.setError(password, e.passwordEmpty);  
        return false;  
    }  
    document.forms['loginForm'].submit();  
    return false;  
};  
}  
  
```  
  
## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
  

