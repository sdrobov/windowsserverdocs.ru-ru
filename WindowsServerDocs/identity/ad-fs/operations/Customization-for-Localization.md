---
ms.assetid: 38bbc002-a8fa-4211-9328-4ef67fca0acf
title: "Настройки для локализации"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: ac206d5aa8af970b65a014955ac66a8cf2835eb6
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="customization-for-localization"></a>Настройки для локализации 

>Область применения: Windows Server 2016, Windows Server 2012 R2

Возможна локализация веб-содержимое на языках, отличных от английского. При локализации необходимо обращать внимание на следующие аспекты.  
  
После настройки содержимого вступают в силу настройки; Таким образом необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр языкового стандарта. При настройке локализованного содержимого его в языковом стандарте country\ менее во-первых, например, «en», прежде чем настраивать настроить страны и языковой стандарт region\ такие как «en\-us».  
  
Ниже показаны некоторые дополнительные примеры кода.  
  
    
    Set-AdfsWebTheme -TargetName default -Logo @{Locale="";Path="c:\contoso.png"}  
      
    Set-AdfsWebTheme -TargetName default -Illustration @{Locale="";Path="c:\illustration.png"}  

  
Ниже показаны некоторые дополнительные примеры кода.  
  
 
    Set-AdfsGlobalWebContent -ErrorPageDescriptionText "This is Contoso's error page description" –locale "en"  
  
  

    Set-AdfsGlobalWebContent -ErrorPageDescriptionText "Il s'agit de description de page erreur de Contoso" –locale "fr"  
 
  
Если вы хотите настроить веб-содержимое на языках, отличных от английского и требующих ввода символов стандарта Юникод, рекомендуется использовать интегрированной среды Сценариев Windows PowerShell. Дополнительные сведения см. [Знакомство с Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx).  

## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md) 
