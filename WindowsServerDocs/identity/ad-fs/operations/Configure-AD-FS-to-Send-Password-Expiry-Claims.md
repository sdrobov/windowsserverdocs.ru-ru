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
ms.openlocfilehash: 3be14b824038e9424b86c40bfd657dd988fa99e9
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66189871"
---
# <a name="configure-ad-fs-to-send-password-expiry-claims"></a>Настройка AD FS для отправки утверждений об истечении срока действия пароля


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
