---
ms.assetid: 24c4b9bb-928a-4118-acf1-5eb06c6b08e5
title: Настройка AD FS 2016 и Azure MFA
description: ''
ms.author: billmath
author: billmath
manager: mtillman
ms.date: 01/28/2019
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 62b366b8fa388319a758ab853d28d1c49cb1bf06
ms.sourcegitcommit: a3958dba4c2318eaf2e89c7532e36c78b1a76644
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719719"
---
# <a name="configure-azure-mfa-as-authentication-provider-with-ad-fs"></a>Настройка многофакторной Идентификации Azure в качестве поставщика проверки подлинности с AD FS

Если ваша организация использует федерацию с Azure AD, можно использовать многофакторную идентификацию Azure к защищенным ресурсам AD FS, так и локально и в облаке. Azure MFA позволяет избежать пароли и предоставить более безопасный способ проверки подлинности.  Начиная с Windows Server 2016, теперь можно настроить Azure MFA для основной проверки подлинности или использовать его в качестве дополнительного поставщика проверки подлинности. 
  
В отличие от и в случае с AD FS в Windows Server 2012 R2, адаптер Azure MFA AD FS 2016 напрямую интегрируется с Azure AD и не требует локальном сервере Azure MFA.   Адаптер Azure MFA встроен в Windows Server 2016, и нет необходимости для дополнительной установки.


## <a name="registering-users-for-azure-mfa-with-ad-fs"></a>Регистрация пользователей для Azure MFA с AD FS

Службы федерации Active Directory не поддерживает встроенный &#34;проверки копии&#34;, или регистрации информации проверки безопасности Azure MFA, например номер телефона или мобильного приложения. Это означает, что пользователи должны получить подтверждены вверх, посетив [ https://account.activedirectory.windowsazure.com/Proofup.aspx ](https://account.activedirectory.windowsazure.com/Proofup.aspx) перед использованием Azure MFA для проверки подлинности для приложений AD FS. Когда пользователь имеет не еще подтверждены копии в Azure AD попытается выполнить проверку подлинности с помощью Azure MFA в AD FS, они будут получать ошибку AD FS.  Как администратор AD FS вы можете настроить этот интерфейс ошибки, чтобы помочь пользователю на странице подтверждения, вместо этого.  Это можно сделать с помощью настройки onload.js обнаруживать строку сообщения об ошибке на странице AD FS и Показать новое сообщение, чтобы помочь пользователям приходится открывать [ https://aka.ms/mfasetup ](https://aka.ms/mfasetup), а затем повторите попытку проверки подлинности. Подробные инструкции см. в разделе «Настройка AD FS веб-страницы предоставляют пользователям указания по регистрации способов проверки подлинности многофакторной проверки Подлинности» ниже в этой статье.

>[!NOTE]
> Ранее пользователям проходить проверку подлинности с многофакторной проверкой Подлинности для регистрации (посещения [ https://account.activedirectory.windowsazure.com/Proofup.aspx ](https://account.activedirectory.windowsazure.com/Proofup.aspx), например через ярлык [ https://aka.ms/mfasetup ](https://aka.ms/mfasetup)).  Теперь доступ к Azure AD для пользователя AD FS, который еще не зарегистрировал сведения о проверке MFA&#34;страницы proofup s через ярлык [ https://aka.ms/mfasetup ](https://aka.ms/mfasetup) с помощью основной проверки подлинности (такие как встроенная проверка подлинности Windows или имя пользователя и пароля с помощью AD FS веб-страниц).  Если пользователь имеет методы проверки, не настроен, Azure AD выполнит встроенной регистрации, в котором пользователь видит сообщение &#34;администратор просит настроить эту учетную запись для дополнительной проверки безопасности&#34;, и пользователь может затем Выберите, чтобы &#34;настроить сейчас&#34;.
> Пользователи, которые уже имеют по крайней мере один метод проверки многофакторной проверки Подлинности, настроенный будет по-прежнему запрашиваться предоставление многофакторной проверки Подлинности при посещении страницы proofup.

## <a name="recommended-deployment-topologies"></a>Рекомендуемые топологии развертывания

### <a name="azure-mfa-as-primary-authentication"></a>Azure MFA как основной проверки подлинности

Существует ряд убедительные причины для использования Azure MFA как основной проверки подлинности с помощью AD FS:

 - Пароли для входа в Azure AD в Office 365 и другим приложениям, AD FS
 - Для защиты паролей на основе входа в систему, требуя дополнительного фактора, например код проверки, прежде чем пароль

Если вы хотите использовать Azure MFA как основной способ проверки подлинности в AD FS для достижения этих преимуществ, вы захотите сохранить возможность использовать в том числе условного доступа Azure AD &#34;true многофакторной проверки Подлинности&#34; запросив дополнительные факторы, в AD FS.

Теперь это можно сделать, настроив параметры домена Azure AD для выполнения многофакторной проверки Подлинности в локальной среде (параметр &#34;SupportsMfa&#34; значение $True).  В этой конфигурации AD FS может быть запросы Azure AD для выполнения дополнительной проверки подлинности или &#34;true многофакторной проверки Подлинности&#34; сценариев условного доступа, которые ее требуют.  

Как описано выше, любой пользователь AD FS, который еще не зарегистрировали (сконфигурированной информации проверки многофакторной проверки Подлинности) будет предложено посредством настроенной страницы ошибок AD FS посетить [ https://aka.ms/mfasetup ](https://aka.ms/mfasetup) для настройки проверки сведений, затем Повторите попытку входа в AD FS.  
Так как Azure MFA как основной считается однофакторные, после первоначальной настройки пользователи должны будут предоставить дополнительный фактор для управления или обновить сведения о своем проверку подлинности в Azure AD, или для доступа к другим ресурсам, требующим многофакторной проверки Подлинности.

>[!NOTE]
> С помощью служб федерации Active Directory 2019 г. необходимо внести изменения в тип утверждения привязки для отношения доверия с поставщиком утверждений Active Directory и изменить это из windowsaccountname имени участника-пользователя. Выполните приведенный ниже командлет PowerShell. Это никак не скажется на внутренней работы фермы AD FS. Вы можете заметить, что несколько пользователей может быть повторно получать запрос на учетные данные, после этого изменения. После входа в систему еще раз, конечные пользователи увидят никаких различий. 

```powershell
Set-AdfsClaimsProviderTrust -AnchorClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -TargetName "Active Directory"
```

### <a name="azure-mfa-as-additional-authentication-to-office-365"></a>Azure MFA в качестве дополнительной проверки подлинности для Office 365

Ранее, если вы хотели бы иметь Azure MFA как дополнительного метода проверки подлинности в AD FS для Office 365 или других проверяющих сторон, лучшим вариантом для настройки Azure AD для комплексной многофакторной проверки Подлинности, в котором основной проверки подлинности выполняется на локальном компьютере в AD FS и многофакторной проверки Подлинности — tr iggered с Azure AD. Теперь можно использовать Azure MFA как дополнительная проверка подлинности в AD FS, при параметре SupportsMfa домена имеет значение $True.  

Как описано выше, любой пользователь AD FS, который еще не зарегистрировали (сконфигурированной информации проверки многофакторной проверки Подлинности) будет предложено посредством настроенной страницы ошибок AD FS посетить [ https://aka.ms/mfasetup ](https://aka.ms/mfasetup) для настройки проверки сведений, затем Повторите попытку входа в AD FS.  

## <a name="pre-requisites"></a>Предварительные требования

При использовании Azure MFA для аутентификации с помощью AD FS, требуются следующие предварительные требования:  
  
- [Подписку Azure с помощью Azure Active Directory](https://azure.microsoft.com/pricing/free-trial/).  
- [Многофакторная Идентификация Azure](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/) 


> [!NOTE]
> Azure AD и Azure MFA, включаются в Azure AD Premium и Enterprise Mobility Suite (EMS).  При наличии любой из этих отдельных подписок не обязательно.

- В Windows Server 2016 AD FS в локальной среде.  
   - Сервер должен иметь возможность взаимодействовать со следующим URL-адресам, через порт 443.
      - https://adnotifications.windowsazure.com
      - https://login.microsoftonline.com
- — В локальной среде [федерацию с Azure AD.](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-get-started-custom/#configuring-federation-with-ad-fs)  
- [Модуль Windows Azure Active Directory для Windows PowerShell](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0).  
- Разрешения глобального администратора на вашем экземпляре Azure AD настроить его с помощью Azure AD PowerShell.  
- Учетные данные администратора предприятия для настройки фермы AD FS для многофакторной Идентификации Azure.  
  
## <a name="configure-the-ad-fs-servers"></a>Настройте серверы AD FS

Чтобы выполнить конфигурацию для Azure MFA для AD FS, необходимо настроить каждый сервер AD FS, выполнив действия, описанные. 

>[!NOTE]
>Убедитесь, что эти действия выполняются на **все** серверы AD FS в ферме. При наличии нескольких серверов AD FS в ферме можно выполнять удаленно с помощью Azure AD PowerShell необходимую конфигурацию.  

### <a name="step-1-generate-a-certificate-for-azure-mfa-on-each-ad-fs-server-using-the-new-adfsazuremfatenantcertificate-cmdlet"></a>Шаг 1. Создать сертификат для Azure MFA на каждом сервере AD FS с помощью `New-AdfsAzureMfaTenantCertificate` командлета

Первое, что вам нужно будет создать сертификат для Azure MFA для использования.  Это можно сделать с помощью PowerShell.  Созданный сертификат можно найти в хранилище сертификатов локального компьютера, и он помечен как с именем субъекта, содержащим идентификатор клиента для каталога Azure AD.

![Службы федерации Active Directory и многофакторной проверки Подлинности](media/Configure-AD-FS-2016-and-Azure-MFA/ADFS_AzureMFA3.png)  

Обратите внимание на то, что идентификатор клиента — это имя каталога в Azure AD.  Используйте следующий командлет PowerShell для создания нового сертификата.  
    `$certbase64 = New-AdfsAzureMfaTenantCertificate -TenantID <tenantID>`  

![Службы федерации Active Directory и многофакторной проверки Подлинности](media/Configure-AD-FS-2016-and-Azure-MFA/ADFS_AzureMFA1.PNG)  
  
### <a name="step-2-add-the-new-credentials-to-the-azure-multi-factor-auth-client-service-principal"></a>Шаг 2. Добавить новые учетные данные для многофакторной проверки подлинности клиента субъекта-службы Azure

Чтобы включить серверы AD FS для связи с клиентом Azure многофакторной проверки подлинности, необходимо добавить учетные данные для субъекта-службы для многофакторной проверки подлинности Azure клиента. Сертификаты, созданные с помощью `New-AdfsAzureMFaTenantCertificate` командлет будет служить эти учетные данные. Выполните следующие действия с помощью PowerShell, чтобы добавить новые учетные данные для многофакторной проверки подлинности клиента субъекта-службы Azure.  

> [!NOTE]
> Чтобы завершить этот шаг, необходимые для подключения к имеющимся экземпляром Azure AD с помощью PowerShell `Connect-MsolService`.  Далее предполагается, что вы уже подключились с помощью PowerShell.  Дополнительные сведения см. в разделе [ `Connect-MsolService`.](https://msdn.microsoft.com/library/dn194123.aspx)  

**Сделайте сертификат новые учетные данные клиента проверки подлинности многофакторной идентификации Azure**  

`New-MsolServicePrincipalCredential -AppPrincipalId 981f26a1-7f43-403b-a875-f8b09b8cd720 -Type asymmetric -Usage verify -Value $certBase64`

> [!IMPORTANT]
> Эта команда должна выполняться на всех серверах AD FS в ферме.  Многофакторная Идентификация Azure AD завершится ошибкой на серверах, которых нет в качестве новых учетных данных с клиентом Azure многофакторной проверки подлинности сертификата.

> [!NOTE]  
> 981f26a1-7f43-403b-a875-f8b09b8cd720 – идентификатор GUID для Azure многофакторной проверки подлинности клиента.  
  
## <a name="configure-the-ad-fs-farm"></a>Настройка фермы AD FS  
  
После завершения предыдущего раздела на каждом сервере AD FS, будет необходимо запустить `Set-AdfsAzureMfaTenant` командлета.  
  
Этот командлет должен выполняться только один раз для фермы AD FS.  Использование PowerShell для выполнения этого шага.
  
> [!NOTE]  
> Необходимо будет перезапустить службу AD FS на каждом сервере в ферме, чтобы изменения вступили в силу.  
  
    Set-AdfsAzureMfaTenant -TenantId <tenant ID> -ClientId 981f26a1-7f43-403b-a875-f8b09b8cd720  

![Службы федерации Active Directory и многофакторной проверки Подлинности](media/Configure-AD-FS-2016-and-Azure-MFA/ADFS_AzureMFA5.png)  
  
После этого вы увидите, что Azure MFA доступна как метод основной проверки подлинности для интрасети и экстрасети.    
  
![Службы федерации Active Directory и многофакторной проверки Подлинности](media/Configure-AD-FS-2016-and-Azure-MFA/ADFS_AzureMFA6.png)  

## <a name="renew-and-manage-ad-fs-azure-mfa-certificates"></a>Обновление и управление AD FS Azure многофакторной проверки Подлинности сертификатов

Следующее руководство помогает выполнить управление сертификатами Azure MFA на серверах AD FS.
По умолчанию при настройке AD FS с Azure MFA, сертификаты сформированный с помощью `New-AdfsAzureMfaTenantCertificate` командлет PowerShell действительны в течение 2 года.  Чтобы определить, насколько близко к истечения срока действия сертификатов, чтобы обновить и установить новые сертификаты, используйте следующую процедуру.

### <a name="assess-ad-fs-azure-mfa-certificate-expiration-date"></a>Оценить дату окончания срока действия сертификата AD FS Azure MFA

На каждом сервере AD FS в локальном хранилище My, будет существовать самозаверяющий сертификат с &#34;OU = Microsoft AD FS Azure MFA&#34; в издателя и субъекта.  Это сертификат Azure MFA.  Проверьте срок действия этого сертификата на каждом сервере AD FS, чтобы определить дату истечения срока действия.  

### <a name="create-new-ad-fs-azure-mfa-certificate-on-each-ad-fs-server"></a>Создать новый сертификат многофакторной проверки Подлинности Azure AD FS на каждом сервере AD FS

Если срок действия сертификатов приближается окончание срока его, запустите процесс обновления, создав новый сертификат на каждом сервере AD FS многофакторной Идентификации Azure. В командном окне PowerShell создайте новый сертификат на каждом сервере AD FS, с помощью следующего командлета:

```
PS C:\> $newcert = New-AdfsAzureMfaTenantCertificate -TenantId <tenant id such as contoso.onmicrosoft.com> -Renew $true
```

В результате этот командлет будет создан новый сертификат, который действителен в течение 2 дней в будущем 2 дней + 2 лет.  Операции AD FS и Azure MFA будет не влияет, этот командлет или новый сертификат. (Примечание: 2 дня задержка является преднамеренным и обеспечивает время выполнения действия для настройки нового сертификата в клиенте, прежде чем AD FS начинает использовать его для Azure MFA.)

### <a name="configure-each-new-ad-fs-azure-mfa-certificate-in-the-azure-ad-tenant"></a>Настройка каждого нового сертификата AD FS Azure MFA в клиенте Azure AD

С помощью модуля Azure AD PowerShell, для каждого нового сертификата (на каждом сервере AD FS), изменить параметры клиента Azure AD следующим образом (Обратите внимание: необходимо сначала подключиться к клиенту, с помощью `Connect-MsolService` для выполнения следующих команд).

```
PS C:/> New-MsolServicePrincipalCredential -AppPrincipalId 981f26a1-7f43-403b-a875-f8b09b8cd720 -Type Asymmetric -Usage Verify -Value $newcert
```

`$certbase64` — Это новый сертификат.  Сертификат в кодировке base64 можно получить путем экспорта сертификата (без закрытого ключа) в кодировке DER файл и открыв в Notepad.exe, а затем скопировав и вставив в сеанс PowerShell и присвоение переменной `$certbase64`.

### <a name="verify-that-the-new-certificates-will-be-used-for-azure-mfa"></a>Убедитесь, что новый сертификат будет использоваться для многофакторной Идентификации Azure

Как только новый сертификат вступит в силу, AD FS принимает их и начать работу с каждого соответствующего сертификата для Azure MFA в течение нескольких часов в день.  После этого на каждом сервере, вы увидите событие записывается в журнал событий администратора AD FS со следующими сведениями:

```
Log Name:      AD FS/Admin
Source:        AD FS
Date:          2/27/2018 7:33:31 PM
Event ID:      547
Task Category: None
Level:         Information
Keywords:      AD FS
User:          DOMAIN\adfssvc
Computer:      ADFS.domain.contoso.com
Description:
The tenant certificate for Azure MFA has been renewed.  

TenantId: contoso.onmicrosoft.com.
Old thumbprint: 7CC103D60967318A11D8C51C289EF85214D9FC63.
Old expiration date: 9/15/2019 9:43:17 PM.
New thumbprint: 8110D7415744C9D4D5A4A6309499F7B48B5F3CCF.
New expiration date: 2/27/2020 2:16:07 AM.
```

## <a name="customize-the-ad-fs-web-page-to-guide-users-to-register-mfa-verification-methods"></a>Настройка веб-страницы AD FS, для регистрации методов проверки многофакторной проверки Подлинности пользователей

Используйте следующие примеры для настройки веб-страниц AD FS для пользователей, которые еще не подтверждены вверх (настраивается сведения о проверке многофакторной проверки Подлинности).

### <a name="find-the-error"></a>Найти ошибку

Во-первых существует несколько различных сообщений об ошибках, возвращаемых в случае, в котором у пользователя отсутствуют сведения о проверке AD FS.
Если вы используете Azure MFA как основной проверки подлинности, не proofed пользователь увидит страницу ошибки AD FS, содержащий следующие сообщения:
```
    <div id="errorArea">
        <div id="openingMessage" class="groupMargin bigText">
            An error occurred
        </div>
        <div id="errorMessage" class="groupMargin">
            Authentication attempt failed. Select a different sign in option or close the web browser and sign in again. Contact your administrator for more information.
        </div>
```
При попытке Azure AD в качестве дополнительной проверки подлинности без proofed пользователь увидит страницу ошибки AD FS, содержащий следующие сообщения:
```
<div id='mfaGreetingDescription' class='groupMargin'>For security reasons, we require additional information to verify your account (mahesh@jenfield.net)</div>
    <div id="errorArea">
        <div id="openingMessage" class="groupMargin bigText">
            An error occurred
        </div>
        <div id="errorMessage" class="groupMargin">
            The selected authentication method is not available for &#39;username@contoso.com&#39;. Choose another authentication method or contact your system administrator for details.
        </div>
```

### <a name="catch-the-error-and-update-the-page-text"></a>Обнаружения ошибок и обновить текст страницы

Для обнаружения ошибок и показать пользователю пользовательское руководство по процессу просто добавить javascript в конец файла onload.js, который является частью веб-темы AD FS.  Благодаря этому можно осуществлять следующее:
 - Поиск идентификационные строки элементов ошибки
 - предоставляют пользовательские веб-содержимого.  

> [!NOTE]
> Рекомендации в целом о том, как настроить файл onload.js, см. в статье [Advanced Customization of AD FS Sign-in Pages](advanced-customization-of-ad-fs-sign-in-pages.md).

Ниже приведен простой пример, необходимо расширить:

1. Откройте Windows PowerShell на сервере-источнике AD FS и создайте новый веб-тема AD FS, выполнив следующую команду:
    
    ``` PowerShell
        New-AdfsWebTheme –Name ProofUp –SourceName default
    ``` 
2. Затем создайте папку и экспорт по умолчанию AD FS веб-темы:

    ``` PowerShell
       New-Item -Path 'c:\Theme' -ItemType Directory;Export-AdfsWebTheme –Name default –DirectoryPath c:\Theme
    ```
3. Откройте в текстовом редакторе файл C:\Theme\script\onload.js
4. Добавьте следующий код в конец файла onload.js
    
    ``` JavaScript
    //Custom Code
    //Customize MFA exception
    //Begin

    var domain_hint = "<YOUR_DOMAIN_NAME_HERE>";
    var mfaSecondFactorErr = "The selected authentication method is not available for";
    var mfaProofupMessage = "You will be automatically redirected in 5 seconds to set up your account for additional security verification. Once you have completed the setup, please return to the application you are attempting to access.<br><br>If you are not redirected automatically, please click <a href='{0}'>here</a>."
    var authArea = document.getElementById("authArea");
    if (authArea) {
        var errorMessage = document.getElementById("errorMessage");
        if (errorMessage) {
            if (errorMessage.innerHTML.indexOf(mfaSecondFactorErr) >= 0) {

                //Hide the error message
                var openingMessage = document.getElementById("openingMessage");
                if (openingMessage) {
                    openingMessage.style.display = 'none'
                }
                var errorDetailsLink = document.getElementById("errorDetailsLink");
                if (errorDetailsLink) {
                    errorDetailsLink.style.display = 'none'
                }

                //Provide a message and redirect to Azure AD MFA Registration Url
                var mfaRegisterUrl = "https://account.activedirectory.windowsazure.com/proofup.aspx?proofup=1&whr=" + domain_hint;
                errorMessage.innerHTML = "<br>" + mfaProofupMessage.replace("{0}", mfaRegisterUrl);
                window.setTimeout(function () { window.location.href = mfaRegisterUrl; }, 5000);
            }
        }
    }

    //End Customize MFA Exception
    //End Custom Code
    ```
    > [!IMPORTANT]
    > Вам нужно изменить «< YOUR_DOMAIN_NAME_HERE >»; Чтобы использовать имя домена. Пример: `var domain_hint = "contoso.com";`
    
5. Сохраните файл onload.js
6. Импортируйте файл onload.js в пользовательской темы, введя следующую команду Windows PowerShell:
    
    ``` PowerShell
    Set-AdfsWebTheme -TargetName ProofUp -AdditionalFileResource @{Uri=’/adfs/portal/script/onload.js’;path="c:\theme\script\onload.js"}
    ```
7. Наконец примените пользовательские веб-темы AD FS, введя следующую команду Windows PowerShell:
    
    ``` PowerShell
    Set-AdfsWebConfig -ActiveThemeName "ProofUp"
    ```

## <a name="next-steps"></a>Следующие шаги

[Управление протоколы TLS/SSL и комплекты шифров, используемый AD FS и Azure MFA](manage-ssl-protocols-in-ad-fs.md)
