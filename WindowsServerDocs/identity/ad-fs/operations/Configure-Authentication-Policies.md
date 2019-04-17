---
ms.assetid: 8e7015bc-c489-4ec7-8b6e-3ece90f72317
title: "Настройка политик аутентификации"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 7faffb7ccbb4b0ea3c65329d18f915d7dafcd46f
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="configure-authentication-policies"></a>Настройка политик аутентификации

>Область применения: Windows Server 2012 R2

В AD FS в Windows Server 2012 R2 и управление доступом и механизм проверки подлинности являются дополнено несколькими факторами, которые включают данные пользователя, устройства, местоположения и проверки подлинности. Эти улучшения позволяют через пользовательский интерфейс или через Windows PowerShell, чтобы снизить риск предоставления разрешений на доступ к приложениям через контроль доступа используется коэффициент и несколькими двойной проверки подлинности, основанная на пользователя удостоверений или членства в группах, сетевого расположения, данных устройства, присоединенных к workplace\, AD FS\ и состояния проверки подлинности, если была \(MFA\) несколькими двухфакторной проверки подлинности выполнены.  
  
Дополнительные сведения о многофакторной проверки Подлинности и коэффициент используется управление доступом в \(AD FS\) служб федерации Active Directory в Windows Server 2012 R2 см. в следующих разделах:  


-   [Присоединение к рабочему месту с любого устройства для единого входа и эффективная двухфакторная аутентификация в приложениях компании](../../ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)

-   [Управление рисками с использованием условного управления доступом](../../ad-fs/operations/Manage-Risk-with-Conditional-Access-Control.md)

-   [Управление рисками с помощью дополнительной многофакторной проверки подлинности для уязвимых приложений](../../ad-fs/operations/Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md)

## <a name="configure-authentication-policies-via-the-ad-fs-management-snap-in"></a>Настройка политик проверки подлинности через управления AD FS оснастка  
Членство в группе **Администраторы**, или в эквивалентной группе на локальном компьютере, является минимальным требованием для выполнения этих процедур.  Подробные сведения об использовании соответствующих учетных записей и членстве в группах в [локальные и доменные группы по умолчанию ](https://go.microsoft.com/fwlink/?LinkId=83477).   
  
В AD FS в Windows Server 2012 R2 можно определить политику проверки подлинности в глобальной области, которая будет применяться ко всем приложениям и службам, защищенным с помощью AD FS. Также можно задать политику проверки подлинности для определенных приложений и служб, использующие стороны отношения доверия и защищены с помощью Служб федерации Active Directory. Определение политики проверки подлинности для конкретного приложения каждой проверяющей стороны отношения доверия не отменяет глобальную политику проверки подлинности. Если глобальный или каждой проверяющей стороной доверия политики проверки подлинности требует многофакторной проверки Подлинности, многофакторной проверки Подлинности запускается в том случае, когда пользователь пытается выполнить проверку подлинности для этого отношения доверия с проверяющей стороной. Глобальная политика проверки подлинности представляет собой резервный вариант для отношений доверия с проверяющей стороной для приложения и службы, которые не содержат политику определенных проверки подлинности. 

## <a name="to-configure-primary-authentication-globally-in-windows-server-2012-r2"></a>Чтобы настроить основной проверки подлинности глобально в Windows Server 2012 R2 
  
1.  В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS **.  
  
2.  В AD FS оснастка, щелкните **политики проверки подлинности**.  
  
3.  В **основной проверки подлинности** щелкните **изменить** рядом с пунктом **глобальные параметры**. Вы также можете щелкнуть **политики проверки подлинности**и выберите **редактировать глобальную первичную аутентификацию**, либо в разделе **действия** выберите **редактировать глобальную первичную аутентификацию**.  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy1.png)
  
4.  В **изменение глобальной политики проверки подлинности** окна на **основной** вкладки, как часть глобальной политики проверки подлинности можно настроить следующие параметры:  
  
    -   Метод проверки подлинности, который будет использоваться для основной проверки подлинности. Можно выбрать доступные методы проверки подлинности в разделе **внешний доступ** и **интрасети**.  
  
    -   Отключение проверки подлинности через **включить проверку подлинности устройства** флажок. Дополнительные сведения см. в разделе [присоединение к рабочему месту с любого устройства для единого входа и эффективной двухфакторной проверки подлинности между приложениями компании](../../ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md).  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy2.png)  

## <a name="to-configure-primary-authentication-per-relying-party-trust"></a>Чтобы настроить основной проверки подлинности каждой проверяющей стороной доверия  
  
1.  В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS **.  
  
2.  В AD FS оснастка, щелкните **политики проверки подлинности**\\**каждого доверия с проверяющей стороной**, а затем нажмите кнопку доверия с проверяющей стороной для которого вы хотите настроить политики проверки подлинности.  
  
3.  Либо щелкните правой кнопкой мыши отношение доверия с проверяющей стороной для которого вы хотите настроить политики проверки подлинности, а затем выберите **изменить пользовательские основной проверки подлинности**, либо в разделе **действия** выберите **изменить пользовательские основной проверки подлинности**.  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy5.png)   

4.  В **изменение политики проверки подлинности для < relying\_party\_trust\_name >** окна в разделе **основной** вкладку, можно настроить следующие параметры как часть **каждого доверия с проверяющей стороной** политики проверки подлинности:  
  
    -   Пользователи должны свои учетные данные каждый раз при входа в систему через **пользователи должны предоставить свои учетные данные каждый раз при входа в систему** флажок.  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy6.png) 

## <a name="to-configure-multi-factor-authentication-globally"></a>Настройка многофакторной проверки подлинности глобально  
  
1.  В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS **.  
  
2.  В AD FS оснастка, щелкните **политики проверки подлинности**.  
  
3.  В **несколькими двухфакторной проверки подлинности** щелкните **изменить** рядом с пунктом **глобальные параметры**. Вы также можете щелкнуть **политики проверки подлинности**и выберите **изменить глобальный параметр двухфакторной проверки подлинности**, или в разделе **действия** выберите **изменить глобальный параметр двухфакторной проверки подлинности**.  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy8.png)   

4.  В **изменение глобальной политики проверки подлинности** окна в разделе **несколькими коэффициент** вкладку, при настройке политики глобальный параметр фактора проверки подлинности можно настроить следующие параметры:  
  
    -   Параметры или условия для многофакторной проверки Подлинности через доступные параметры в разделе **папке Users\/группы**, **устройств**, и **расположения** разделов.  
  
    -   Чтобы включить многофакторную проверку Подлинности для любого из этих параметров, необходимо выбрать по крайней мере один дополнительного метода проверки подлинности. **Сертификат проверки подлинности** является параметром по умолчанию доступны. Можно также настроить другие настраиваемые дополнительные методы проверки подлинности, например, Windows Azure Active Authentication. Дополнительные сведения см. в разделе [Пошаговое руководство: управление рисками с помощью дополнительной многофакторной проверки подлинности для уязвимых приложений](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md).  
  
> [!WARNING]  
> Можно настроить только дополнительные методы проверки подлинности глобально.  
![политики проверки подлинности](media/Configure-Authentication-Policies/authpolicy9.png)  

## <a name="to-configure-multi-factor-authentication-per-relying-party-trust"></a>Настройка проверки подлинности используется коэффициент каждой проверяющей стороной доверия  
  
1.  В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS **.  
  
2.  В AD FS оснастка, щелкните **политики проверки подлинности**\\**каждого доверия с проверяющей стороной**, а затем нажмите кнопку доверия с проверяющей стороной для которого вы хотите настроить многофакторную проверку Подлинности.  
  
3.  Либо щелкните правой кнопкой мыши отношение доверия с проверяющей стороной для которого вы хотите настроить многофакторную проверку Подлинности, а затем выберите **изменить пользовательские несколькими двухфакторной проверки подлинности**, либо в разделе **действия** выберите **изменить пользовательские несколькими двухфакторной проверки подлинности**.  
  
4.  В **изменение политики проверки подлинности для < relying\_party\_trust\_name >** окна в разделе **несколькими коэффициент** вкладку, можно настроить следующие параметры в рамках политика проверки подлинности доверия кусту проверяющей стороной:  
  
    -   Параметры или условия для многофакторной проверки Подлинности через доступные параметры в разделе **папке Users\/группы**, **устройств**, и **расположения** разделов.  

## <a name="configure-authentication-policies-via-windows-powershell"></a>Настройка политик проверки подлинности через Windows PowerShell  
Windows PowerShell позволяет добиться большей гибкости в с помощью различных факторов контроля доступа и механизм проверки подлинности, доступные в AD FS в Windows Server 2012 R2 для настройки политик проверки подлинности и авторизации правила, которые необходимы для реализации true условного доступа для ресурсов \-secured AD FS.  
  
Минимальным требованием для выполнения этих процедур является членство в группе администраторов или аналогичной ей на локальном компьютере.  Подробные сведения об использовании соответствующих учетных записей и членстве в группах в [локальные и доменные группы по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477) \ (http:///\/ go.microsoft.com\/fwlink\ /? LinkId\ = 83477\).   
  
### <a name="to-configure-an-additional-authentication-method-via-windows-powershell"></a>Чтобы настроить дополнительный метод проверки подлинности через Windows PowerShell  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду.  
  

    `Set-AdfsGlobalAuthenticationPolicy –AdditionalAuthenticationProvider CertificateAuthentication  `

  
> [!WARNING]  
> Чтобы убедиться в успешном выполнении этой команды, можно запустить `Get-AdfsGlobalAuthenticationPolicy` команды.  
  
### <a name="to-configure-mfa-per-relying-party-trust-that-is-based-on-a-users-group-membership-data"></a>Настройка многофакторной проверки Подлинности проверяющей кусту доверия стороной, которое основана на данных о членстве пользователя  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду:  
  

    `$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust`  
  
  
> [!WARNING]  
> Убедитесь, что заменить *< relying\_party\_trust >* с именем доверия с проверяющей стороной.  
  
2.  В том же окне команд Windows PowerShell выполните следующую команду.  
  
 
    $MfaClaimRule = «c: [тип == "» https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid"», значение = ~ "» $^(?i) < group_SID >"»] = > проблемы (тип = "» https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod"», значение "» https://schemas.microsoft.com/claims/multipleauthn"»);» 
    
    SET-AdfsRelyingPartyTrust-TargetRelyingParty $rp — AdditionalAuthenticationRules $MfaClaimRule
  
  
> [!NOTE]  
> Убедитесь, что замените < group\_SID > значением идентификатора безопасности \(SID\) для вашей группы Active Directory \(AD\).  
  
### <a name="to-configure-mfa-globally-based-on-users-group-membership-data"></a>Настройка многофакторной проверки Подлинности, глобально на основании данных о членстве в группе пользователей  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду.  
  

    $MfaClaimRule = «c: [тип == "«https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid"», значение == "«group_SID" «]  
     = > проблемы (тип = "" https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod "», значение =" "https://schemas.microsoft.com/claims/multipleauthn"»);»  
      
    SET-AdfsAdditionalAuthenticationRule $MfaClaimRule  

  
> [!NOTE]  
> Убедитесь, что заменить *< group\_SID >* со значением идентификатора безопасности для вашей группы AD.  
  
### <a name="to-configure-mfa-globally-based-on-users-location"></a>Настройка многофакторной проверки Подлинности, глобально зависимости от расположения пользователя  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду.  
  
 
    $MfaClaimRule = «c: [тип == "«https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork"», значение == "«true_or_false" «]  
     = > проблемы (тип = "" https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod "», значение =" "https://schemas.microsoft.com/claims/multipleauthn"»);»  
  
    SET-AdfsAdditionalAuthenticationRule $MfaClaimRule  
  

  
> [!NOTE]  
> Убедитесь, что заменить *< true\_or\_false >* с помощью `true` или `false`. Значение зависит от вашей конкретное условие правила на основании ли запрос на доступ поступает из экстрасети или интрасети.  
  
### <a name="to-configure-mfa-globally-based-on-users-device-data"></a>Настройка многофакторной проверки Подлинности, глобально на основании данных пользователя устройства  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду.  
  

    $MfaClaimRule = «c: [тип == "«https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser"», значение == «true_or_false»]  
     = > проблемы (тип = "" https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod "», значение =" "https://schemas.microsoft.com/claims/multipleauthn"»);»  
  
    SET-AdfsAdditionalAuthenticationRule $MfaClaimRule  

  
> [!NOTE]  
> Убедитесь, что заменить *< true\_or\_false >* с помощью `true` или `false`. Значение зависит от вашей конкретное условие правила на основании ли устройство присоединяется workplace\ или нет.  
  
### <a name="to-configure-mfa-globally-if-the-access-request-comes-from-the-extranet-and-from-a-non-workplace-joined-device"></a>Глобально Настройка многофакторной проверки Подлинности при поступлении запроса на доступ из экстрасети и устройства, не являющихся workplace\ присоединенных к  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду.  
  
 
    `Set-AdfsAdditionalAuthenticationRule "c:[Type == '"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser'", Value == '"true_or_false'"] && c2:[Type == '"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork'", Value == '" true_or_false '"] => issue(Type = '"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'", Value ='"https://schemas.microsoft.com/claims/multipleauthn'");" ` 
 
  
> [!NOTE]  
> Убедитесь, что замены обоих экземпляров *< true\_or\_false >* с помощью `true` или `false`, выбор зависит от конкретного правила условия. Условия правил на основе ли устройство workplace\ присоединен или не и ли поступлении запроса на доступ из экстрасети или интрасети.  
  
### <a name="to-configure-mfa-globally-if-access-comes-from-an-extranet-user-that-belongs-to-a-certain-group"></a>Глобально Настройка многофакторной проверки Подлинности при поступлении доступа из экстрасети пользователя, который принадлежит к определенной группе  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду.  
  

    Set-AdfsAdditionalAuthenticationRule «c: [тип == `"https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid`», значение == `"group_SID`»] & & c2: [тип == `"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork`», значение == `"true_or_false`»] = > проблемы (тип = `"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod`», значение = "«https://schemas.microsoft.com/claims/
      
> [!NOTE]  
> Убедитесь, чтобы заменить *< group\_SID >* со значением SID группы и *< true\_or\_false >* с помощью `true` или `false`, которая зависит от вашей конкретное условие правила на основании ли поступлении запроса на доступ из экстрасети или интрасети.  
  
### <a name="to-grant-access-to-an-application-based-on-user-data-via-windows-powershell"></a>Чтобы предоставить доступ к приложению на основе данных пользователя с помощью Windows PowerShell  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду.  
  
    ```  
    $rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust  
  
    ```  
  
> [!NOTE]  
> Убедитесь, что заменить *< relying\_party\_trust >* со значением доверия с проверяющей стороной.  
  
2.  В том же окне команд Windows PowerShell выполните следующую команду.  
  
    ```  
  
      $GroupAuthzRule = "@RuleTemplate = `“Authorization`” @RuleName = `"Foo`" c:[Type == `"https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid`", Value =~ `"^(?i)<group_SID>$`"] =>issue(Type = `"https://schemas.microsoft.com/authorization/claims/deny`", Value = `"DenyUsersWithClaim`");"  
    Set-AdfsRelyingPartyTrust –TargetRelyingParty $rp –IssuanceAuthorizationRules $GroupAuthzRule  
    ```  
  
> [!NOTE]  
> > Убедитесь, что заменить *< group\_SID >* со значением идентификатора безопасности для вашей группы AD.  
  
### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-this-users-identity-was-validated-with-mfa"></a>Чтобы предоставить доступ к приложению, защищаемому AD FS, только если удостоверение пользователя проверено с помощью многофакторной проверки Подлинности  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду.  
  

    `$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust ` 
 
  
> [!NOTE]  
> Убедитесь, что заменить *< relying\_party\_trust >* со значением доверия с проверяющей стороной.  
  
2.  В том же окне команд Windows PowerShell выполните следующую команду.  
  
    ```  
    $GroupAuthzRule = "@RuleTemplate = `"Authorization`"  
    @RuleName = `"PermitAccessWithMFA`"  
    c:[Type == `"https://schemas.microsoft.com/claims/authnmethodsreferences`", Value =~ `"^(?i)https://schemas\.microsoft\.com/claims/multipleauthn$`"] => issue(Type = `"https://schemas.microsoft.com/authorization/claims/permit`", Value = ‘“PermitUsersWithClaim’");"  
  
    ```  
  
### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-the-access-request-comes-from-a-workplace-joined-device-that-is-registered-to-the-user"></a>Для предоставления доступа к приложению, защищаемому AD FS только если запрос на доступ поступает с устройства, подключенного к workplace\, которое зарегистрировано для пользователя  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду.  
  
    ```  
    $rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust  
  
    ```  
  
> [!NOTE]  
> Убедитесь, что заменить *< relying\_party\_trust >* со значением доверия с проверяющей стороной.  
  
2.  В том же окне команд Windows PowerShell выполните следующую команду.  
  

    $GroupAuthzRule = "@RuleTemplate = `"Authorization`»  
    @RuleName = `"PermitAccessFromRegisteredWorkplaceJoinedDevice`"  
    c: [тип == `"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser`«, значение = ~ `"^(?i)true$`»] = > проблемы (тип = `"https://schemas.microsoft.com/authorization/claims/permit`", значение = `"PermitUsersWithClaim`»);  
  

  
### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-the-access-request-comes-from-a-workplace-joined-device-that-is-registered-to-a-user-whose-identity-has-been-validated-with-mfa"></a>Чтобы предоставить доступ к приложению, защищаемому AD FS только если запрос на доступ поступает с устройства, подключенного к workplace\, которое зарегистрировано для пользователя, удостоверение которого проверено с помощью многофакторной проверки Подлинности  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду.  
  
 
    `$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust ` 
 
  
> [!NOTE]  
> Убедитесь, что заменить *< relying\_party\_trust >* со значением доверия с проверяющей стороной.  
  
2.  В том же окне команд Windows PowerShell выполните следующую команду.  
  
    ```  
    $GroupAuthzRule = ‘@RuleTemplate = “Authorization”  
    @RuleName = “RequireMFAOnRegisteredWorkplaceJoinedDevice”  
    c1:[Type == `"https://schemas.microsoft.com/claims/authnmethodsreferences`", Value =~ `"^(?i)http://schemas\.microsoft\.com/claims/multipleauthn$`"] &&  
    c2:[Type == `"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser`", Value =~ `"^(?i)true$”] => issue(Type = "https://schemas.microsoft.com/authorization/claims/permit`", Value = `"PermitUsersWithClaim`");"  
  
    ```  
  
### <a name="to-grant-extranet-access-to-an-application-secured-by-ad-fs-only-if-the-access-request-comes-from-a-user-whose-identity-has-been-validated-with-mfa"></a>Предоставление доступа из экстрасети к приложению, защищаемому AD FS, только в том случае, если запрос на доступ поступает от пользователя, удостоверение которого проверено с помощью многофакторной проверки Подлинности  
  
1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду.  
  
 
    `$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust`  

  
> [!NOTE]  
> Убедитесь, что заменить *< relying\_party\_trust >* со значением доверия с проверяющей стороной.  
  
2.  В том же окне команд Windows PowerShell выполните следующую команду.  
  

    $GroupAuthzRule = "@RuleTemplate = `"Authorization`»  
    @RuleName = `"RequireMFAForExtranetAccess`"  
    C1: [тип == `"https://schemas.microsoft.com/claims/authnmethodsreferences`«, значение = ~ `"^(?i)http://schemas\.microsoft\.com/claims/multipleauthn$`»] & &  
    C2: [тип == `"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork`«, значение = ~ `"^(?i)false$`»] = > проблемы (тип = `"https://schemas.microsoft.com/authorization/claims/permit`», значение = `"PermitUsersWithClaim`»);»  

## <a name="additional-references"></a>Дополнительные ссылки  

[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)
