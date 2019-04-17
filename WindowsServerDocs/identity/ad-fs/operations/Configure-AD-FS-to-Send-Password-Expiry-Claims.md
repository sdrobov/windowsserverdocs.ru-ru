---
ms.assetid: 03c82f43-ae2d-4038-b286-ae3858aed35a
title: "Настройка AD FS для отправки утверждений об истечении срока действия пароля"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 386a5ac921ba609c371121b8657351667628951b
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="configure-ad-fs-to-send-password-expiry-claims"></a>Настройка AD FS для отправки утверждений об истечении срока действия пароля

>Область применения: Windows Server 2016, Windows Server 2012 R2

Можно настроить федерации служб Active Directory (AD FS) для отправки утверждений об истечении срока действия пароля доверия с проверяющей стороной (приложения), защищенным с помощью служб федерации Active Directory. Как используются эти утверждения зависит от приложения. Например с Office 365 как проверяющей стороной, обновления были реализованы в Exchange и Outlook, чтобы уведомить федеративных пользователей скоро к--срок действия паролей.

Чтобы настроить AD FS для отправки пароля утверждений об истечении срока действия для доверия с проверяющей стороной, необходимо добавить следующие правила утверждений для этого отношения доверия с проверяющей стороной:

```
c1:[Type == "https://schemas.microsoft.com/ws/2012/01/passwordexpirationtime"]
=> issue(store = "_PasswordExpiryStore", types = ("https://schemas.microsoft.com/ws/2012/01/passwordexpirationtime", "https://schemas.microsoft.com/ws/2012/01/passwordexpirationdays", "https://schemas.microsoft.com/ws/2012/01/passwordchangeurl"), query = "{0};", param = c1.Value);
```

> [!NOTE]
> Утверждений об истечении срока действия пароля доступны только для имени пользователя и пароль для Microsoft Passport для работы типов проверки подлинности.  Если пользователь проходит проверку подлинности с помощью встроенной проверки подлинности Windows и Passport не настроен, утверждения будут недоступны и пользователи не будут видеть уведомления об истечении срока действия пароля.

> [!NOTE]
> Нет окно 14 дней, поэтому отправленных утверждений будет заполнен, только если истекает срок действия пароля в течение 14 дней.

## <a name="see-also"></a>См. также:
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)
