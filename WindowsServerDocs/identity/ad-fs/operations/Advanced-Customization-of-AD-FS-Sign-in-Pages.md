---
ms.assetid: 882abec8-0189-4f73-99c5-792987168080
title: Расширенная настройка AD FS Sign-in Pages
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 01/16/2019
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: ee7bef2afe61500fe75b2d3c61b92b902f9757fa
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66444260"
---
# <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>Расширенная настройка AD FS Sign-in Pages

  
## <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>Расширенная настройка входа AD FS\-на страницах  
AD FS в Windows Server 2012 R2 обладает встроенной\-в поддержка настройки входа\-в интерфейсе. Для большинства из этих сценариев, встроенный\-в Windows PowerShell командлеты: все, что является обязательным.  Рекомендуется использовать встроенные\-в командах Windows PowerShell могут настраивать стандартные элементы для AD FS входить\-по опыту, когда это возможно.  См. в разделе [Настройка входа пользователя AD FS](AD-FS-user-sign-in-customization.md) Дополнительные сведения.  
  
В некоторых случаях Администраторы AD FS может потребоваться предоставить дополнительные входа\-в действия, которые не являются можно реализовать с помощью существующего команды PowerShell, поставляемых в\-поле с AD FS. В некоторых случаях возможна \(в инструкции, приведенные ниже\) администраторам настраивать знак\-по опыту дальнейшего путем добавления дополнительной логики для **onload.js** , предоставляется службами AD FS и будет выполняться на всех страницах AD FS.  
  
## <a name="things-to-know-before-you-start"></a>Что нужно знать перед началом  
  
-   Любое изменение, которое влияет на потоки перенаправления или изменяет параметры протокола, которые службы AD FS работают с не поддерживается.
  
-   Исходное onload.js, тот, который поставляется с веб-тему по умолчанию, содержит код, который обрабатывает отрисовки страницы для разных форм-факторов. Рекомендуется не изменять исходное содержимое onload.js, но только добавить код существующих onload.js, который обрабатывает пользовательскую логику.  
  
-   AD FS поставляется со встроенными\-в веб-темы, который вызывается по умолчанию. Нельзя изменять onload.js веб-темы по умолчанию. Чтобы обновить onload.js, вам нужно создавать и использовать пользовательские веб-тема для AD FS sign\-на страницах.  См. в разделе [Настройка входа пользователя AD FS](AD-FS-user-sign-in-customization.md) сведения о создании пользовательской веб-темы.  
  
-   Же onload.js будет выполняться на всех страницах ADFS \(ex. Форма\-на страницу входа в систему, страница обнаружения домашней области и др.\). Необходимо убедиться, что код в скрипт только возвращает выполнено, так как оно разработано и неожиданно не запускалась.  
  
-   При ссылке на любой элемент HTML, убедитесь, всегда проверять существование элемент перед обработкой элемента. Это обеспечивает надежность и гарантирует, что пользовательская логика на страницах, которые не содержат этот элемент не может быть выполнен. Можно просто просмотреть исходный код HTML на странице входа AD FS\-на страницах, чтобы просмотреть существующие элементы.  
  
-   Настоятельно рекомендуется для проверки настроек в другую среду и протестировать их, прежде чем развернуть его в рабочей среде серверы AD FS. Это снижает вероятность непреднамеренного раскрытия для этих настроек до проверки на конечных пользователей.  
  
## <a name="customizing-the-ad-fs-sign-in-experience-by-using-onloadjs"></a>Настройка входа в AD FS\-в систему с помощью onload.js  
При настройке onload.js служб AD FS, выполните следующие действия.  
  
#### <a name="customizing-onloadjs-for-the-ad-fs-service"></a>Настройка onload.js служб AD FS  
  
1.  Чтобы добавить пользовательскую логику onload.js, необходимо сначала создать пользовательскую веб-тему. Темы, входящий в комплект поставки out\-из\-\-поле вызывается по умолчанию. Можно экспортировать тему по умолчанию и воспользоваться ей, чтобы быстро приступить к работе. Следующий командлет позволяет создать пользовательскую веб-тему, дублирующую веб-темы по умолчанию:  
  
    ```  
    New-AdfsWebTheme –Name custom –SourceName default  
  
    ```  
  
2.  Затем можно экспортировать данные пользовательской или по умолчанию веб-тему, чтобы получить файл onload.js. Чтобы экспортировать веб-тема, используйте следующий командлет:  
  
    ```  
    Export-AdfsWebTheme –Name default –DirectoryPath c:\theme  
  
    ```  
  
    Вы найдете onload.js в папке скрипта в каталоге, укажите в командлет export выше и добавьте пользовательскую логику в скрипт \(см. в разделе варианты использования в примере ниже в разделе\).  
  
3.  Внести в нее необходимые изменения для настройки onload.js по своему усмотрению.  
  
4.  Замените измененный onload.js темы. Используйте следующий командлет, чтобы применить обновления onload.js пользовательской веб-темы:  

     Для AD FS на Windows Server 2012 R2:  

    ```  
    Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri=’/adfs/portal/script/onload.js’;path="c:\theme\script\onload.js"}  
  
    ```  
    Для AD FS на Windows Server 2016:

     ```  
    Set-AdfsWebTheme -TargetName custom -OnLoadScriptPath "c:\ADFStheme\script\onload.js"   
  
    ```  
  
5.  Для применения пользовательской веб-темы к AD FS, используйте следующий командлет:  
  
    ```  
    Set-AdfsWebConfig -ActiveThemeName custom  
    ```  
  
## <a name="additional-customization-examples"></a>Примеры дополнительных настроек  
Ниже приведены примеры пользовательского кода, добавляемого onload.js для разных fine\-настройки целей. При добавлении пользовательского кода, всегда необходимо добавьте пользовательский код в нижнюю часть onload.js.  
  
### <a name="example-1-change-sign-in-with-organizational-account-string"></a>Пример 1: измените строку «Войти с учетной записью организации»  
По умолчанию AD FS формы\-на основе входа\-странице имеет название «Войти с учетной записью организации» выше полей ввода пользователя.  
  
Если вы хотите заменить эту строку с собственной строки, можно добавить следующий код для onload.js.  
  
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
  
### <a name="example-2-accept-sam-account-name-as-a-login-format-on-an-ad-fs-form-based-sign-in-page"></a>Пример 2: примите SAM\-имя учетной записи с форматом имени входа в AD FS форме\-на основе входа\-на странице  
По умолчанию AD FS формы\-на основе входа\-странице поддерживает формат имени входа имен участника-пользователя \(имена участников-пользователей\) \(к примеру, <strong>johndoe@contoso.com</strong> \) или домена sam\-имен учетных записей \( **contoso\\johndoe** или **contoso.com\\johndoe**\). В случае, если все пользователи из одного домена и только они знают о sam\-имена учетных записей, может потребоваться поддерживать сценарии, где пользователи могут входить в с их помощью sam\-только имена учетной записи. Можно добавить следующий код к onload.js для поддержки этого сценария, просто замените домена «contoso.com» в примере ниже с доменом, который вы хотите использовать.  
  
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
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)  
  

