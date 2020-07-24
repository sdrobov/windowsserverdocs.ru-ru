---
ms.assetid: 38bbc002-a8fa-4211-9328-4ef67fca0acf
title: Настройка для локализации
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 9a6bce383e04a892203c38cadc7ec2b7388b23a6
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965416"
---
# <a name="customization-for-localization"></a>Настройка для локализации 


Возможна локализация веб-содержимого на языки, отличные от английского. При локализации необходимо обращать внимание на следующие аспекты.  
  
После настройки содержимого вступают в силу пользовательские настройки. Следовательно, необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр, определяющий языковой стандарт. При настройке локализованного содержимого настройте его с использованием страны \- меньшего языкового стандарта, например "en", перед настройкой страны и региона, \- относящихся к региону, например "en \- US".  
  
Ниже показаны некоторые дополнительные примеры кода.  
  
    
    Set-AdfsWebTheme -TargetName default -Logo @{Locale="";Path="c:\contoso.png"}  
      
    Set-AdfsWebTheme -TargetName default -Illustration @{Locale="";Path="c:\illustration.png"}  

  
Ниже показаны некоторые дополнительные примеры кода.  
  
 
    Set-AdfsGlobalWebContent -ErrorPageDescriptionText "This is Contoso's error page description" –locale "en"  
  
  

    Set-AdfsGlobalWebContent -ErrorPageDescriptionText "Il s'agit de description de page erreur de Contoso" –locale "fr"  
 
  
Если вы хотите настроить веб-содержимое на языках, отличных от английского, для которых требуется ввод данных в Юникоде, рекомендуется использовать интегрированную среду сценариев Windows PowerShell. Дополнительные сведения см. [в статье Знакомство с интегрированной средой сценариев Windows PowerShell](/previous-versions/mt707506(v=msdn.10)).  

## <a name="additional-references"></a>Дополнительные ссылки 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md) 
