---
ms.assetid: 882abec8-0189-4f73-99c5-792987168080
title: "Дополнительная настройка AD FS Sign-in страниц"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/13/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: ea01d0ff2a38c4fef2f68091608d777d8412e91b
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>Дополнительная настройка AD FS Sign-in страниц

>Область применения: Windows Server 2016, Windows Server 2012 R2
  
## <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>Дополнительная настройка страниц AD FS входа  
AD FS в Windows Server 2012 R2 поддерживает встроенных Настройка входа в систему. Для большинства из этих сценариев встроенных командлетов Windows PowerShell — это все, что требуется.  Рекомендуется использовать команды Windows PowerShell встроенных могут настраивать стандартные элементы для входа в систему в AD FS по возможности.  В разделе [настройки входа пользователя AD FS](AD-FS-user-sign-in-customization.md) Дополнительные сведения.  
  
В некоторых случаях Администраторы AD FS может потребоваться предоставить дополнительные возможности входа в систему, не невозможно с помощью команды PowerShell, входящие в поле ввода количества с AD FS. В некоторых случаях есть возможность \ (в пределах below\ рекомендации) администраторы могут настроить, добавив дополнительную логику для входа в систему дальнейшей **onload.js** предоставляется с помощью AD FS, которая будет выполняться на всех страницах AD FS.  
  
## <a name="things-to-know-before-you-start"></a>Что нужно знать перед началом  
  
-   Изменения, которые затрагивает перенаправления потоков или изменяет параметры протокола, службы федерации Active Directory работает с не поддерживается.
  
-   Исходный onload.js, приложение, которое поставляется вместе с веб-тему по умолчанию, содержит кода, который обрабатывает отрисовки страницы для различных форм-факторы. Рекомендуется не изменять исходное содержимое на onload.js, но только добавить кода существующих onload.js, который обрабатывает пользовательскую логику.  
  
-   AD FS поставляется с темой встроенных в Интернете, который вызывается по умолчанию. Не удается изменить onload.js веб-темы по умолчанию. Чтобы обновить onload.js, необходимо создать и использовать настраиваемые веб-темы для страниц входа AD FS.  В разделе [настройки входа пользователя AD FS](AD-FS-user-sign-in-customization.md) сведения о том, как создать пользовательскую веб-тему.  
  
-   Же onload.js выполняется на всех \(ex. страницы служб федерации Active Directory страница входа на основе form\, страница обнаружения домашней области и и т. д. \). Необходимо, чтобы убедиться в том, что код в ваш скрипт только получает выполнена, так как оно разработано и не выполняются неожиданно.  
  
-   При ссылке на любой элемент HTML, убедитесь, что всегда проверяйте наличие элемента перед обработкой элемента. Это обеспечивает надежность и гарантирует, что пользовательская логика не может быть выполнен на страницы, которые не содержат данный элемент. Можно просто просмотреть исходный код HTML на страницы входа AD FS для просмотра существующих элементов.  
  
-   Настоятельно рекомендуется проверить настроек в другую среду и проверить их перед его выпуском на производственных серверов AD FS. Это снижает вероятность конечных пользователей, предоставление этих настроек перед проверку.  
  
## <a name="customizing-the-ad-fs-sign-in-experience-by-using-onloadjs"></a>Настройка AD FS входа в систему с помощью onload.js  
При настройке onload.js для службы AD FS, выполните следующие действия.  
  
#### <a name="customizing-onloadjs-for-the-ad-fs-service"></a>Настройка onload.js для службы AD FS  
  
1.  Чтобы добавить свою собственную логику onload.js, необходимо сначала создать пользовательскую веб-тему. Тема, предоставляемая в заводской out\-of\-the\-box называется по умолчанию. Можно экспортировать тему по умолчанию и воспользоваться ей, чтобы быстро приступить к работе. Следующий командлет создает пользовательскую веб-тему, дублирующую веб-тему по умолчанию:  
  
    ```  
    New-AdfsWebTheme –Name custom –SourceName default  
  
    ```  
  
2.  Затем можно экспортировать пользовательский или веб-темы для получения файла onload.js по умолчанию. Чтобы экспортировать веб-тему, используйте следующий командлет:  
  
    ```  
    Export-AdfsWebTheme –Name default –DirectoryPath c:\theme  
  
    ```  
  
    Вы найдете onload.js в папке сценария в каталоге указать в командлет export выше и добавить свою собственную логику скрипт \ (см. в разделе вариантов использования в below\ разделе примере).  
  
3.  Внести необходимые изменения для настройки onload.js основании потребностями.  
  
4.  Обновление темы с измененной onload.js. Для применения пользовательской веб-темы onload.js обновления, используйте следующий командлет:  
  
    ```  
    Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri=’/adfs/portal/script/onload.js’;path="c:\theme\script\onload.js"}  
  
    ```  
  
5.  Для применения пользовательской веб-темы к AD FS, используйте следующий командлет:  
  
    ```  
    Set-AdfsWebConfig -ActiveThemeName custom  
    ```  
  
## <a name="additional-customization-examples"></a>Примеры дополнительных настроек  
Ниже приведены примеры пользовательский код, добавленный к onload.js для разных fine\ Настройка целей. При добавлении пользовательский код, всегда необходимо добавьте пользовательский код в нижнюю часть onload.js.  
  
### <a name="example-1-change-sign-in-with-organizational-account-string"></a>Пример 1: измените строку «Вход с учетной записью организации»  
Страница по умолчанию AD FS на основе form\ входа имеет название «Войдите с помощью учетной записи организации» выше полях пользовательского ввода.  
  
Если вы хотите заменить эту строку свою собственную строку, можно добавить следующий код для onload.js.  
  
```  
// Sample code to change “Sign in with organizational account” string.  
  
// Check whether the loginMessage element is present on this page.  
var loginMessage = document.getElementById('loginMessage');  
if (loginMessage)  
{  
       // loginMessage element is present, modify its properties.  
       loginMessage.innerHTML = 'Your company description text';  
}  
  
```  
  
### <a name="example-2-accept-sam-account-name-as-a-login-format-on-an-ad-fs-form-based-sign-in-page"></a>Пример 2: примите имя учетной записи SAM\ как формат входа в службы федерации Active Directory на основе form\ одной странице  
Формат входа Служб федерации Active Directory на основе form\ одной странице поддерживает \(UPNs\) \(for example, ** johndoe@contoso.com **\) имена участника-пользователя или домена по умолчанию полные имена учетной записи sam\ \ (**contoso\\johndoe** или **contoso.com\\johndoe**\). В случае всех пользователей поступают из того же домена, и они знать имена учетных записей sam\, может потребоваться поддерживает сценарии, где пользователи могут войти в их использование только имена учетной записи sam\. Можно добавить следующий код для onload.js для поддержки этого сценария, просто замените домена «contoso.com» в примере ниже с доменом, который вы хотите использовать.  
  
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
  
## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)  
  

