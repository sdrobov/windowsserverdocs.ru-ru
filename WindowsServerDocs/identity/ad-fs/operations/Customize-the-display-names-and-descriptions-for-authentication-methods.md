---
ms.assetid: 309d6358-777d-496a-856d-728246c7d9a1
title: "Настроить отображаемые имена и описания методов проверки подлинности"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 699622a8a075dd6c78ab1b536dce2abfee642e9e
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="customize-the-display-names-and-descriptions-for-authentication-methods"></a>Настроить отображаемые имена и описания методов проверки подлинности 

>Область применения: Windows Server 2016, Windows Server 2012 R2

Чтобы настроить отображаемые имена и описания методов проверки подлинности можно использовать `Set-AdfsAuthenticationProviderWebContent`командлет PowerShell.  Чтобы использовать этот командлет, сначала необходимо получить имя метода проверки подлинности, который вы хотите настроить.  Это можно сделать с помощью `Get-AdfsGlobalAuthenticationPolicy`.  В приведенном ниже примере мы видим, что на странице входа в систему отображается следующая: «вход с использованием сертификата X.509».  Мы хотим упростить текст для пользователей.  
  
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

## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md) 
