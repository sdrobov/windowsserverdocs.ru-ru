---
ms.assetid: 28043fc4-a34d-4710-ac3b-5c9d4d6a895c
title: "Изменения названия компании, на странице входа в AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 8e99f6fed8922ed15bf78a98b207b6f46767763a
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="change-the-company-name-on-the-ad-fs-sign-in-page"></a>Изменения названия компании, на странице входа в AD FS

>Область применения: Windows Server 2016, Windows Server 2012 R2
 
Чтобы изменить название компании, которая отображается на странице входа, используйте следующий командлет Windows PowerShell PowerShell и синтаксисом. Это значение, по умолчанию с помощью значения из отображаемого имени службы федерации, которое вы указали во время установки.  

![Изменение имени](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1.png)
  
  
    Set-AdfsGlobalWebContent –CompanyName "Contoso Corp"  
 
  
> [!NOTE]  
> Можно также использовать \(ISE\) Windows интегрированной среды сценариев PowerShell для изменения названия компании. С помощью интегрированной среды Сценариев Windows PowerShell, можно отображать содержимое в среде с Юникодом. Дополнительные сведения см. в разделе [Знакомство с Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx).  

## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)  
  
