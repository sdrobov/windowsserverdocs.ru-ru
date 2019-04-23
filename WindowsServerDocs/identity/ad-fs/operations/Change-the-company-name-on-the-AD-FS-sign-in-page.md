---
ms.assetid: 28043fc4-a34d-4710-ac3b-5c9d4d6a895c
title: Изменения названия компании на странице входа AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 1711e7d7de871c9ae9b1b7ea7b21f6e75ae15220
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868475"
---
# <a name="change-the-company-name-on-the-ad-fs-sign-in-page"></a>Изменения названия компании на странице входа AD FS

>Область применения. Windows Server 2016, Windows Server 2012 R2
 
Чтобы изменить название компании, которое отображается на странице входа\-на странице, используйте следующий командлет Windows PowerShell и синтаксис. Это значение настраивается по умолчанию с помощью значения из отображаемого имени службы федерации, вводимого во время настройки.  

![Изменение имени](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1.png)
  
  
    Set-AdfsGlobalWebContent –CompanyName "Contoso Corp"  
 
  
> [!NOTE]  
> Можно также использовать Windows PowerShell интегрированная среда сценариев \(интегрированной среды Сценариев\) для изменения названия компании. С помощью интегрированной среды Сценариев Windows PowerShell, можно отображать содержимое в формате Юникод\-требованиям среды. Дополнительные сведения см. в разделе [Знакомство с Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx).  

## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)  
  
