---
ms.assetid: f7f6bac2-1100-4b00-a248-4ca3eb3cdbe9
title: "Изменение логотипа компании на страницу входа AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 03/08/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: ca54abe7fe852b22f2f4d9a717e38d219fa50694
ms.sourcegitcommit: a00fc4426dc4ad0098257f01f0124d6c733d1aef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2018
---
# <a name="changing-the-company-logo-on-the-ad-fs-sign-in-page"></a>Изменение логотипа компании на страницу входа AD FS

>Область применения: Windows Server 2016, Windows Server 2012 R2

#### <a name="change-company-logo"></a>Изменение логотипа компании  
Чтобы изменить логотип компании, которая отображается на странице входа, используйте следующий командлет PowerShell Windows PowerShell и синтаксисом.  

![Изменение эмблемы](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  
> [!IMPORTANT]  
> Мы рекомендуем размеры логотипа — 260 x 350 @ 96 точек на дюйм размер файла не должен превышать 10 КБ.  
  
    
    Set-AdfsWebTheme -TargetName default -Logo @{path="c:\Contoso\logo.png"}  

  
> [!NOTE]  
> `TargetName`Параметр является обязательным. Тема по умолчанию, который входит в состав Служб федерации Active Directory называется *по умолчанию*.  

## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)  
