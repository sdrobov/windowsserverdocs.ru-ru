---
ms.assetid: 8e7015bc-c489-4ec7-8b6e-3ece90f72317
title: Настройка политик аутентификации
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 2215f172128a533e0e0d4e10b72be53ad455a262
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66444959"
---
# <a name="configure-authentication-policies"></a>Настройка политик аутентификации

В AD FS в Windows Server 2012 R2 и управление доступом и механизм проверки подлинности расширены за счет нескольких факторов, которые включают данные пользователя, устройства, расположения и проверки подлинности. Эти улучшения позволят вам, в пользовательском интерфейсе или с помощью Windows PowerShell, чтобы снизить риск предоставления разрешения на доступ к AD FS\-защищенных приложений через с несколькими\-factor контроля доступа и с несколькими\-многофакторной идентификации, которые основаны на пользователя удостоверения или членство в группах, сетевого расположения, данные устройства, которые к рабочему месту\-присоединен, и состояние проверки подлинности, при нескольких\-идентификации \(MFA\) было выполнено.  

Дополнительные сведения о многофакторной проверки Подлинности и с несколькими\-вынести управление доступом в службах федерации Active Directory \(AD FS\) в Windows Server 2012 R2, см. в следующих разделах:  


-   [Присоединение к рабочему месту с любого устройства для единого входа и эффективная двухфакторная аутентификация в приложениях компании](../../ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)

-   [Управление рисками с использованием условного управления доступом](../../ad-fs/operations/Manage-Risk-with-Conditional-Access-Control.md)

-   [Управление рисками с помощью дополнительной многофакторной проверки подлинности для уязвимых приложений](../../ad-fs/operations/Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md)

## <a name="configure-authentication-policies-via-the-ad-fs-management-snap-in"></a>Настройка политик проверки подлинности с помощью оснастки управления AD FS\-в  
Минимальным требованием для выполнения этих процедур является членство в группе **Администраторы** на локальном компьютере либо наличие эквивалентных прав.  Просмотрите сведения об использовании соответствующих учетных записей и членства в группах в [локальные и доменные группы по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).   

В AD FS в Windows Server 2012 R2 можно указать политику проверки подлинности в глобальной области, которая будет применяться ко всем приложениям и службам, защищенным службами AD FS. Можно также задать политики проверки подлинности для определенных приложений и служб, которые зависят от отношения доверия и защищены с помощью AD FS. Указав политику проверки подлинности для конкретного приложения каждой проверяющей стороны отношения доверия не переопределяет глобальную политику проверки подлинности. Если глобальный или каждой проверяющей стороны отношения доверия с политика проверки подлинности требуется многофакторная Идентификация, многофакторной проверки Подлинности активируется в том случае, когда пользователь пытается выполнить проверку подлинности для отношений доверия этой проверяющей стороны. Глобальная политика проверки подлинности представляет собой резервный вариант для доверия с проверяющей стороной для приложений и служб, которые не имеют политики определенные проверки подлинности. 

## <a name="to-configure-primary-authentication-globally-in-windows-server-2012-r2"></a>Глобально Настройка основной проверки подлинности в Windows Server 2012 R2 

1.  В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS**.  

2.  В AD FS привязать\-в, щелкните **политики проверки подлинности**.  

3.  В **основной проверки подлинности** щелкните **изменить** рядом с полем **глобальные параметры**. Можно также правой\-щелкните **политики проверки подлинности**и выберите **изменить глобальную основную проверку подлинности**, либо в разделе **действия** области выберите  **Редактировать глобальную первичную аутентификацию**.  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy1.png)

4.  В **изменение глобальной политики проверки подлинности** окна на **основной** вкладки, как часть глобальной политики поверки подлинности можно настроить следующие параметры:  

    -   Методы проверки подлинности, используемый для основной проверки подлинности. Можно выбрать доступные методы проверки подлинности в разделе **экстрасети** и **интрасети**.  

    -   Проверка подлинности устройства с помощью **включить аутентификацию устройства** "флажок". Дополнительные сведения см. в разделе [Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications](../../ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md).  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy2.png)  

## <a name="to-configure-primary-authentication-per-relying-party-trust"></a>Чтобы настроить основной проверки подлинности по проверяющей стороной  

1.  В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS**.  

2.  В AD FS привязать\-в, щелкните **политики проверки подлинности**\\**отдельного проверяющей стороны отношения доверия с**, а затем нажмите кнопку доверия с проверяющей стороной для которого вы хотите настроить проверку подлинности политики.  

3.  Непосредственно\-щелкните доверия с проверяющей стороной для которого вы хотите настроить политики проверки подлинности, а затем выберите **изменить настраиваемый основной проверки подлинности**, либо в разделе **действия** области Выберите **изменить настраиваемый основной проверки подлинности**.  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy5.png)   

4.  В **изменение политики проверки подлинности для < проверяющей стороной\_сторона\_доверия\_имя >** окна в разделе **основной** вкладке можно настроить следующий параметр как часть **на доверия с проверяющей стороной** политика проверки подлинности:  

    -   Ли пользователям требуется вводить свои учетные данные каждый раз знак\-в через **пользователям требуется вводить свои учетные данные каждый раз знак\-в** "флажок".  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy6.png) 

## <a name="to-configure-multi-factor-authentication-globally"></a>Чтобы настроить многофакторную проверку подлинности глобально  

1.  В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS**.  

2.  В AD FS привязать\-в, щелкните **политики проверки подлинности**.  

3.  В **с несколькими\-двухфакторная проверка подлинности** щелкните **изменить** рядом с полем **глобальные параметры**. Можно также правой\-щелкните **политики проверки подлинности**и выберите **изменить глобальные с несколькими\-двухфакторная проверка подлинности**, либо в разделе **действия**области выберите **изменить глобальные с несколькими\-двухфакторная проверка подлинности**.  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy8.png)   

4.  В **изменение глобальной политики проверки подлинности** окна в разделе **с несколькими\-идентификации** вкладке, можно настроить следующие параметры как часть глобальной множественных\-идентификации Политика проверки подлинности:  

    -   Параметры или условия для многофакторной проверки Подлинности через доступные параметры в разделе **пользователей\/группы**, **устройств**, и **расположения** разделы.  

    -   Чтобы включить многофакторную проверку Подлинности для любой из этих параметров, необходимо выбрать по крайней мере одного дополнительного метода проверки подлинности. **Сертификат проверки подлинности** является параметром по умолчанию доступны. Можно также настроить другие пользовательские дополнительные методы проверки подлинности, например, Windows Azure Active Authentication. Дополнительные сведения см. в разделе [Пошаговое руководство: Управление рисками с помощью дополнительной многофакторной проверки подлинности для уязвимых приложений](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md).  

> [!WARNING]  
> Можно настроить только дополнительные методы проверки подлинности глобально.  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy9.png)  

## <a name="to-configure-multi-factor-authentication-per-relying-party-trust"></a>Для настройки с несколькими\-многофакторной идентификации каждой проверяющей стороны отношения доверия  

1.  В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS**.  

2.  В AD FS привязать\-, нажмите кнопку **политики проверки подлинности**\\**отдельного проверяющей стороны отношения доверия с**, а затем нажмите кнопку доверия с проверяющей стороной для которого вы хотите настроить MFA.  

3.  Непосредственно\-щелкните доверия с проверяющей стороной для которого вы хотите настроить MFA, а затем выберите **изменение с несколькими Custom\-двухфакторная проверка подлинности**, либо в разделе **действия** области Выберите **изменение с несколькими Custom\-двухфакторная проверка подлинности**.  

4.  В **изменение политики проверки подлинности для < проверяющая\_сторона\_доверия\_имя >** окно в разделе **с несколькими\-коэффициент** вкладке вы можете Настройте следующие параметры как часть каждого\-политику проверки подлинности проверяющей стороны отношения доверия:  

    -   Параметры или условия для многофакторной проверки Подлинности через доступные параметры в разделе **пользователей\/группы**, **устройств**, и **расположения** разделы.  

## <a name="configure-authentication-policies-via-windows-powershell"></a>Настройка политик проверки подлинности с помощью Windows PowerShell  
Windows PowerShell позволяет достичь большей гибкости в с помощью различных факторов, контроля доступа и правила механизма проверки подлинности, доступные в AD FS в Windows Server 2012 R2 для настройки политики проверки подлинности и авторизации, которые необходимо Реализация true условного доступа для AD FS \-защищенным ресурсам.  

Минимальным требованием для выполнения этих процедур является членство в группе администраторов или аналогичной ей на локальном компьютере.  Просмотрите сведения об использовании соответствующих учетных записей и членства в группах в [локальные и доменные группы по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477) \(http:\/\/go.microsoft.com\/fwlink\/? LinkId\=83477\).   

### <a name="to-configure-an-additional-authentication-method-via-windows-powershell"></a>Настройка дополнительного метода проверки подлинности с помощью Windows PowerShell  

1.  На своем сервере федерации откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
`Set-AdfsGlobalAuthenticationPolicy –AdditionalAuthenticationProvider CertificateAuthentication  `
~~~


> [!WARNING]  
> Чтобы убедиться в успешном выполнении этой команды, можно выполнить команду `Get-AdfsGlobalAuthenticationPolicy` .  

### <a name="to-configure-mfa-per-relying-party-trust-that-is-based-on-a-users-group-membership-data"></a>Настройка многофакторной проверки Подлинности на\-доверия с проверяющей стороной, основанный на данных о членстве пользователя  

1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду:  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust`  
~~~


> [!WARNING]  
> Убедитесь, что замена *< проверяющей стороной\_сторона\_доверия >* именем вашего доверия с проверяющей стороной.  

2. В этом же окне команд Windows PowerShell выполните следующую команду.  


~~~
$MfaClaimRule = “c:[Type == ‘“https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid’”, Value =~ ‘“^(?i) <group_SID>$’”] => issue(Type = ‘“https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod’”, Value ‘“https://schemas.microsoft.com/claims/multipleauthn’”);” 

Set-AdfsRelyingPartyTrust –TargetRelyingParty $rp –AdditionalAuthenticationRules $MfaClaimRule
~~~


> [!NOTE]  
> Обязательно замените < группы\_SID > со значением идентификатора безопасности \(SID\) каталога Active Directory \(AD\) группы.  

### <a name="to-configure-mfa-globally-based-on-users-group-membership-data"></a>Настройка многофакторной проверки Подлинности, глобально на основании данных о членстве в группе пользователей  

1.  На своем сервере федерации откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
$MfaClaimRule = “c:[Type == ‘" https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid’", Value == ‘"group_SID’"]  
 => issue(Type = ‘"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod’", Value = ‘"https://schemas.microsoft.com/claims/multipleauthn’");”  

Set-AdfsAdditionalAuthenticationRule $MfaClaimRule  
~~~


> [!NOTE]  
> Убедитесь, что замена *< группы\_SID >* со значением идентификатора безопасности для вашей группы AD.  

### <a name="to-configure-mfa-globally-based-on-users-location"></a>Настройка многофакторной проверки Подлинности, глобально зависимости от расположения пользователя  

1.  На своем сервере федерации откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
$MfaClaimRule = “c:[Type == ‘" https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork’", Value == ‘"true_or_false’"]  
 => issue(Type = ‘"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod’", Value = ‘"https://schemas.microsoft.com/claims/multipleauthn’");”  

Set-AdfsAdditionalAuthenticationRule $MfaClaimRule  
~~~



> [!NOTE]  
> Убедитесь, что замена *< true\_или\_false >* сочетанием `true` или `false`. Значение зависит от вашей определенное условие, основана ли запрос на доступ поступает из экстрасети или интрасети.  

### <a name="to-configure-mfa-globally-based-on-users-device-data"></a>Настройка многофакторной проверки Подлинности, глобально на основании данных пользователя устройства  

1.  На своем сервере федерации откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
$MfaClaimRule = "c:[Type == ‘" https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser’", Value == ‘"true_or_false"']  
 => issue(Type = ‘"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod’", Value = ‘"https://schemas.microsoft.com/claims/multipleauthn’");"  

Set-AdfsAdditionalAuthenticationRule $MfaClaimRule  
~~~


> [!NOTE]  
> Убедитесь, что замена *< true\_или\_false >* сочетанием `true` или `false`. Значение зависит от вашей определенное условие, основанный на том, является ли устройство workplace\-присоединен или нет.  

### <a name="to-configure-mfa-globally-if-the-access-request-comes-from-the-extranet-and-from-a-non-workplace-joined-device"></a>Настройка многофакторной проверки Подлинности глобально, если запрос на доступ поступает из экстрасети и которая не является\-workplace\-присоединенного к домену устройства  

1.  На своем сервере федерации откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
`Set-AdfsAdditionalAuthenticationRule "c:[Type == '"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser'", Value == '"true_or_false'"] && c2:[Type == '"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork'", Value == '" true_or_false '"] => issue(Type = '"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'", Value ='"https://schemas.microsoft.com/claims/multipleauthn'");" ` 
~~~


> [!NOTE]  
> Обязательно замените оба экземпляра *< true\_или\_false >* сочетанием `true` или `false`, зависящее от условия конкретного правила. Условия правила основаны на том, является ли устройство workplace\-присоединен или не и был ли запрос на доступ поступает из экстрасети или интрасети.  

### <a name="to-configure-mfa-globally-if-access-comes-from-an-extranet-user-that-belongs-to-a-certain-group"></a>Настройка многофакторной проверки Подлинности глобально в том случае, если доступ поступает из экстрасети пользователя, которому принадлежит к определенной группе  

1.  На своем сервере федерации откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
Set-AdfsAdditionalAuthenticationRule "c:[Type == `"https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid`", Value == `"group_SID`"] && c2:[Type == `"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork`", Value== `"true_or_false`"] => issue(Type = `"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod`", Value =`"https://schemas.microsoft.com/claims/
~~~

> [!NOTE]  
> Убедитесь, что замена *< группы\_SID >* со значением SID группы и *< true\_или\_false >* сочетанием `true` или `false`, который зависит от вашей определенное условие, основана ли запрос на доступ поступает из экстрасети или интрасети.  

### <a name="to-grant-access-to-an-application-based-on-user-data-via-windows-powershell"></a>Чтобы предоставить доступ к приложению на основе данных пользователя с помощью Windows PowerShell  

1.  На своем сервере федерации откройте командное окно Windows PowerShell и выполните следующую команду.  

    ```  
    $rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust  

    ```  

> [!NOTE]  
> Убедитесь, что замена *< проверяющей стороной\_сторона\_доверия >* со значением вашей доверия с проверяющей стороной.  

2. В этом же окне команд Windows PowerShell выполните следующую команду.  

   ```  

     $GroupAuthzRule = "@RuleTemplate = `“Authorization`” @RuleName = `"Foo`" c:[Type == `"https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid`", Value =~ `"^(?i)<group_SID>$`"] =>issue(Type = `"https://schemas.microsoft.com/authorization/claims/deny`", Value = `"DenyUsersWithClaim`");"  
   Set-AdfsRelyingPartyTrust –TargetRelyingParty $rp –IssuanceAuthorizationRules $GroupAuthzRule  
   ```  

> [!NOTE]  
> > Убедитесь, что замена *< группы\_SID >* со значением идентификатора безопасности для вашей группы AD.  

### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-this-users-identity-was-validated-with-mfa"></a>Чтобы предоставить доступ к приложению с защитой AD FS, только если удостоверение пользователя проверено с помощью многофакторной проверки Подлинности  

1.  На своем сервере федерации откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust ` 
~~~


> [!NOTE]  
> Убедитесь, что замена *< проверяющей стороной\_сторона\_доверия >* со значением вашей доверия с проверяющей стороной.  

2. В этом же окне команд Windows PowerShell выполните следующую команду.  

   ```  
   $GroupAuthzRule = "@RuleTemplate = `"Authorization`"  
   @RuleName = `"PermitAccessWithMFA`"  
   c:[Type == `"https://schemas.microsoft.com/claims/authnmethodsreferences`", Value =~ `"^(?i)https://schemas\.microsoft\.com/claims/multipleauthn$`"] => issue(Type = `"https://schemas.microsoft.com/authorization/claims/permit`", Value = ‘“PermitUsersWithClaim’");"  

   ```  

### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-the-access-request-comes-from-a-workplace-joined-device-that-is-registered-to-the-user"></a>Чтобы предоставить доступ к приложению с защитой AD FS, только если доступ запрос поступает из workplace\-присоединенного к домену устройства, зарегистрированного для пользователя  

1.  На своем сервере федерации откройте командное окно Windows PowerShell и выполните следующую команду.  

    ```  
    $rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust  

    ```  

> [!NOTE]  
> Убедитесь, что замена *< проверяющей стороной\_сторона\_доверия >* со значением вашей доверия с проверяющей стороной.  

2. В этом же окне команд Windows PowerShell выполните следующую команду.  


~~~
$GroupAuthzRule = "@RuleTemplate = `"Authorization`"  
@RuleName = `"PermitAccessFromRegisteredWorkplaceJoinedDevice`"  
c:[Type == `"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser`", Value =~ `"^(?i)true$`"] => issue(Type = `"https://schemas.microsoft.com/authorization/claims/permit`", Value = `"PermitUsersWithClaim`");  
~~~



### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-the-access-request-comes-from-a-workplace-joined-device-that-is-registered-to-a-user-whose-identity-has-been-validated-with-mfa"></a>Чтобы предоставить доступ к приложению с защитой AD FS, только если доступ запрос поступает из workplace\-присоединенного к домену устройства, зарегистрированного на пользователя, удостоверение которого проверено с помощью многофакторной проверки Подлинности  

1.  На своем сервере федерации откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust ` 
~~~


> [!NOTE]  
> Убедитесь, что замена *< проверяющей стороной\_сторона\_доверия >* со значением вашей доверия с проверяющей стороной.  

2. В этом же окне команд Windows PowerShell выполните следующую команду.  

   ```  
   $GroupAuthzRule = ‘@RuleTemplate = “Authorization”  
   @RuleName = “RequireMFAOnRegisteredWorkplaceJoinedDevice”  
   c1:[Type == `"https://schemas.microsoft.com/claims/authnmethodsreferences`", Value =~ `"^(?i)http://schemas\.microsoft\.com/claims/multipleauthn$`"] &&  
   c2:[Type == `"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser`", Value =~ `"^(?i)true$”] => issue(Type = "https://schemas.microsoft.com/authorization/claims/permit`", Value = `"PermitUsersWithClaim`");"  

   ```  

### <a name="to-grant-extranet-access-to-an-application-secured-by-ad-fs-only-if-the-access-request-comes-from-a-user-whose-identity-has-been-validated-with-mfa"></a>Для предоставления доступа к экстрасети к приложению, защищенных с помощью AD FS, только в том случае, если запрос на доступ поступает от пользователя, удостоверение которого проверено с помощью многофакторной проверки Подлинности  

1.  На своем сервере федерации откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust`  
~~~


> [!NOTE]  
> Убедитесь, что замена *< проверяющей стороной\_сторона\_доверия >* со значением вашей доверия с проверяющей стороной.  

2. В этом же окне команд Windows PowerShell выполните следующую команду.  


~~~
$GroupAuthzRule = "@RuleTemplate = `"Authorization`"  
@RuleName = `"RequireMFAForExtranetAccess`"  
c1:[Type == `"https://schemas.microsoft.com/claims/authnmethodsreferences`", Value =~ `"^(?i)http://schemas\.microsoft\.com/claims/multipleauthn$`"] &&  
c2:[Type == `"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork`", Value =~ `"^(?i)false$`"] => issue(Type = `"https://schemas.microsoft.com/authorization/claims/permit`", Value = `"PermitUsersWithClaim`");"  
~~~

## <a name="additional-references"></a>Дополнительная справка  

[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)
