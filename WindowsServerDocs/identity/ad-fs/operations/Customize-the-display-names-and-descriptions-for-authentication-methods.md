---
ms.assetid: 309d6358-777d-496a-856d-728246c7d9a1
title: Настроить отображаемые имена и описания методов проверки подлинности
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: b9702873d42e0a72e510ac022d8d7fb04b45dab9
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66189168"
---
# <a name="customize-the-display-names-and-descriptions-for-authentication-methods"></a>Настроить отображаемые имена и описания методов проверки подлинности 


Чтобы настроить отображаемые имена и описание методов проверки подлинности, можно использовать командлет `Set-AdfsAuthenticationProviderWebContent` PowerShell.  Чтобы использовать этот командлет, сначала необходимо получить имя метода проверки подлинности, который вы хотите настроить.  Это можно сделать с помощью `Get-AdfsGlobalAuthenticationPolicy`.  В следующем примере мы видим, что, в нашем входа\-на странице отображается следующая информация:  "Войдите с использованием сертификата X.509".  Мы хотим упростить текст для пользователей.  
  
![Настройка displayname](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update1.PNG)  
  
Поэтому сначала мы получаем имя метода проверки подлинности, а затем изменяем отображаемый текст.  
  
 
    Get-AdfsGlobalAuthenticationPolicy  
      
    AdditionalAuthenticationProvider  : {}  
    DeviceAuthenticationEnabled   : False  
    PrimaryIntranetAuthenticationProvider : {FormsAuthentication, CertificateAuthentication}  
    PrimaryExtranetAuthenticationProvider : {FormsAuthentication, CertificateAuthentication}  
    WindowsIntegratedFallbackEnabled  : True  
      
    Set-AdfsAuthenticationProviderWebContent -Name CertificateAuthentication -DisplayName "Sign in with a certificate"  
  
  
![Настройка displayname](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update2.PNG)  
  
Теперь мы видим, что сообщение изменилось.  
  
![Настройка displayname](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update3.PNG)  

## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md) 
