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
ms.openlocfilehash: 218643bbd5ada63b6bee2b91a7bace3f9959c0bd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80816447"
---
# <a name="customize-the-display-names-and-descriptions-for-authentication-methods"></a>Настройка отображаемых имен и описаний для методов проверки подлинности 


Чтобы настроить отображаемые имена и описание методов проверки подлинности, можно использовать командлет `Set-AdfsAuthenticationProviderWebContent` PowerShell.  Чтобы использовать этот командлет, сначала необходимо получить имя метода проверки подлинности, который вы хотите настроить.  Это можно сделать с помощью `Get-AdfsGlobalAuthenticationPolicy`.  В приведенном ниже примере отображается следующее: "вход с помощью сертификата X. 509" на странице "вход\-".  Мы хотим упростить текст для пользователей.  
  
![Настройка DisplayName](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update1.PNG)  
  
Поэтому сначала мы получаем имя метода проверки подлинности, а затем изменяем отображаемый текст.  
  
 
    Get-AdfsGlobalAuthenticationPolicy  
      
    AdditionalAuthenticationProvider  : {}  
    DeviceAuthenticationEnabled   : False  
    PrimaryIntranetAuthenticationProvider : {FormsAuthentication, CertificateAuthentication}  
    PrimaryExtranetAuthenticationProvider : {FormsAuthentication, CertificateAuthentication}  
    WindowsIntegratedFallbackEnabled  : True  
      
    Set-AdfsAuthenticationProviderWebContent -Name CertificateAuthentication -DisplayName "Sign in with a certificate"  
  
  
![Настройка DisplayName](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update2.PNG)  
  
Теперь мы видим, что сообщение изменилось.  
  
![Настройка DisplayName](media/AD-FS-user-sign-in-customization/ADFS_Customize_Update3.PNG)  

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md) 
