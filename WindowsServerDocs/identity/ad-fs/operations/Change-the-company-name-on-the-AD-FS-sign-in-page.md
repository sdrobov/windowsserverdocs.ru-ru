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
ms.openlocfilehash: f32abbfbc74ad81dfeab5aed403178be4a9b0a57
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86953746"
---
# <a name="change-the-company-name-on-the-ad-fs-sign-in-page"></a>Изменение названия компании на странице входа AD FS
 
Чтобы изменить имя компании, отображаемое на \- странице входа, используйте следующий командлет и синтаксис Windows PowerShell. Это значение настраивается по умолчанию с помощью значения из отображаемого имени службы федерации, вводимого во время настройки.  

![изменить имя](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1.png)
  
  
    Set-AdfsGlobalWebContent –CompanyName "Contoso Corp"  
 
  
> [!NOTE]  
> Можно также использовать интегрированную среду сценариев Windows PowerShell \( \) для изменения названия компании. С помощью интегрированной среды сценариев Windows PowerShell можно отображать содержимое в среде, \- совместимой с Юникодом. Дополнительные сведения см. в разделе [Знакомство с Windows PowerShell ISE](/previous-versions/mt707506(v=msdn.10)).  

## <a name="additional-references"></a>Дополнительные ссылки 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
  
