---
ms.assetid: 8e7015bc-c489-4ec7-8b6e-3ece90f72317
title: Настройка политик аутентификации
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: ef38b0280a5753b0995e85d0809de6b632fa3afc
ms.sourcegitcommit: 06ae7c34c648538e15c4d9fe330668e7df32fbba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78371262"
---
# <a name="configure-authentication-policies"></a>Настройка политик аутентификации

В AD FS в Windows Server 2012 R2 улучшена поддержка управления доступом и механизма проверки подлинности с несколькими факторами, включающими пользователя, устройство, расположение и данные проверки подлинности. Эти улучшения позволяют вам, используя пользовательский интерфейс или Windows PowerShell, управлять риском предоставления разрешений на доступ AD FS\-защищенные приложения через много\-ный контроль доступа\-и многофакторную проверку подлинности, основанную на удостоверениях пользователей или группах, сетевом расположении, данных устройства, подключенных к рабочей области\-, и состоянии проверки подлинности при\-многофакторной проверки подлинности\(\)  

Дополнительные сведения о MFA и много\-ном контроле доступа в службы федерации Active Directory (AD FS) \(AD FS\) в Windows Server 2012 R2 см. в следующих разделах:  


-   [Присоединение к рабочей области с любого устройства для единого входа и эффективная двухфакторная аутентификация в приложениях компании](../../ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)

-   [Управление рисками с использованием условного управления доступом](../../ad-fs/operations/Manage-Risk-with-Conditional-Access-Control.md)

-   [Управление рисками для уязвимых приложений с помощью дополнительной многофакторной аутентификации](../../ad-fs/operations/Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md)

## <a name="configure-authentication-policies-via-the-ad-fs-management-snap-in"></a>Настройка политик проверки подлинности с помощью\-оснастки "Управление AD FS" в  
Минимальным требованием для выполнения этих процедур является членство в группе **Администраторы** на локальном компьютере либо наличие эквивалентных прав.  Просмотрите сведения об использовании соответствующих учетных записей и членстве в группах в [локальной среде и группах домена по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).   

В AD FS в Windows Server 2012 R2 можно указать политику проверки подлинности в глобальной области, применимую ко всем приложениям и службам, защищенным AD FS. Можно также задать политики проверки подлинности для конкретных приложений и служб, которые используют отношения доверия сторон и защищены с помощью AD FS. Указание политики проверки подлинности для конкретного приложения на отношение доверия с проверяющей стороной не переопределяет глобальную политику проверки подлинности. Если для глобальной или для каждой политики проверки подлинности доверия с проверяющей стороной требуется MFA, MFA активируется, когда пользователь пытается пройти проверку подлинности для этого отношения доверия с проверяющей стороной. Глобальная политика проверки подлинности — это резервная стратегия для отношений доверия проверяющей стороны для приложений и служб, которые не имеют определенной настроенной политики аутентификации. 

## <a name="to-configure-primary-authentication-globally-in-windows-server-2012-r2"></a>Настройка основной проверки подлинности глобально в Windows Server 2012 R2 

1.  В диспетчер сервера щелкните **Сервис**, а затем выберите **AD FS управление**.  

2.  В AD FS привязать\-в выберите **политики проверки подлинности**.  

3.  В разделе **Основная проверка подлинности** щелкните **изменить** рядом с **параметром глобальные параметры**. Можно также щелкнуть правой кнопкой мыши\-**политики проверки подлинности**и выбрать пункт **изменить глобальную основную проверку подлинности**или в области **действия** выберите **изменить глобальную основную проверку подлинности**.  
политики ![проверки подлинности](media/Configure-Authentication-Policies/authpolicy1.png)

4.  В окне **изменение политики глобальной проверки подлинности** на **главной** вкладке можно настроить следующие параметры в рамках глобальной политики проверки подлинности.  

    -   Методы проверки подлинности, используемые для основной проверки подлинности. В **экстрасети** и **интрасети**можно выбрать доступные методы проверки подлинности.  

    -   Проверка подлинности устройства с помощью флажка **включить проверку подлинности устройства** . Дополнительные сведения см. в разделе [Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications](../../ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md).  
политики ![проверки подлинности](media/Configure-Authentication-Policies/authpolicy2.png)  

## <a name="to-configure-primary-authentication-per-relying-party-trust"></a>Настройка основной проверки подлинности для отношения доверия с проверяющей стороной  

1.  В диспетчер сервера щелкните **Сервис**, а затем выберите **AD FS управление**.  

2.  В AD FS привязать\-в выберите **политики проверки Подлинности**\\**отношение доверия с проверяющей**стороной, а затем щелкните отношение доверия с проверяющей стороной, для которого требуется настроить политики проверки подлинности.  

3.  Щелкните правой кнопкой\-мыши отношение доверия с проверяющей стороной, для которого нужно настроить политики проверки подлинности, а затем выберите **изменить настраиваемую основную проверку подлинности**или в области **действия** выберите **изменить настраиваемую основную проверку подлинности**.  
политики ![проверки подлинности](media/Configure-Authentication-Policies/authpolicy5.png)   

4.  В окне **изменение политики проверки подлинности для < проверяющей стороны\_\_доверие\_имя >** на **главной** вкладке можно настроить следующий параметр в рамках политики проверки подлинности с **отношением доверия с проверяющей стороной** .  

    -   Должны ли пользователи предоставлять свои учетные данные при каждом входе в систему\-через **пользователей, необходимо предоставлять свои учетные данные каждый раз при входе\-** .  
политики ![проверки подлинности](media/Configure-Authentication-Policies/authpolicy6.png) 

## <a name="to-configure-multi-factor-authentication-globally"></a>Настройка многофакторной проверки подлинности на глобальном уровне  

1.  В диспетчер сервера щелкните **Сервис**, а затем выберите **AD FS управление**.  

2.  В AD FS привязать\-в выберите **политики проверки подлинности**.  

3.  В разделе **многофакторная проверка Подлинности\-** щелкните **изменить** рядом с **параметром глобальные параметры**. Можно также щелкнуть правой кнопкой мыши\-**политики проверки подлинности**и выбрать пункт **изменить\-глобальную многофакторную проверку подлинности**, или в области **действия** выберите **изменить глобальную много\-фактор проверки подлинности**.  
политики ![проверки подлинности](media/Configure-Authentication-Policies/authpolicy8.png)   

4.  В окне **изменение политики глобальной проверки подлинности** на вкладке **много\-ный фактор** можно настроить следующие параметры в рамках политики глобальной много\-ной проверки подлинности.  

    -   Параметры и условия для MFA через доступные параметры в разделах **пользователи\/группы**, **устройства**и **расположения** .  

    -   Чтобы включить MFA для любого из этих параметров, необходимо выбрать по крайней мере один дополнительный метод проверки подлинности. Параметр **Проверка подлинности по сертификату** доступен по умолчанию. Можно также настроить другие дополнительные методы проверки подлинности, например Windows Azure Active Authentication. Дополнительные сведения см. в разделе [Пошаговое руководство. Управление рисками с помощью дополнительной многофакторной проверки подлинности для конфиденциальных приложений](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md).  

> [!WARNING]  
> Дополнительные методы проверки подлинности можно настраивать только глобально.  
политики ![проверки подлинности](media/Configure-Authentication-Policies/authpolicy9.png)  

## <a name="to-configure-multi-factor-authentication-per-relying-party-trust"></a>Настройка многофакторной проверки подлинности\-для отношения доверия с проверяющей стороной  

1.  В диспетчер сервера щелкните **Сервис**, а затем выберите **AD FS управление**.  

2.  В AD FS привязать\-в выберите **политики проверки Подлинности**\\**отношение доверия с проверяющей стороной**, а затем щелкните отношение доверия с проверяющей стороной, для которого требуется настроить mfa.  

3.  Щелкните правой кнопкой мыши отношение доверия с проверяющей стороной, для которого требуется настроить MFA, а затем выберите пункт **изменить\-настраиваемую многофакторную проверку Подлинности**\-или в области **действия** выберите **изменить\-настраиваемую многофакторную проверку подлинности**.  

4.  В окне **изменение политики проверки подлинности для < проверяющей стороны\_\_доверие\_имя >** на вкладке **многофакторная\-** можно настроить следующие параметры в рамках политики проверки подлинности для каждой\-проверяющей стороны:  

    -   Параметры и условия для MFA через доступные параметры в разделах **пользователи\/группы**, **устройства**и **расположения** .  

## <a name="configure-authentication-policies-via-windows-powershell"></a>Настройка политик проверки подлинности с помощью Windows PowerShell  
Windows PowerShell обеспечивает большую гибкость в использовании различных факторов контроля доступа и механизма проверки подлинности, доступных в AD FS в Windows Server 2012 R2 для настройки политик проверки подлинности и правил авторизации, необходимых для реализации истинного условного доступа для AD FS \-защищенных ресурсов.  

Минимальным требованием для выполнения этих процедур является членство в группе Администраторы на локальном компьютере либо наличие эквивалентных прав.  Просмотрите сведения об использовании соответствующих учетных записей и членства в группах в [локальной среде и группах домена по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477) \(http:\/\/go.Microsoft.com\/fwlink\/? LinkId\=83477\).   

### <a name="to-configure-an-additional-authentication-method-via-windows-powershell"></a>Настройка дополнительного метода проверки подлинности с помощью Windows PowerShell  

1.  На сервере федерации Откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
`Set-AdfsGlobalAuthenticationPolicy –AdditionalAuthenticationProvider CertificateAuthentication  `
~~~


> [!WARNING]  
> Чтобы убедиться в успешном выполнении этой команды, можно выполнить команду `Get-AdfsGlobalAuthenticationPolicy` .  

### <a name="to-configure-mfa-per-relying-party-trust-that-is-based-on-a-users-group-membership-data"></a>Настройка многофакторной проверки подлинности на\-отношения доверия с проверяющей стороной на основе данных членства пользователя в группах  

1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду:  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust`  
~~~


> [!WARNING]  
> Обязательно замените *< проверяющей стороны\_\_доверие >* с именем отношения доверия с проверяющей стороной.  

2. В том же командном окне Windows PowerShell выполните следующую команду.  


~~~
$MfaClaimRule = “c:[Type == ‘“https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid'”, Value =~ ‘“^(?i) <group_SID>$'”] => issue(Type = ‘“https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'”, Value ‘“https://schemas.microsoft.com/claims/multipleauthn'”);” 

Set-AdfsRelyingPartyTrust –TargetRelyingParty $rp –AdditionalAuthenticationRules $MfaClaimRule
~~~


> [!NOTE]  
> Не забудьте заменить < группы\_SID > значением идентификатора безопасности \(\) SID группы Active Directory \(AD.\)  

### <a name="to-configure-mfa-globally-based-on-users-group-membership-data"></a>Настройка MFA на глобальном уровне на основе данных членства пользователей в группах  

1.  На сервере федерации Откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
$MfaClaimRule = “c:[Type == ‘" https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid'", Value == ‘"group_SID'"]  
 => issue(Type = ‘"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'", Value = ‘"https://schemas.microsoft.com/claims/multipleauthn'");”  

Set-AdfsAdditionalAuthenticationRule $MfaClaimRule  
~~~


> [!NOTE]  
> Обязательно замените *< group\_sid >* значением SID группы AD.  

### <a name="to-configure-mfa-globally-based-on-users-location"></a>Настройка MFA на основе расположения пользователя на глобальном уровне  

1.  На сервере федерации Откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
$MfaClaimRule = “c:[Type == ‘" https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork'", Value == ‘"true_or_false'"]  
 => issue(Type = ‘"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'", Value = ‘"https://schemas.microsoft.com/claims/multipleauthn'");”  

Set-AdfsAdditionalAuthenticationRule $MfaClaimRule  
~~~



> [!NOTE]  
> Обязательно замените *< true\_или\_false >* на `true` или `false`. Это значение зависит от конкретного условия правила, основанного на том, поступает ли запрос на доступ из экстрасети или из интрасети.  

### <a name="to-configure-mfa-globally-based-on-users-device-data"></a>Настройка MFA на глобальном уровне на основе данных устройства пользователя  

1.  На сервере федерации Откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
$MfaClaimRule = "c:[Type == ‘" https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser'", Value == ‘"true_or_false"']  
 => issue(Type = ‘"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'", Value = ‘"https://schemas.microsoft.com/claims/multipleauthn'");"  

Set-AdfsAdditionalAuthenticationRule $MfaClaimRule  
~~~


> [!NOTE]  
> Обязательно замените *< true\_или\_false >* на `true` или `false`. Это значение зависит от условия конкретного правила в зависимости от того, является ли устройство рабочей областью\-присоединенным.  

### <a name="to-configure-mfa-globally-if-the-access-request-comes-from-the-extranet-and-from-a-non-workplace-joined-device"></a>Настройка MFA на глобальном уровне, если запрос на доступ поступает из экстрасети и с не\-ного\-присоединенного устройства  

1.  На сервере федерации Откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
`Set-AdfsAdditionalAuthenticationRule "c:[Type == '"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser'", Value == '"true_or_false'"] && c2:[Type == '"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork'", Value == '" true_or_false '"] => issue(Type = '"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'", Value ='"https://schemas.microsoft.com/claims/multipleauthn'");" ` 
~~~


> [!NOTE]  
> Обязательно замените оба экземпляра *< true\_или\_false >* на `true` или `false`, которые зависят от конкретных условий правил. Условия правила основаны на том, находится ли устройство в рабочей области\-присоединено или нет, а также от того, поступает ли запрос на доступ из экстрасети или интрасети.  

### <a name="to-configure-mfa-globally-if-access-comes-from-an-extranet-user-that-belongs-to-a-certain-group"></a>Настройка MFA глобально, если доступ осуществляется от пользователя экстрасети, принадлежащего определенной группе  

1.  На сервере федерации Откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
Set-AdfsAdditionalAuthenticationRule "c:[Type == `"https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid`", Value == `"group_SID`"] && c2:[Type == `"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork`", Value== `"true_or_false`"] => issue(Type = `"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod`", Value =`"https://schemas.microsoft.com/claims/
~~~

> [!NOTE]  
> Обязательно замените *< group\_sid >* значением SID группы и *< true\_или\_false >* на `true` или `false`, что зависит от конкретного условия правила, основанного на том, поступает ли запрос на доступ из экстрасети или интрасети.  

### <a name="to-grant-access-to-an-application-based-on-user-data-via-windows-powershell"></a>Предоставление доступа к приложению на основе данных пользователя с помощью Windows PowerShell  

1.  На сервере федерации Откройте командное окно Windows PowerShell и выполните следующую команду.  

    ```  
    $rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust  

    ```  

> [!NOTE]  
> Убедитесь, что *< проверяющей стороны\_\_доверия >* со значением отношения доверия с проверяющей стороной.  

2. В том же командном окне Windows PowerShell выполните следующую команду.  

   ```  

     $GroupAuthzRule = "@RuleTemplate = `“Authorization`” @RuleName = `"Foo`" c:[Type == `"https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid`", Value =~ `"^(?i)<group_SID>$`"] =>issue(Type = `"https://schemas.microsoft.com/authorization/claims/deny`", Value = `"DenyUsersWithClaim`");"  
   Set-AdfsRelyingPartyTrust –TargetRelyingParty $rp –IssuanceAuthorizationRules $GroupAuthzRule  
   ```  

> [!NOTE]  
> > Обязательно замените *< group\_sid >* значением SID группы AD.  

### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-this-users-identity-was-validated-with-mfa"></a>Предоставление доступа к приложению, защищенному AD FS только в том случае, если удостоверение этого пользователя было проверено с помощью MFA  

1.  На сервере федерации Откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust ` 
~~~


> [!NOTE]  
> Убедитесь, что *< проверяющей стороны\_\_доверия >* со значением отношения доверия с проверяющей стороной.  

2. В том же командном окне Windows PowerShell выполните следующую команду.  

   ```  
   $GroupAuthzRule = "@RuleTemplate = `"Authorization`"  
   @RuleName = `"PermitAccessWithMFA`"  
   c:[Type == `"https://schemas.microsoft.com/claims/authnmethodsreferences`", Value =~ `"^(?i)https://schemas\.microsoft\.com/claims/multipleauthn$`"] => issue(Type = `"https://schemas.microsoft.com/authorization/claims/permit`", Value = ‘“PermitUsersWithClaim'");"  

   ```  

### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-the-access-request-comes-from-a-workplace-joined-device-that-is-registered-to-the-user"></a>Предоставление доступа к приложению, защищенному AD FS только в том случае, если запрос на доступ поступает с рабочего места\-присоединенного к нему устройства, зарегистрированного для пользователя.  

1.  На сервере федерации Откройте командное окно Windows PowerShell и выполните следующую команду.  

    ```  
    $rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust  

    ```  

> [!NOTE]  
> Убедитесь, что *< проверяющей стороны\_\_доверия >* со значением отношения доверия с проверяющей стороной.  

2. В том же командном окне Windows PowerShell выполните следующую команду.  


~~~
$GroupAuthzRule = "@RuleTemplate = `"Authorization`"  
@RuleName = `"PermitAccessFromRegisteredWorkplaceJoinedDevice`"  
c:[Type == `"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser`", Value =~ `"^(?i)true$`"] => issue(Type = `"https://schemas.microsoft.com/authorization/claims/permit`", Value = `"PermitUsersWithClaim`");  
~~~



### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-the-access-request-comes-from-a-workplace-joined-device-that-is-registered-to-a-user-whose-identity-has-been-validated-with-mfa"></a>Предоставление доступа к приложению, защищенному AD FS только в том случае, если запрос на доступ поступает с рабочего места\-присоединенного устройства, зарегистрированного для пользователя, удостоверение которого было проверено с помощью MFA.  

1.  На сервере федерации Откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust ` 
~~~


> [!NOTE]  
> Убедитесь, что *< проверяющей стороны\_\_доверия >* со значением отношения доверия с проверяющей стороной.  

2. В том же командном окне Windows PowerShell выполните следующую команду.  

   ```  
   $GroupAuthzRule = ‘@RuleTemplate = “Authorization”  
   @RuleName = “RequireMFAOnRegisteredWorkplaceJoinedDevice”  
   c1:[Type == `"https://schemas.microsoft.com/claims/authnmethodsreferences`", Value =~ `"^(?i)http://schemas\.microsoft\.com/claims/multipleauthn$`"] &&  
   c2:[Type == `"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser`", Value =~ `"^(?i)true$”] => issue(Type = "https://schemas.microsoft.com/authorization/claims/permit`", Value = `"PermitUsersWithClaim`");"  

   ```  

### <a name="to-grant-extranet-access-to-an-application-secured-by-ad-fs-only-if-the-access-request-comes-from-a-user-whose-identity-has-been-validated-with-mfa"></a>Предоставление доступа к экстрасети приложению, защищенному AD FS, только если запрос на доступ поступает от пользователя, удостоверение которого проверено с помощью MFA  

1.  На сервере федерации Откройте командное окно Windows PowerShell и выполните следующую команду.  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust`  
~~~


> [!NOTE]  
> Убедитесь, что *< проверяющей стороны\_\_доверия >* со значением отношения доверия с проверяющей стороной.  

2. В том же командном окне Windows PowerShell выполните следующую команду.  


~~~
$GroupAuthzRule = "@RuleTemplate = `"Authorization`"  
@RuleName = `"RequireMFAForExtranetAccess`"  
c1:[Type == `"https://schemas.microsoft.com/claims/authnmethodsreferences`", Value =~ `"^(?i)http://schemas\.microsoft\.com/claims/multipleauthn$`"] &&  
c2:[Type == `"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork`", Value =~ `"^(?i)false$`"] => issue(Type = `"https://schemas.microsoft.com/authorization/claims/permit`", Value = `"PermitUsersWithClaim`");"  
~~~

## <a name="additional-references"></a>Дополнительная справка  

[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)
