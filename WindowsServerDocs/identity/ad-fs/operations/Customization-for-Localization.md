---
ms.assetid: 38bbc002-a8fa-4211-9328-4ef67fca0acf
title: Настройка для локализации
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: ba3441d362960e054791ca3d6872dba6c7bd9a12
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71357978"
---
# <a name="customization-for-localization"></a>Настройка для локализации 


Возможна локализация веб-содержимого на языки, отличные от английского. При локализации необходимо обращать внимание на следующие аспекты.  
  
После настройки содержимого вступают в силу пользовательские настройки. Следовательно, необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр, определяющий языковой стандарт. При настройке локализованного содержимого сначала настройте его с помощью языкового стандарта Country @ no__t-0less, например en, перед настройкой страны и региона @ no__t-1specific locale, например "EN @ no__t-2US".  
  
Ниже показаны некоторые дополнительные примеры кода.  
  
    
    Set-AdfsWebTheme -TargetName default -Logo @{Locale="";Path="c:\contoso.png"}  
      
    Set-AdfsWebTheme -TargetName default -Illustration @{Locale="";Path="c:\illustration.png"}  

  
Ниже показаны некоторые дополнительные примеры кода.  
  
 
    Set-AdfsGlobalWebContent -ErrorPageDescriptionText "This is Contoso's error page description" –locale "en"  
  
  

    Set-AdfsGlobalWebContent -ErrorPageDescriptionText "Il s'agit de description de page erreur de Contoso" –locale "fr"  
 
  
Если вы хотите настроить веб-содержимое на языках, отличных от английского, для которых требуется ввод данных в Юникоде, рекомендуется использовать интегрированную среду сценариев Windows PowerShell. Дополнительные сведения см. в разделе [Знакомство с Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx).  

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md) 
