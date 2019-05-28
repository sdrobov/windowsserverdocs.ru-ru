---
ms.assetid: 38bbc002-a8fa-4211-9328-4ef67fca0acf
title: Настройка локализации
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 3cf209756c27c72836c7e2e1e58e84f3f5af2ca9
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66189185"
---
# <a name="customization-for-localization"></a>Настройка локализации 


Возможна локализация веб-содержимого на языки, отличные от английского. При локализации необходимо обращать внимание на следующие аспекты.  
  
После настройки содержимого вступают в силу пользовательские настройки. Следовательно, необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр, определяющий языковой стандарт. При настройке локализованного содержимого необходимо его настроить со страной\-меньше языковой стандарт во-первых, например, «en», прежде чем настраивать страны и региона\-конкретного языкового стандарта, например «en\-США».  
  
Ниже показаны некоторые дополнительные примеры кода.  
  
    
    Set-AdfsWebTheme -TargetName default -Logo @{Locale="";Path="c:\contoso.png"}  
      
    Set-AdfsWebTheme -TargetName default -Illustration @{Locale="";Path="c:\illustration.png"}  

  
Ниже показаны некоторые дополнительные примеры кода.  
  
 
    Set-AdfsGlobalWebContent -ErrorPageDescriptionText "This is Contoso's error page description" –locale "en"  
  
  

    Set-AdfsGlobalWebContent -ErrorPageDescriptionText "Il s'agit de description de page erreur de Contoso" –locale "fr"  
 
  
Если вы хотите настроить веб-содержимое на языках, отличных от английского и требующих ввода символов стандарта Юникод, рекомендуется использовать интегрированную среду Сценариев Windows PowerShell. Дополнительные сведения см. в разделе [Знакомство с Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx).  

## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md) 
