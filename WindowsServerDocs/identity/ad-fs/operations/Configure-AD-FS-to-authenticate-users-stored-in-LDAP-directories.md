---
ms.assetid: e863ab80-4e4c-48d3-bdaa-31815ef36bae
title: "Настройка AD FS для проверки подлинности пользователей, хранящихся в каталогах LDAP"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 05f8b8991e664a84c3f2b3200de4068af8d1476a
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="configure-ad-fs-to-authenticate-users-stored-in-ldap-directories"></a>Настройка AD FS для проверки подлинности пользователей, хранящихся в каталогах LDAP

>Область применения: Windows Server 2016

В данном разделе описаны конфигурации, необходимые для включения инфраструктуры AD FS для проверки подлинности пользователей, удостоверения хранятся в каталогах несоответствия v3 облегченного доступа к каталогам LDAP Directory Access Protocol ().

Во многих организациях решения для управления удостоверениями представляют сочетание Active Directory, AD LDS или каталогов LDAP сторонних производителей. С добавлением поддержки AD FS для проверки подлинности пользователей, хранящихся в каталогах v3 совместимый с LDAP, можно воспользоваться из всего корпоративного уровня набор независимо от того, где хранятся удостоверения пользователей возможностей Служб федерации Active Directory. AD FS поддерживает все совместимые v3 каталога LDAP.

> [!NOTE]
> Некоторые из функций Служб федерации Active Directory включают единого входа (SSO), проверку подлинности устройства, политики гибкого условного доступа, поддержка работы из-из любого места через интеграцию с прокси веб-приложения и безупречное федерации с Azure AD, который в свою очередь активирует вас и ваших пользователей для использования в облаке, включая Office 365 и других приложений SaaS.  Дополнительные сведения см. в разделе [Обзор служб федерации Active Directory ](../../ad-fs/AD-FS-2016-Overview.md).

Чтобы AD FS для проверки подлинности пользователей из каталога LDAP, необходимо подключить этот каталог LDAP фермы AD FS, создав **доверия с поставщиком утверждений локального **.  Отношения доверия с поставщиком утверждений локального это объект доверия, представляющий каталог LDAP в ферме AD FS. Локальный доверия поставщика утверждений объект состоит из разных идентификаторов, имен и правил, идентифицирующих этого каталога LDAP к службе федерации.

Может поддерживать несколько каталогов LDAP, каждый из которых собственную конфигурацию, в пределах фермы AD FS, добавив несколько **отношения доверия с поставщиком утверждений локального **. Кроме того леса AD DS, которые не являются доверенными для леса, будет находиться в AD FS можно моделировать также как отношения доверия с поставщиком утверждений локальный. Отношения доверия с поставщиком утверждений локального можно создать с помощью Windows PowerShell.

Каталогов LDAP (отношения доверия поставщика утверждений локального) может работать вместе с AD каталоги (отношения доверия поставщика утверждений) на том же сервере Служб федерации Active Directory, в пределах фермы AD FS, таким образом, один экземпляр Служб федерации Active Directory для проверки подлинности и авторизации доступа для пользователей, которые хранятся в обоих AD и каталогов не относящихся к AD.

Для проверки подлинности пользователей в каталогах LDAP поддерживается только на основе форм для проверки подлинности. На основе сертификатов и встроенной проверки подлинности Windows, не поддерживаются для проверки подлинности пользователей в каталогах LDAP.

Все протоколы пассивный авторизации, которые поддерживаются в AD FS, включая SAML, WS-Federation и OAuth также поддерживаются для удостоверений, которые хранятся в каталогах LDAP.

Протокол WS-Trust active авторизации также поддерживается для удостоверений, которые хранятся в каталогах LDAP.

## <a name="configure-ad-fs-to-authenticate-users-stored-in-an-ldap-directory"></a>Настройка AD FS для проверки подлинности пользователей, хранящихся в каталоге LDAP
Чтобы настроить ферму AD FS для проверки подлинности пользователей из каталога LDAP, необходимо выполнить следующие действия.

1.  Сначала необходимо настроить подключение к каталогу LDAP с помощью **New-AdfsLdapServerConnection** командлета:

    ```
    $DirectoryCred = Get-Credential
    $vendorDirectory = New-AdfsLdapServerConnection -HostName dirserver -Port 50000 -SslMode None -AuthenticationMethod Basic -Credential $DirectoryCred
    ```

    > [!NOTE]
    > Рекомендуется создать новый объект подключения для каждого сервера LDAP, который вы хотите подключиться к. AD FS можно подключиться к нескольким серверам LDAP реплики и автоматически переключиться на случай, если определенный сервер LDAP не работает. Для случаев, можно создать один AdfsLdapServerConnection для каждого из этих серверов LDAP реплики и затем добавить массив объектов соединения, с помощью**LdapServerConnection** параметр **добавить AdfsLocalClaimsProviderTrust** командлета.

    **Примечание:** попытка использовать Get-Credential и введите различающееся имя и пароль, чтобы использовать для привязки к экземпляру LDAP может привести к сбою из-за требования интерфейса пользователя для конкретного ввода форматы, например, домен\имя_пользователя или user@domain.tld. Вместо этого можно использовать командлет ConvertTo-SecureString следующим образом (в этом примере предполагается uid = администратора, ou = системы как различающееся имя учетные данные, чтобы можно было выполнить привязку к экземпляру LDAP):

    ```
    $ldapuser = ConvertTo-SecureString -string "uid=admin,ou=system" -asplaintext -force
    $DirectoryCred = Get-Credential -username $ldapuser -Message "Enter the credentials to bind to the LDAP instance:"
    ```

    Затем введите пароль для uid = администратора и выполните оставшиеся действия.

2.  Затем можно выполнить дополнительный шаг сопоставление атрибутов LDAP для существующих утверждений Служб федерации Active Directory, с помощью **New-AdfsLdapAttributeToClaimMapping** командлета. В приведенном ниже примере сопоставить givenName, Фамилия, и CommonName LDAP атрибуты для утверждений Служб федерации Active Directory:

    ```
    #Map given name claim
    $GivenName = New-AdfsLdapAttributeToClaimMapping -LdapAttribute givenName -ClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname"
    # Map surname claim
    $Surname = New-AdfsLdapAttributeToClaimMapping -LdapAttribute sn -ClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname"
    # Map common name claim
    $CommonName = New-AdfsLdapAttributeToClaimMapping -LdapAttribute cn -ClaimType "http://schemas.xmlsoap.org/claims/CommonName"
    ```

    Это сопоставление выполняется для предоставления атрибуты из хранилища LDAP как утверждений в AD FS для создания правила управления условным доступом в AD FS. Он также позволяет работать с пользовательские схемы в магазинах LDAP, предоставляя простой способ сопоставление атрибутов LDAP для утверждений Служб федерации Active Directory.

3.  Наконец, необходимо зарегистрировать хранилища LDAP с помощью AD FS, как локального утверждений с помощью доверия поставщика **добавить AdfsLocalClaimsProviderTrust** командлета:

    ```
    Add-AdfsLocalClaimsProviderTrust -Name "Vendors" -Identifier "urn:vendors" -Type Ldap

    # Connection info
    -LdapServerConnection $vendorDirectory 

    # How to locate user objects in directory
    -UserObjectClass inetOrgPerson -UserContainer "CN=VendorsContainer,CN=VendorsPartition" -LdapAuthenticationMethod Basic 

    # Claims for authenticated users
    -AnchorClaimLdapAttribute mail -AnchorClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -LdapAttributeToClaimMapping @($GivenName, $Surname, $CommonName) 

    # General claims provider properties
    -AcceptanceTransformRules "c:[Type != ''] => issue(claim=c);" -Enabled $true 

    # Optional - supply user name suffix if you want to use Ws-Trust
    -OrganizationalAccountSuffix "vendors.contoso.com"

    ```

    В приведенном выше примере создании отношения доверия с поставщиком утверждений локального под названием «Поставщики». Указываются сведения о подключении для Служб федерации Active Directory для подключения к каталогу LDAP этого отношения доверия с поставщиком утверждений локального представляет путем назначения `$vendorDirectory`для `-LdapServerConnection`параметра. Обратите внимание, что на первом шаге, присвоенный `$vendorDirectory`строку подключения для использования при подключении к вашей определенного каталога LDAP. Наконец, вы указываете, `$GivenName`, `$Surname`, и `$CommonName`атрибутов LDAP (которые сопоставляется с утверждений AD FS) будут использоваться для условного управления доступом, включая политики многофакторной проверки подлинности и правила авторизации выдачи, а также для выдачи через утверждений в токены AD FS выдан безопасности. Чтобы воспользоваться active протоколы, такие как Ws-Trust AD FS, необходимо указать параметр OrganizationalAccountSuffix, который позволяет AD FS для устранения неоднозначности между локальной утверждений отношения доверия с поставщиком при обслуживании запрос active авторизации.

## <a name="see-also"></a>См. также:
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)


