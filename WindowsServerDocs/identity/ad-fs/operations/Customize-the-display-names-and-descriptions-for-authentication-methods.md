---
ms.assetid: 309d6358-777d-496a-856d-728246c7d9a1
title: Настройка отображаемых имен и описаний для методов проверки подлинности
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: b599d5b1d9d66758f70b7e5ab8cab8f53c475788
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87519743"
---
# <a name="customize-the-display-names-and-descriptions-for-authentication-methods"></a>Настройка отображаемых имен и описаний для методов проверки подлинности

Чтобы настроить отображаемые имена и описание методов проверки подлинности, можно использовать командлет `Set-AdfsAuthenticationProviderWebContent` PowerShell.  Чтобы использовать этот командлет, сначала необходимо получить имя метода проверки подлинности, который вы хотите настроить.  Это можно сделать с помощью `Get-AdfsGlobalAuthenticationPolicy`.  В приведенном ниже примере показано, что на странице входа \- отображается следующее: "войти с использованием сертификата X. 509".  Мы хотим упростить текст для пользователей.

![Настройка DisplayName](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update1.PNG)

Поэтому сначала мы получаем имя метода проверки подлинности, а затем изменяем отображаемый текст.

```powershell
Get-AdfsGlobalAuthenticationPolicy

AdditionalAuthenticationProvider  : {}
DeviceAuthenticationEnabled   : False
PrimaryIntranetAuthenticationProvider : {FormsAuthentication, CertificateAuthentication}
PrimaryExtranetAuthenticationProvider : {FormsAuthentication, CertificateAuthentication}
WindowsIntegratedFallbackEnabled  : True

Set-AdfsAuthenticationProviderWebContent -Name CertificateAuthentication -DisplayName "Sign in with a certificate"
 ```

![Настройка DisplayName](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update2.PNG)

Теперь мы видим, что сообщение изменилось.

![Настройка DisplayName](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update3.PNG)

## <a name="additional-references"></a>Дополнительные ссылки

[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)
