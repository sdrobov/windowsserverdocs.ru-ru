---
ms.assetid: 28043fc4-a34d-4710-ac3b-5c9d4d6a895c
title: Изменение названия компании на странице входа AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 378979825c0e8e505c3996cf8cbcdb471a0c7d79
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859967"
---
# <a name="change-the-company-name-on-the-ad-fs-sign-in-page"></a>Изменение названия компании на странице входа AD FS
 
Чтобы изменить имя компании, которая отображается на странице\-входа, используйте следующий командлет и синтаксис Windows PowerShell. Это значение настраивается по умолчанию с помощью значения из отображаемого имени службы федерации, вводимого во время настройки.  

![изменить имя](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1.png)
  
  
    Set-AdfsGlobalWebContent –CompanyName "Contoso Corp"  
 
  
> [!NOTE]  
> Можно также использовать интегрированную среду сценариев Windows PowerShell \(ISE\), чтобы изменить название компании. С помощью интегрированной среды сценариев Windows PowerShell можно отображать содержимое в совместимой с Юникод\-среде. Дополнительные сведения см. в разделе [Знакомство с Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx).  

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
  
