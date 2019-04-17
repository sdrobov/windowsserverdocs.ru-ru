---
ms.assetid: 1df78c2a-5054-4b54-8310-c48ea62e6e0b
title: "Пользовательские сообщения об ошибках для страницы входа AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 3a015c27f784d5b1f488f984450612820d4a06b1
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="custom-error-messages-for-ad-fs-sign-in-page"></a>Пользовательские сообщения об ошибках для страницы входа AD FS  

>Область применения: Windows Server 2016, Windows Server 2012 R2

Можно настроить пользовательские сообщения об ошибках специально для вашей организации. На следующем рисунке настроенное описание страницы ошибок и универсальное сообщение об ошибке. Используйте следующие командлеты Windows PowerShell для настройки сообщений об ошибках.  
  
![специальных ошибок](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom3.png)  
  
## <a name="customize-the-error-page-description"></a>Настройка описания страницы ошибок  
Чтобы настроить описание страницы ошибок, используйте следующий командлет Windows PowerShell и синтаксисом.  
  

`Set-AdfsGlobalWebContent -ErrorPageDescriptionText "This is Contoso's error page description" ` 

  
## <a name="customize-a-generic-error-message"></a>Настройка сообщения об ошибке  
Чтобы настроить универсальное сообщение об ошибке, используйте следующий командлет Windows PowerShell и синтаксисом.  
  
 
`Set-AdfsGlobalWebContent -ErrorPageGenericErrorMessage "This is a generic error message.  Contact Contoso IT for assistance." ` 

  
## <a name="customize-an-authorization-error-message"></a>Настройка сообщения об ошибке авторизации  
Чтобы настроить сообщение об ошибке авторизации, используйте следующий командлет Windows PowerShell и синтаксисом.  
  

    Set-AdfsGlobalWebContent -ErrorPageAuthorizationErrorMessage "You have received an Authorization error.  Contact Contoso IT for assistance."  

  
## <a name="customize-a-device-authentication-error-message"></a>Настройка сообщения об ошибке аутентификации устройства  
Чтобы настроить сообщение об ошибке аутентификации устройства, используйте следующий командлет Windows PowerShell и синтаксисом.  
  
 
`Set-AdfsGlobalWebContent -ErrorPageDeviceAuthenticationErrorMessage "Your device is not authorized.  Contact Contoso IT for assistance."`  
 
  
## <a name="customize-a-support-email-error-message"></a>Настроить сообщение об ошибке поддержки по электронной почте  
Можно настроить электронный адрес службы поддержки в AD FS. Если настройки Служб федерации Active Directory автоматически отображается ссылка конечные пользователи могут отправить подробные сведения об ошибке.  
  
Чтобы настроить сообщение об ошибке поддержки электронной почты, используйте следующий командлет Windows PowerShell и синтаксисом.  
  

    Set-AdfsGlobalWebContent -ErrorPageSupportEmail  "admin@contoso.com"  

  
## <a name="customize-a-relying-party-authorization-message"></a>Настройка сообщения авторизации проверяющей стороны  
Можно настроить сообщение об ошибке авторизации проверяющей стороны в AD FS.  
  
Чтобы настроить сообщение об ошибке проверяющей стороной, используйте следующий командлет Windows PowerShell и синтаксисом.  

    Set-AdfsRelyingPartyWebContent -Name fedpassive -ErrorPageAuthorizationErrorMessage "<p> You need to be a member of Security Auditors to access this site. Click <A href='http://accessrequest/'>here</A> for more information.</p>“  


## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)    
