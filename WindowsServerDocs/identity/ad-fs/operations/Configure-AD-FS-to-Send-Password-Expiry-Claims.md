---
ms.assetid: 03c82f43-ae2d-4038-b286-ae3858aed35a
title: Настройка AD FS для отправки утверждений об истечении срока действия пароля
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 29760dcc0dffe9fe29289f20f1abca4cfd8325b1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407693"
---
# <a name="configure-ad-fs-to-send-password-expiry-claims"></a>Настройка AD FS для отправки утверждений об истечении срока действия пароля


Можно настроить службы федерации Active Directory (AD FS) (AD FS) для отправки утверждений об истечении срока действия пароля в отношения доверия проверяющей стороны (приложения), защищенные ADFS. Использование этих утверждений зависит от приложения. Например, в качестве проверяющей стороны в Office 365 были реализованы обновления для Exchange и Outlook, позволяющие уведомлять федеративных пользователей о сроках их действия в скором времени.

Чтобы настроить AD FS для отправки утверждений об истечении срока действия пароля в отношение доверия с проверяющей стороной, необходимо добавить следующие правила утверждений в отношение доверия с проверяющей стороной:

```
@RuleName = "Issue Password Expiry Claims"
c1:[Type == "http://schemas.microsoft.com/ws/2012/01/passwordexpirationtime"]
 => issue(store = "_PasswordExpiryStore", types = ("http://schemas.microsoft.com/ws/2012/01/passwordexpirationtime", "http://schemas.microsoft.com/ws/2012/01/passwordexpirationdays", "http://schemas.microsoft.com/ws/2012/01/passwordchangeurl"), query = "{0};", param = c1.Value);
```

> [!NOTE]
> Утверждения об истечении срока действия пароля доступны только для типов проверки подлинности username и Password и Microsoft Passport for Work.  Если пользователь проходит аутентификацию с помощью встроенной проверки подлинности Windows и паспорт не настроен, утверждения не будут доступны и пользователи не увидят уведомления об истечении срока действия пароля.

> [!NOTE]
> Если срок действия пароля истекает через 14 дней, то в течение 14 дней будет заполнено поправку утверждений.

## <a name="see-also"></a>См. также
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)
