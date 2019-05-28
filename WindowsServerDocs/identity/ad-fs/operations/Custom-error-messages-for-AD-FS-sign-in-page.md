---
ms.assetid: 1df78c2a-5054-4b54-8310-c48ea62e6e0b
title: Пользовательские сообщения об ошибках для страницы входа AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 8bcc653cc9eb9adb6d31331463d01774d4faec1a
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66189216"
---
# <a name="custom-error-messages-for-ad-fs-sign-in-page"></a>Пользовательские сообщения об ошибках для страницы входа AD FS  


Можно настроить пользовательские сообщения об ошибках специально для вашей организации. На следующей иллюстрации показаны настроенное описание страницы ошибок и универсальное сообщение об ошибке. Используйте следующие командлеты Windows PowerShell для настройки сообщений об ошибках.  
  
![настраиваемая ошибка](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom3.png)  
  
## <a name="customize-the-error-page-description"></a>Настройка описания страницы ошибок  
Чтобы настроить описание страницы ошибок, используйте следующий командлет Windows PowerShell и синтаксис.  
  

`Set-AdfsGlobalWebContent -ErrorPageDescriptionText "This is Contoso's error page description" ` 

  
## <a name="customize-a-generic-error-message"></a>Настройка универсального сообщения об ошибке  
Чтобы настроить универсальное сообщение об ошибке, используйте следующий командлет Windows PowerShell и синтаксисом.  
  
 
`Set-AdfsGlobalWebContent -ErrorPageGenericErrorMessage "This is a generic error message.  Contact Contoso IT for assistance." ` 

  
## <a name="customize-an-authorization-error-message"></a>Настройка сообщения об ошибке авторизации  
Чтобы настроить сообщение об ошибке авторизации, используйте следующий командлет Windows PowerShell и синтаксисом.  
  

    Set-AdfsGlobalWebContent -ErrorPageAuthorizationErrorMessage "You have received an Authorization error.  Contact Contoso IT for assistance."  

  
## <a name="customize-a-device-authentication-error-message"></a>Настройка сообщения об ошибке аутентификации устройства  
Чтобы настроить сообщение об ошибке аутентификации устройства, используйте следующий командлет Windows PowerShell и синтаксисом.  
  
 
`Set-AdfsGlobalWebContent -ErrorPageDeviceAuthenticationErrorMessage "Your device is not authorized.  Contact Contoso IT for assistance."`  
 
  
## <a name="customize-a-support-email-error-message"></a>Настройка сообщения об ошибке с указанием электронного адреса службы поддержки  
Адрес электронной почты службы поддержки можно настроить в AD FS. Если настройки AD FS автоматически отображается ссылка для конечных пользователей к электронной почте, сведения об ошибке.  
  
Чтобы настроить сообщение об ошибке поддержки по электронной почте, используйте следующий командлет Windows PowerShell и синтаксисом.  
  

    Set-AdfsGlobalWebContent -ErrorPageSupportEmail  "admin@contoso.com"  

  
## <a name="customize-a-relying-party-authorization-message"></a>Настройка сообщения авторизации проверяющей стороны  
Можно настроить сообщение об ошибке авторизации проверяющей стороной в AD FS.  
  
Чтобы настроить доверяющей стороной сообщение об ошибке, используйте следующий командлет Windows PowerShell и синтаксисом.  

    Set-AdfsRelyingPartyWebContent -Name fedpassive -ErrorPageAuthorizationErrorMessage "<p> You need to be a member of Security Auditors to access this site. Click <A href='http://accessrequest/'>here</A> for more information.</p>“  


## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)    
