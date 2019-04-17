---
title: "Один журнала ожидания для подключения OpenID с помощью AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 11/17/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 3af10ec139edbc72e75bf80f544ac5b4f1cf9222
ms.sourcegitcommit: c16a2bf1b8a48ff267e71ff29f18b5e5cda003e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
#  <a name="single-log-out-for-openid-connect-with-ad-fs"></a>Один журнала ожидания для подключения OpenID с помощью AD FS

## <a name="overview"></a>Обзор
Построенная на начальной поддержку Oauth в AD FS в Windows Server 2012 R2, AD FS 2016 введена поддержка подключения OpenId входа. С помощью [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801), AD FS 2016 теперь поддерживает один журнал ухода для подключения OpenId сценариев. В этой статье представлен обзор одного журнала ухода для подключения OpenId сценария, а также инструкции о том, как использовать его для подключения OpenId приложений в AD FS.


## <a name="discovery-doc"></a>Обнаружение документов
Подключения OpenID использует JSON документа под названием «документ обнаружения» для предоставления сведений о конфигурации.  Сюда входят коды URI проверки подлинности, маркер, сведений о пользователях и конечные точки открытым.  Ниже приведен пример в документе обнаружения.

```
{
"issuer":"https://fs.fabidentity.com/adfs",
"authorization_endpoint":"https://fs.fabidentity.com/adfs/oauth2/authorize/",
"token_endpoint":"https://fs.fabidentity.com/adfs/oauth2/token/",
"jwks_uri":"https://fs.fabidentity.com/adfs/discovery/keys",
"token_endpoint_auth_methods_supported":["client_secret_post","client_secret_basic","private_key_jwt","windows_client_authentication"],
"response_types_supported":["code","id_token","code id_token","id_token token","code token","code id_token token"],
"response_modes_supported":["query","fragment","form_post"],
"grant_types_supported":["authorization_code","refresh_token","client_credentials","urn:ietf:params:oauth:grant-type:jwt-bearer","implicit","password","srv_challenge"],
"subject_types_supported":["pairwise"],
"scopes_supported":["allatclaims","email","user_impersonation","logon_cert","aza","profile","vpn_cert","winhello_cert","openid"],
"id_token_signing_alg_values_supported":["RS256"],
"token_endpoint_auth_signing_alg_values_supported":["RS256"],
"access_token_issuer":"http://fs.fabidentity.com/adfs/services/trust",
"claims_supported":["aud","iss","iat","exp","auth_time","nonce","at_hash","c_hash","sub","upn","unique_name","pwd_url","pwd_exp","sid"],
"microsoft_multi_refresh_token":true,
"userinfo_endpoint":"https://fs.fabidentity.com/adfs/userinfo",
"capabilities":[],
"end_session_endpoint":"https://fs.fabidentity.com/adfs/oauth2/logout",
"as_access_token_token_binding_supported":true,
"as_refresh_token_token_binding_supported":true,
"resource_access_token_token_binding_supported":true,
"op_id_token_token_binding_supported":true,
"rp_id_token_token_binding_supported":true,
"frontchannel_logout_supported":true,
"frontchannel_logout_session_supported":true
} 
 
```



Следующие дополнительные значения можно найти в документе обнаружения для указания поддержки передней канал выхода:

- frontchannel_logout_supported: значение будет равно «true»
- frontchannel_logout_session_supported: значение будет равно «true».
- end_session_endpoint: это выход OAuth URI, который клиент может использовать для запуска выхода из системы на сервере.


## <a name="ad-fs-server-configuration"></a>Конфигурация сервера AD FS
Свойства Служб федерации Active Directory EnableOAuthLogout будет включена по умолчанию.  Это свойство указывает сервера AD FS, чтобы искать URL-адрес (LogoutURI) с SID запуск выход на клиенте. Если у вас [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801) установленных, можно использовать следующую команду PowerShell:

```PowerShell
Set-ADFSProperties -EnableOAuthLogout $true
```

>[!NOTE]
> `EnableOAuthLogout` параметр будут помечены как устаревшие после установки [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801). `EnableOAUthLogout` всегда будет значение true и не будет влиять на функциональности выхода.

>[!NOTE]
>поддерживается frontchannel_logout **только** после installtion из [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801)

## <a name="client-configuration"></a>Настройка клиента
Клиент должен реализовать URL-адрес, который «выходит из системы» вошедшего пользователя. Администратор может настроить LogoutUri в конфигурации клиента, используя следующие командлеты PowerShell. 


- `(Add | Set)-AdfsNativeApplication`
- `(Add | Set)-AdfsServerApplication`
- `(Add | Set)-AdfsClient`

```PowerShell
Set-AdfsClient -LogoutUri <url>
```

`LogoutUri`URL-адрес, используемый AF FS «выход» пользователя. Для реализации `LogoutUri`, клиент, необходимо убедиться, что все очищает состояние проверки подлинности пользователя в приложении, например, удаление проверки подлинности токены, что он имеет. AD FS будет найдите этот URL-адрес с ИД безопасности как параметр запроса сигналов проверяющей стороны и приложения для пользователя из системы. 

![](media/ad-fs-logout-openid-connect/adfs_single_logout2.png)


1.  **Токен OAuth с Идентификатором сеанса**: AD FS включает идентификатор сеанса в токен OAuth во время выпуска маркера id_token. Это будет использоваться позже с помощью AD FS для определения соответствующих cookie единого входа для очищен для пользователя.
2.  **Пользователь инициирует выход на компьютере App1**: пользователь может запустить выход из любых приложений, вошедший в систему. В этом примере сценария пользователь инициирует выход из компьютера App1.
3.  **Приложение отправляет запрос выход AD FS**: после выхода из системы, когда пользователь инициирует, приложение отправляет запрос GET end_session_endpoint Служб федерации Active Directory. Приложения можно включать id_token_hint в качестве параметра запроса. При наличии id_token_hint AD FS будет использовать в сочетании с Идентификатором сеанса на рис. out какие URI клиента должны быть перенаправлены на после выхода (post_logout_redirect_uri).  Post_logout_redirect_uri должен быть допустимым uri, зарегистрированных с помощью параметра RedirectUris AD FS.
4.  **Службы федерации Active Directory отправляет выхода вошедшего в систему клиентам**: службы федерации Active Directory использует значение идентификатора сеанса, чтобы найти соответствующие клиенты пользователя входит в. Обнаруженные клиентов отправляется запрос на LogoutUri, зарегистрированных с помощью AD FS, чтобы инициировать выход на стороне клиента.

## <a name="faqs"></a>Вопросы и ответы
**Вопрос:** я не вижу параметры frontchannel_logout_supported и frontchannel_logout_session_supported в документе обнаружения.</br>
**Ответ** убедитесь, что у вас есть [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801) установлен на все серверы Служб федерации Active Directory. Ссылки для одного журнала в Server 2016 с [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801).

**Вопрос:** я настроили единого выхода, как указано, но остается вошедшего в систему на других клиентских компьютерах.</br>
**Ответ** убедитесь, что `LogoutUri`установлено для всех клиентов, что пользователь не выполнил вход. Также, AD FS выполняет лучшем попытки отправки запроса на выход на зарегистрированный `LogoutUri`. Клиент должен реализовать логику для обработки запроса и выполните действия для выхода пользователя из приложения.</br>

**Вопрос:** Если после выхода из системы, одному из клиентов возвращается к AD FS с маркером допустимый обновления, службы федерации Active Directory выдаст маркер доступа?</br>
**Ответ** Да. Именно клиентское приложение для удаления всех зарегистрированных артефакты после получения запроса на выход на зарегистрированный `LogoutUri`.


## <a name="next-steps"></a>Дальнейшие действия
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
