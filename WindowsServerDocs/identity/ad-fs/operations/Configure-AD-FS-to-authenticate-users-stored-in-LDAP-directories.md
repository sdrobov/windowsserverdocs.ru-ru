---
ms.assetid: e863ab80-4e4c-48d3-bdaa-31815ef36bae
title: Настройка AD FS для проверки подлинности пользователей, хранящихся в каталогах LDAP
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 2053f0a93f33cdfdd85eec8cdbb6eca4ebad1ff0
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66444926"
---
# <a name="configure-ad-fs-to-authenticate-users-stored-in-ldap-directories"></a>Настройка AD FS для проверки подлинности пользователей, хранящихся в каталогах LDAP

В данном разделе описаны конфигурации, необходимые для включения инфраструктуры AD FS для проверки подлинности пользователей, удостоверения хранятся в каталогах v3-совместимым Lightweight Directory Access Protocol (LDAP).

Во многих организациях решения для управления удостоверениями состоит из комбинации Active Directory, AD LDS или сторонние каталоги LDAP. С добавлением поддержки AD FS для проверки подлинности пользователей, хранящихся в каталогах v3 с LDAP, можно воспользоваться из всей корпоративного наборе независимо от того, где хранятся удостоверения пользователей возможностей AD FS. AD FS поддерживает любой LDAP v3-совместимый каталог.

> [!NOTE]
> Некоторые средства AD FS Включить единый вход (SSO), проверка подлинности устройства, политики условного доступа на гибкий, поддержку работы из — в любом месте за счет интеграции с веб-прокси приложения и простой федерации с Azure AD, который в свою очередь позволяет пользователям использования облака, включая Office 365 и другим приложениям SaaS.  Дополнительные сведения см. в разделе [Обзор служб федерации Active Directory](../../ad-fs/AD-FS-2016-Overview.md).

Чтобы AD FS для проверки подлинности пользователей из каталога LDAP, необходимо подключиться этот каталог LDAP к ферме AD FS, создав **отношения доверия с поставщиком утверждений локального**.  Отношения доверия поставщика утверждений локального является объект доверия, представляющий каталог LDAP в ферме AD FS. Доверия локального поставщика утверждений состоит из разных идентификаторов, имен и правил, идентифицирующих этого каталога LDAP к службе федерации.

Может поддерживать несколько каталогов LDAP, каждый с собственными конфигурациями, в пределах фермы AD FS, добавив несколько **отношения доверия с поставщиком утверждений локального**. Кроме того лесов AD DS, которые не являются доверенными, AD FS находится в лесу можно также моделировать в виде отношения доверия с поставщиком локального утверждений. Можно создать отношения доверия с поставщиком локального утверждений с помощью Windows PowerShell.

Каталоги LDAP (отношения доверия поставщика утверждений локального) могут сосуществовать с каталогов AD (отношения доверия поставщика утверждений) на одном сервере AD FS, в пределах одной и той же ферме AD FS, таким образом, один экземпляр AD FS может выполнять проверки подлинности и авторизации доступа для пользователей, которым хранятся как в AD и без AD каталоги.

Только на основе форм проверки подлинности поддерживается для проверки подлинности пользователей из каталогов LDAP. На основе сертификатов и встроенная проверка подлинности Windows не поддерживаются для проверки подлинности пользователей в каталогах LDAP.

Все протоколы пассивный авторизации, которые поддерживаются службами AD FS, включая SAML, WS-Federation и OAuth, также поддерживаются для удостоверений, которые хранятся в каталогах LDAP.

Протокол WS-Trust active авторизации также поддерживается для удостоверений, которые хранятся в каталогах LDAP.

## <a name="configure-ad-fs-to-authenticate-users-stored-in-an-ldap-directory"></a>Настройка AD FS для проверки подлинности пользователей, хранящихся в каталоге LDAP
Для настройки фермы AD FS для проверки подлинности пользователей из каталога LDAP, можно выполнить следующие действия:

1. Во-первых, настройки подключения каталога LDAP с помощью **New AdfsLdapServerConnection** командлета:

   ```
   $DirectoryCred = Get-Credential
   $vendorDirectory = New-AdfsLdapServerConnection -HostName dirserver -Port 50000 -SslMode None -AuthenticationMethod Basic -Credential $DirectoryCred
   ```

   > [!NOTE]
   > Рекомендуется создать новый объект подключения для каждого сервера LDAP, который вы хотите подключиться к. AD FS можно подключаться к нескольким серверам LDAP реплики и автоматически выполнить отработку отказа в случае конкретного сервера LDAP не работает. Для такого случая, можно создать один AdfsLdapServerConnection для каждого из этих серверов LDAP реплики и затем добавить массив объектов соединения, с помощью**LdapServerConnection** параметр  **Добавить AdfsLocalClaimsProviderTrust** командлета.

   **ПРИМЕЧАНИЕ.** Попытка использовать Get-Credential и введите различающееся имя и пароль, которая будет использоваться для привязки к LDAP экземпляра может привести к ошибке, так как требования интерфейс пользователя для определенных входных форматов, например, домен\имя_пользователя или user@domain.tld. Вместо этого можно использовать командлет ConvertTo-SecureString следующим образом (в приведенном ниже примере предполагается, что uid = admin, ou = системы как Различающееся имя учетных данных для привязки к экземпляру LDAP):

   ```
   $ldapuser = ConvertTo-SecureString -string "uid=admin,ou=system" -asplaintext -force
   $DirectoryCred = Get-Credential -username $ldapuser -Message "Enter the credentials to bind to the LDAP instance:"
   ```

   Затем введите пароль для uid = администратора и выполните остальные шаги.

2. Затем можно выполнить дополнительный этап сопоставление атрибутов LDAP с существующей утверждений AD FS, с помощью **New AdfsLdapAttributeToClaimMapping** командлета. В следующем примере сопоставления givenName, Surname и CommonName LDAP атрибуты к утверждениям AD FS:

   ```
   #Map given name claim
   $GivenName = New-AdfsLdapAttributeToClaimMapping -LdapAttribute givenName -ClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname"
   # Map surname claim
   $Surname = New-AdfsLdapAttributeToClaimMapping -LdapAttribute sn -ClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname"
   # Map common name claim
   $CommonName = New-AdfsLdapAttributeToClaimMapping -LdapAttribute cn -ClaimType "http://schemas.xmlsoap.org/claims/CommonName"
   ```

   Это сопоставление выполняется для предоставления атрибутов в магазине LDAP как утверждений в AD FS для создания правила управления условного доступа в AD FS. Он также позволяет AD FS для работы с пользовательских схем в хранилищах LDAP, предоставляя простой способ сопоставления атрибутов LDAP с утверждений.

3. Наконец, необходимо зарегистрировать хранилище LDAP с AD FS, как локальной утверждений с помощью отношения доверия поставщика **AdfsLocalClaimsProviderTrust добавить** командлета:

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

   В приведенном выше примере вы создаете доверия с поставщиком утверждений локального называется «Поставщики». При указании сведений о подключении для AD FS для подключения к каталогу LDAP этого отношения доверия с поставщиком утверждений локального представляет путем назначения `$vendorDirectory` для `-LdapServerConnection` параметра. Обратите внимание, что на первом шаге, назначенные `$vendorDirectory` строку подключения для использования при подключении в определенный каталог LDAP. Наконец, вы указываете, `$GivenName`, `$Surname`, и `$CommonName` атрибутов LDAP (отнесенные к утверждениям AD FS), следует использовать для условного управления доступом, включая политики многофакторной проверки подлинности и выдачи правил авторизации, а также как и для выдачи с помощью утверждений в токены AD FS безопасности. Для использования active протоколов, таких как Ws-Trust с AD FS, необходимо указать параметр OrganizationalAccountSuffix, который позволяет устранить неоднозначность между локальной утверждений отношений доверия с поставщиком при обслуживании запроса на авторизацию active AD FS.

## <a name="see-also"></a>См. также
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)


