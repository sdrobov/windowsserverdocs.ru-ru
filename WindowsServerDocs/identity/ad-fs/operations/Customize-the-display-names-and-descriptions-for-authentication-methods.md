---
ms.assetid: 309d6358-777d-496a-856d-728246c7d9a1
title: Настройка отображаемых имен и описаний для методов проверки подлинности
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: cc0da10858ca6924a516fbf825206e376294209d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407565"
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
