---
ms.assetid: 882abec8-0189-4f73-99c5-792987168080
title: Расширенная настройка страниц входа AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 01/16/2019
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: e49b18bf5e10de6150603b690095f61a13e59ef2
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70865989"
---
# <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>Расширенная настройка страниц входа AD FS

  
## <a name="advanced-customization-of-ad-fs-sign-in-pages"></a>Расширенная настройка AD FS страниц\-входа  
AD FS в Windows Server 2012 R2 предоставляет встроенную\-поддержку для настройки входа в систему.\- В большинстве этих сценариев все, что требуется,\-являются встроенными командлетами Windows PowerShell.  Рекомендуется использовать встроенные\-команды Windows PowerShell, чтобы настроить стандартные элементы для AD FS входа в систему\-везде, где это возможно.  Дополнительные сведения см. [в статье Настройка входа пользователя AD FS](AD-FS-user-sign-in-customization.md) .  
  
В некоторых случаях AD FS администраторам может потребоваться предоставить дополнительные возможности входа\-, которые невозможно выполнить с помощью существующих команд PowerShell, поставляемых в\-комплекте с AD FS. В некоторых случаях \(можно выполнить следующие\) рекомендации для администраторов по настройке интерфейса входа\-, добавив дополнительную логику к **OnLoad. js** , предоставляемую AD FS и будет выполняться на всех AD FS страницах.  
  
## <a name="things-to-know-before-you-start"></a>Вопросы, которые необходимо изучить перед началом работы  
  
-   Любое изменение, влияющее на перенаправление потоков или изменение параметров протокола, которые AD FS работает с, не поддерживается.
  
-   Исходная программа OnLoad. js, которая поставляется вместе с веб-темой по умолчанию, содержит код, обрабатывающий отрисовку страниц для различных конструктивных параметров. Рекомендуется не вносить изменения в первоначальное содержимое «OnLoad. js», но добавлять код только в существующий объект OnLoad. js, который обрабатывает пользовательскую логику.  
  
-   AD FS поставляется с встроенной\-веб-темой, которая называется по умолчанию. Нельзя изменить OnLoad. js веб-темы по умолчанию. Чтобы обновить OnLoad. js, необходимо создать и использовать пользовательскую веб-тему для AD FS страниц входа\-.  Сведения о создании пользовательской веб-темы см. в статье [Настройка входа пользователя AD FS](AD-FS-user-sign-in-customization.md) .  
  
-   Тот же OnLoad. js будет выполняться на всех страницах \(ADFS, например Страница\-входа на основе форм, страница обнаружения домашней области и т\). д. Необходимо убедиться, что код в скрипте выполняется только в том виде, в котором он создан, и не будет выполняться непредвиденным образом.  
  
-   При ссылке на любой HTML-элемент убедитесь, что всегда проверяется наличие элемента перед началом работы с элементом. Это обеспечивает надежность и гарантирует, что пользовательская логика не будет выполняться на страницах, не содержащих этот элемент. Можно просто просмотреть исходный код HTML на AD FS страницах входа\-, чтобы просмотреть существующие элементы.  
  
-   Настоятельно рекомендуется проверить настройки в другой среде и протестировать их перед развертыванием на рабочих AD FS серверах. Это снижает вероятность предоставления конечным пользователям таких настроек до проверки.  
  
## <a name="customizing-the-ad-fs-sign-in-experience-by-using-onloadjs"></a>Настройка интерфейса входа\-AD FS с помощью OnLoad. js  
При настройке OnLoad. js для службы AD FS выполните следующие действия.  
  
#### <a name="customizing-onloadjs-for-the-ad-fs-service"></a>Настройка OnLoad. js для службы AD FS  
  
1.  Чтобы добавить пользовательскую логику в OnLoad. js, необходимо сначала создать пользовательскую веб-тему. Тема, которая поставляется\-\-\-из комплекта, называется по умолчанию. Можно экспортировать тему по умолчанию и воспользоваться ей, чтобы быстро приступить к работе. Следующий командлет создает пользовательскую веб-тему, которая дублирует веб-тему по умолчанию:  
  
    ```  
    New-AdfsWebTheme –Name custom –SourceName default  
  
    ```  
  
2.  Затем можно экспортировать пользовательскую или веб-тему по умолчанию, чтобы получить файл OnLoad. js. Чтобы экспортировать веб-тему, используйте следующий командлет:  
  
    ```  
    Export-AdfsWebTheme –Name default –DirectoryPath c:\theme  
  
    ```  
  
    Вы найдете OnLoad. js в папке script в каталоге, указанном в приведенном выше командлете Export, и добавите пользовательскую логику в \(скрипт, см. раздел примеры использования ниже\).  
  
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
Ниже приведены примеры пользовательского кода, добавленного в OnLoad. js для выполнения различных задач\-тонкой настройки. При добавлении пользовательского кода всегда добавляйте пользовательский код в нижнюю часть OnLoad. js.  
  
### <a name="example-1-change-sign-in-with-organizational-account-string"></a>Пример 1. изменение "вход с использованием учетной записи организации"  
По умолчанию на\-странице входа\-на основе формы AD FS заголовком "вход с учетной записью организации" над полями ввода пользователя.  
  
Если вы хотите заменить эту строку собственной строкой, можно добавить следующий код в OnLoad. js.  
  
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
  
### <a name="example-2-accept-sam-account-name-as-a-login-format-on-an-ad-fs-form-based-sign-in-page"></a>Пример 2. принятие имени\-учетной записи SAM в качестве формата входа на AD FS\-на странице\-входа на основе формы  
На странице входа\-по\-умолчанию AD FS форм поддерживается формат входа в систему имен \(участников-\) пользователей UPN \(, <strong>johndoe@contoso.com</strong> например, \) или полный домен SAM\-. имена\(учетных записей **contoso\\JohnDoe** или **\\contoso.com JohnDoe.** \) Если все пользователи поступают из одного и того же домена, и они только узнают об\-именах учетных записей SAM, может потребоваться поддержка сценария, в котором пользователи могут войти в систему\-, используя только имена учетных записей SAM. Для поддержки этого сценария можно добавить следующий код в OnLoad. js, просто замените домен "contoso.com" в примере ниже на домен, который вы хотите использовать.  
  
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
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
  

