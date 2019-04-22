---
title: Настройка утверждений может быть выпущен в "id_token", при использовании OAuth или OpenID Connect с AD FS 2016
description: Технический обзор маркера conecpts пользовательский идентификатор, в AD FS 2016
author: anandyadavmsft
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.reviewer: anandy
ms.technology: identity-adfs
ms.openlocfilehash: 8c8e14f22a4bca5b6d32e841814a58a4b4ddca01
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59820645"
---
# <a name="customize-claims-to-be-emitted-in-idtoken-when-using-openid-connect-or-oauth-with-ad-fs-2016"></a>Настройка утверждений может быть выпущен в "id_token", при использовании OAuth или OpenID Connect с AD FS 2016

## <a name="overview"></a>Обзор
Статья [здесь](enabling-openId-connect-with-ad-fs.md) показано, как создать приложение, которое использует OpenID Connect для входа AD FS. Однако по умолчанию есть только фиксированный набор утверждений, доступных в id_token. AD FS 2016 имеет возможность настроить id_token в сценариях OpenID Connect.

## <a name="when-are-custom-id-token-used"></a>Когда будете пользовательский идентификатор токен, используемый?
В некоторых сценариях может оказаться, что клиентское приложение не имеет ресурс, который пытается получить доступ к. Таким образом не требуется маркер доступа. В таких случаях клиентское приложение по сути необходимо только идентификатор токена, однако с некоторые дополнительные утверждения, чтобы помочь в функциональные возможности.

## <a name="what-are-the-restrictions-on-getting-custom-claims-in-id-token"></a>Каковы ограничения на получение пользовательских утверждений в идентификатор маркера?

### <a name="scenario-1"></a>Сценарий 1

![ограничения](media/Custom-Id-Tokens-in-AD-FS/res1.png)

1.  response_mode задается как form_post
2.  Только общедоступные клиенты могут получить настраиваемые утверждения в идентификатор токена
3.  Идентификатор проверяющей стороны следует использовать тот же идентификатор клиента

### <a name="scenario-2"></a>Сценарий 2

![ограничения](media/Custom-Id-Tokens-in-AD-FS/restrict2.png)

С помощью [KB4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472) установленные на серверах AD FS
1.  response_mode задается как form_post
2.  Назначьте область allatclaims клиенту — пара RP.
Область можно назначить с помощью командлет Grant-ADFSApplicationPermission, как показано в следующем примере:

``` powershell
Grant-AdfsApplicationPermission -ClientRoleIdentifier "https://my/privateclient" -ServerRoleIdentifier "https://rp/fedpassive" -ScopeNames "allatclaims","openid"
```

## <a name="creating-an-oauth-application-to-handle-custom-claims-in-id-token"></a>Создание приложения OAuth для обработки пользовательских утверждений в маркере
Ознакомьтесь со статьей [здесь](Enabling-OpenId-Connect-with-AD-FS-2016.md) для создания приложения приложения, использующего входа AD FS для OpenID Connect. Затем выполните следующие действия, чтобы настроить приложение в AD FS для получения маркера Идентификации с помощью настраиваемых утверждений.

### <a name="create-the-application-group-in-ad-fs-2016"></a>Создание группы приложений в AD FS 2016

1.  Создайте группу приложений, на основе нового шаблона, показано ниже, именем CustomTokenClient.

![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap1.png)

2. Этот шаблон создает конфиденциального клиента. Обратите внимание, идентификатор и указать возвращаемое URI в качестве URL-адрес SSL проекта VS.

![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap2.png)

3.  В следующем шаге выберите **создать общий секрет** для создания учетных данных клиента и скопируйте созданные учетные данные клиента.

![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap3.png)

4. Нажмите кнопку **Далее** и продолжить работу мастера.

![клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap4.png)

### <a name="create-the-relying-party"></a>Создать проверяющую сторону
Чтобы добавить настраиваемые утверждения в идентификатор токена, необходимо создать RP, будут добавлены, утверждения в маркере идентификатора. С помощью мастера добавления доверия с проверяющей стороной для создания новой RP, как показано ниже:
 
![Проверяющая сторона](media/Custom-Id-Tokens-in-AD-FS/rpsnap1.png)

После создания проверяющую сторону правой кнопкой мыши щелкните запись доверяющей стороной и выберите **редактирования утверждения политики выдачи** для добавления правила выдачи утверждений. Добавьте необходимые пользовательские утверждения для маркера Идентификации, как показано ниже:

![Проверяющая сторона](media/Custom-Id-Tokens-in-AD-FS/rpsnap2.png)

### <a name="assign-allatclaims-scope-to-the-pair-of-client-and-relying-party"></a>Назначить область «allatclaims» к паре клиент и проверяющая сторона
С помощью PowerShell на сервере AD FS, назначить новую область allatclaims, как показано в следующем примере (изменить clientID и сервер:

``` powershell
Grant-AdfsApplicationPermission -ClientRoleIdentifier "5db77ce4-cedf-4319-85f7-cc230b7022e0" -ServerRoleIdentifier "https://customidrp1/" -ScopeNames "allatclaims","openid"
```

>[!NOTE]
>Изменить ClientRoleIdentifier и ServerRoleIdentifier в соответствии с настройками приложения

## <a name="test-the-custom-claims-in-id-token"></a>Тестирование пользовательских утверждений в маркере

Затем с помощью одного бита кода, который вы всегда использовали для доступа к утверждениям, вы увидите дополнительные утверждения, которые станут частью "id_token".
Например, в пример приложения .NET MVC, откройте один из файлов контроллера и введите следующий код ниже:


``` code
    [Authorize]
    public ActionResult About()
    {

        ClaimsPrincipal cp = ClaimsPrincipal.Current;

        string userName = cp.FindFirst(ClaimTypes.GivenName).Value;
        ViewBag.Message = String.Format("Hello {0}!", userName);
        return View();

    }

```

>[!NOTE]
>Имейте в виду, что в запросе Oauth2 необходим параметр ресурса.
>
>Неправильный пример:
>
>**HTTPS&#58;//sts.contoso.com/adfs/oauth2/authorize?response_type=id_token & область = openid & redirect_uri = https&#58;//myportal/auth & nonce = b3ceb943fc756d927777 & client_id = 72-9b22-ca7ab60cb4e7 6db3ec2a-075a - 4c & состояние = ресурс & 42c2c156aef47e8d0870 = 72-9b22-ca7ab60cb4e7 6db3ec2a-075a - 4c**
>
>Хорошим примером:
>
>**HTTPS&#58;//sts.contoso.com/adfs/oauth2/authorize?response_type=id_token & область = openid & redirect_uri = https&#58;//myportal/auth & nonce = b3ceb943fc756d927777 & client_id = 72-9b22-ca7ab60cb4e7 6db3ec2a-075a - 4c & состояние = ресурс & 42c2c156aef47e8d0870 = https&#58;//customidrp1/ & response_mode = form_post**
>
>Если параметр ресурса не существует в запросе может появиться ошибка или маркером без все пользовательские утверждения.

## <a name="next-steps"></a>Следующие шаги
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
