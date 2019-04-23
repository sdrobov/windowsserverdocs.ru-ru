---
ms.assetid: 03c82f43-ae2d-4038-b286-ae3858aed35a
title: Настройка AD FS для отправки утверждений об истечении срока действия пароля
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 080e8cc81949df3bf74ae846eee7f32c5e145f53
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59834365"
---
# <a name="configure-ad-fs-to-send-password-expiry-claims"></a>Настройка AD FS для отправки утверждений об истечении срока действия пароля

>Область применения. Windows Server 2016, Windows Server 2012 R2

Можно настроить федерации служб Active Directory (AD FS) для отправки утверждений истечения срока действия пароля для отношений доверия проверяющих сторон (приложения), которые защищены с помощью служб федерации Active Directory. Как используются эти утверждения зависит от приложения. Например Office 365 как проверяющей обновления были реализованы к Exchange и Outlook, сообщите об этом федеративной пользователям их паролей скоро к--, истек срок действия.

Для настройки AD FS для отправки пароля срок действия утверждения для доверия с проверяющей стороной, необходимо добавить следующие правила утверждения для отношений доверия этой проверяющей стороны:

```
@RuleName = "Issue Password Expiry Claims"
c1:[Type == "http://schemas.microsoft.com/ws/2012/01/passwordexpirationtime"]
 => issue(store = "_PasswordExpiryStore", types = ("http://schemas.microsoft.com/ws/2012/01/passwordexpirationtime", "http://schemas.microsoft.com/ws/2012/01/passwordexpirationdays", "http://schemas.microsoft.com/ws/2012/01/passwordchangeurl"), query = "{0};", param = c1.Value);
```

> [!NOTE]
> Утверждения истечения срока действия пароля доступны только для имени пользователя и пароля, а также Microsoft Passport для рабочих типов проверки подлинности.  Если пользователь проходит проверку подлинности с помощью встроенной проверки подлинности Windows и Passport не настроен, утверждения будут недоступны и пользователи не будут видеть уведомления о истечения срока действия пароля.

> [!NOTE]
> Нет окна 14 дней, поэтому отправленные утверждения будет заполнен, только если истекает срок действия пароля в течение 14 дней.

## <a name="see-also"></a>См. также
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)
