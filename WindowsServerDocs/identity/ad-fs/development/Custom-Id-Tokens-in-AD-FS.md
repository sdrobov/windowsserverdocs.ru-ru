---
title: "Настройка утверждений может быть выпущен в id_token при использовании подключения OpenID или OAuth с AD FS 2016"
description: "Технический обзор маркера conecpts пользовательский идентификатор, в AD FS 2016"
author: anandyadavmsft
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.reviewer: anandy
ms.technology: identity-adfs
ms.openlocfilehash: c17d50bb6d90726eafc3e585f16a7a8189a68392
ms.sourcegitcommit: c16a2bf1b8a48ff267e71ff29f18b5e5cda003e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="customize-claims-to-be-emitted-in-idtoken-when-using-openid-connect-or-oauth-with-ad-fs-2016"></a>Настройка утверждений может быть выпущен в id_token при использовании подключения OpenID или OAuth с AD FS 2016

## <a name="overview"></a>Обзор
Статья [здесь](enabling-openId-connect-with-ad-fs.md) показано, как создать приложение, которое использует службы федерации Active Directory для подключения OpenID вход. Однако по умолчанию существует фиксированный набор утверждений, доступные в id_token. AD FS 2016 имеет возможность изменить настройки id_token в сценариях подключения OpenID.

## <a name="when-are-custom-id-token-used"></a>Когда будете пользовательский идентификатор маркер используемый?
В некоторых сценариях это возможно, что клиентское приложение не имеет ресурс, который пытается получить доступ. Таким образом ему не требуется действительно маркер доступа. В таких случаях клиент по сути приложению только код токена, однако с некоторых дополнительных утверждений, для помощи в функциональные возможности.

## <a name="what-are-the-restrictions-on-getting-custom-claims-in-id-token"></a>Каковы ограничения на получение токена настраиваемые утверждения в код?

### <a name="scenario-1"></a>Сценарий 1

![Ограничения](media/Custom-Id-Tokens-in-AD-FS/res1.png)

1.  response_mode задается как form_post
2.  Только открытый клиенты можно получить настраиваемые утверждения в код маркера
3.  Идентификатор проверяющей стороны должен быть такой же, как идентификатор клиента

### <a name="scenario-2"></a>Сценарий 2

![Ограничения](media/Custom-Id-Tokens-in-AD-FS/restrict2.png)

С помощью [KB4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472) установить на серверах Служб федерации Active Directory
1.  response_mode задается как form_post
2.  Назначьте область allatclaims клиента — RP пары.
Область действия можно назначить с помощью командлета Grant-ADFSApplicationPermission, как показано в следующем примере:

``` powershell
Grant-AdfsApplicationPermission -ClientRoleIdentifier "https://my/privateclient" -ServerRoleIdentifier "https://rp/fedpassive" -ScopeNames "allatclaims","openid"
```

## <a name="creating-an-oauth-application-to-handle-custom-claims-in-id-token"></a>Создание приложения для обработки настраиваемые утверждения в токене идентификатор OAuth
Воспользуйтесь статьей [здесь](Enabling-OpenId-Connect-with-AD-FS-2016.md) Чтобы создать приложение приложения, которое использует службы федерации Active Directory для подключения OpenID войти в систему. Затем выполните следующие действия, чтобы настроить приложение в AD FS для получения маркера идентификатор настраиваемые утверждения.

### <a name="create-the-application-group-in-ad-fs-2016"></a>Создать группу приложений в AD FS 2016

1.  Создание группы приложений на основе нового шаблона, показанные ниже, под названием CustomTokenClient.

![Клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap1.png)

2. Этот шаблон создает конфиденциальных клиента. Запишите идентификатор и указать возвращаемое URI в качестве SSL URL-адрес проекта VS.

![Клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap2.png)

3.  На следующем шаге, выберите **создать общий секрет** для создания учетных данных клиента и скопируйте созданные учетные данные клиента.

![Клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap3.png)

4. Нажмите кнопку **Далее** и продолжить работу мастера.

![Клиент](media/Custom-Id-Tokens-in-AD-FS/clientsnap4.png)

### <a name="create-the-relying-party"></a>Создание проверяющей стороны
Чтобы добавить настраиваемые утверждения в код маркера, необходимо создать RP, которого утверждения будут добавлены в токене идентификатор. Используйте мастер добавления отношения доверия проверяющей стороны для создания нового проверяющей стороны, как показано ниже:
 
![Проверяющая сторона](media/Custom-Id-Tokens-in-AD-FS/rpsnap1.png)

После создания проверяющей стороны, щелкните правой кнопкой мыши щелкните запись проверяющей стороной и выберите **политику выдачи утверждений изменить** по добавлению правил выдачи утверждений. Добавьте необходимые настраиваемые утверждения для код маркера, как показано ниже:

![Проверяющая сторона](media/Custom-Id-Tokens-in-AD-FS/rpsnap2.png)

### <a name="assign-allatclaims-scope-to-the-pair-of-client-and-relying-party"></a>Назначьте область «allatclaims» пара клиента и проверяющей стороной
С помощью PowerShell на сервере AD FS назначить новой области allatclaims, как показано в примере ниже (изменение clientID и сервера:

``` powershell
Grant-AdfsApplicationPermission -ClientRoleIdentifier "5db77ce4-cedf-4319-85f7-cc230b7022e0" -ServerRoleIdentifier "https://customidrp1/" -ScopeNames "allatclaims","openid"
```

>[!NOTE]
>Измените ClientRoleIdentifier и ServerRoleIdentifier согласно параметры приложения

## <a name="test-the-custom-claims-in-id-token"></a>Проверка пользовательских утверждений в код маркера

Затем используя тот же самый бит кода, который использовался для доступа к утверждения всегда, вы увидите дополнительных утверждений, которые станут частью id_token.
Например, в приложении пример .NET MVC откройте один из файлов контроллера и введите код, например, ниже:


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
>Учтите, что параметр ресурса необходимо в запросе Oauth2.
>
>Неправильный пример.
>
>**HTTPS & #58; / / sts.contoso.com/adfs/oauth2/authorize?response_type=id_token&scope=openid&redirect_uri=https&#58;//myportal/auth&nonce=b3ceb943fc756d927777&client_id=6db3ec2a-075a-4c72-9b22-ca7ab60cb4e7&state=42c2c156aef47e8d0870&resource=6db3ec2a-075a-4c72-9b22-ca7ab60cb4e7**
>
>Хороший пример:
>
>**HTTPS & #58; / / sts.contoso.com/adfs/oauth2/authorize?response_type=id_token&scope=openid&redirect_uri=https&#58;//myportal/auth&nonce=b3ceb943fc756d927777&client_id=6db3ec2a-075a-4c72-9b22-ca7ab60cb4e7&state=42c2c156aef47e8d0870&resource=https&#58;//customidrp1/**
>
>Если параметр ресурса не запрос, что может появиться сообщение об ошибке или токена без любые настраиваемые утверждения.

## <a name="next-steps"></a>Дальнейшие действия
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  