---
title: Однократный выход для OpenID Connect в AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 11/17/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 3af10ec139edbc72e75bf80f544ac5b4f1cf9222
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825775"
---
#  <a name="single-log-out-for-openid-connect-with-ad-fs"></a>Однократный выход для OpenID Connect в AD FS

## <a name="overview"></a>Обзор
Основываясь на первоначально поддержка Oauth в AD FS в Windows Server 2012 R2, AD FS 2016 появилась поддержка OpenId Connect единого входа. С помощью [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801), AD FS 2016 теперь поддерживает единого выхода для сценариев OpenId Connect. В этой статье содержится обзор единого выхода для сценария, OpenId Connect и приводятся рекомендации по способы ее использования для приложений OpenId Connect в AD FS.


## <a name="discovery-doc"></a>Документ обнаружения
OpenID Connect использует документе JSON, который называется «документа обнаружения» для предоставления сведений о конфигурации.  Сюда входят URI-адреса проверки подлинности, маркер, сведений о пользователе и конечные точки public.  Ниже приведен пример документа обнаружения.

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



Следующие дополнительные значения будут доступны в документе обнаружения, чтобы указать поддержку для внешнего канала выхода:

- frontchannel_logout_supported: значение будет равно «true»
- frontchannel_logout_session_supported: значение будет равно «true».
- end_session_endpoint: это URI, который клиент может использовать, чтобы инициировать выход из системы на сервере выхода OAuth.


## <a name="ad-fs-server-configuration"></a>Конфигурация сервера AD FS
Свойства служб AD FS EnableOAuthLogout будет включено по умолчанию.  Это свойство указывает, что сервер AD FS для поиска URL-адрес (LogoutURI) с идентификатором безопасности, чтобы инициировать выход из системы на клиентском компьютере. Если у вас нет [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801) установленных, можно использовать следующую команду PowerShell:

```PowerShell
Set-ADFSProperties -EnableOAuthLogout $true
```

>[!NOTE]
> `EnableOAuthLogout` параметр будут помечены как устаревшие после установки [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801). `EnableOAUthLogout` всегда будет иметь значение true и не оказывает влияния на функцию выхода.

>[!NOTE]
>поддерживается frontchannel_logout **только** после установки из [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801)

## <a name="client-configuration"></a>Конфигурация клиента
Клиент должен реализовать URL-адрес, на который «выходе из системы» вошедшего пользователя. Администратор может настроить LogoutUri в конфигурации клиента, используя следующие командлеты PowerShell. 


- `(Add | Set)-AdfsNativeApplication`
- `(Add | Set)-AdfsServerApplication`
- `(Add | Set)-AdfsClient`

```PowerShell
Set-AdfsClient -LogoutUri <url>
```

`LogoutUri` URL-адрес, используемый AF FS «выход» пользователя. Для реализации `LogoutUri`, потребности клиента, чтобы убедиться, что она очищает состояние проверки подлинности пользователя в приложении, например, удаление проверки подлинности маркеров, что у него есть. AD FS будет перейдите по этому АДРЕСУ, с ИД безопасности как параметр запроса, сигнализация проверяющей / приложению завершить сеанс пользователя. 

![](media/ad-fs-logout-openid-connect/adfs_single_logout2.png)


1.  **Токен OAuth с Идентификатором сеанса**: AD FS включает идентификатор сеанса в токен OAuth во время выдачи маркера "id_token". Это будет использоваться позже с помощью AD FS для идентификации соответствующие файлы cookie SSO очистки для пользователя.
2.  **Пользователь инициирует выход из системы на компьютере App1**: Пользователь может инициировать выход из системы из любых приложений, вошедшего в систему. В этом примере сценария пользователь инициирует выход из компьютера App1.
3.  **Приложение отправляет запрос на выход из системы AD FS**: После пользователь инициирует выход из системы, приложение отправляет запрос GET к end_session_endpoint из AD FS. Приложение можно дополнительно включить id_token_hint в качестве параметра этот запрос. При наличии id_token_hint AD FS будет использоваться в сочетании с Идентификатором сеанса для рис out какие URI клиента следует перенаправить после выхода (post_logout_redirect_uri).  Post_logout_redirect_uri должно быть допустимым uri, зарегистрированные с помощью параметра RedirectUris AD FS.
4.  **AD FS отправляет выхода вошедшего в систему клиентам**: AD FS использует значение идентификатор сеанса для поиска соответствующих клиентов, которые пользователь вошел в. Идентифицированные клиенты являются отправила запрос на LogoutUri, зарегистрированные с AD FS, чтобы инициировать выход из системы на стороне клиента.

## <a name="faqs"></a>Вопросы и ответы
**ВОПРОС** Я не вижу frontchannel_logout_supported и frontchannel_logout_session_supported параметры в документе обнаружения.</br>
**Ответ.** Убедитесь, что у вас есть [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801) установлена на всех серверах AD FS. Ссылаться на единого выхода в Server 2016 с [KB4038801](https://support.microsoft.com/en-gb/help/4038801/windows-10-update-kb4038801).

**ВОПРОС** Я настроил единый выход, как указано выше, но пользователь остается вошедшего в систему на других клиентов.</br>
**Ответ.** Убедитесь, что `LogoutUri` устанавливается для всех клиентов, на которой пользователь может войти в систему. Также, AD FS выполняет оптимистичный попытка отправки запроса выхода для зарегистрированного `LogoutUri`. Клиент должен реализовать логику для обработки запроса и предпринимать действия для выхода пользователя из приложения.</br>

**ВОПРОС** Если после выхода, один из клиентов возвращается к AD FS с помощью действительный маркер обновления, AD FS будет выдавать маркер доступа?</br>
**Ответ.** Да. Он отвечает за клиентского приложения для удаления всех зарегистрированных артефакты, после получения запроса выхода в зарегистрированный `LogoutUri`.


## <a name="next-steps"></a>Следующие шаги
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
