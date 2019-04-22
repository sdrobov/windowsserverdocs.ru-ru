---
ms.assetid: f7f6bac2-1100-4b00-a248-4ca3eb3cdbe9
title: Изменение эмблемы компании на страницы входа AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 03/08/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 6e0271ae3d7ac120e510a2fb81fb55c8d10b3c87
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813585"
---
# <a name="changing-the-company-logo-on-the-ad-fs-sign-in-page"></a>Изменение эмблемы компании на страницы входа AD FS

>Область применения. Windows Server 2016, Windows Server 2012 R2

#### <a name="change-company-logo"></a>Изменение логотипа компании  
Чтобы изменить логотип компании, которая отображается на странице входа\-на странице, используйте следующий командлет PowerShell Windows PowerShell и синтаксис.  

![изменить логотип](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  
> [!IMPORTANT]  
> Рекомендуемые размеры логотипа — 260 x 35 @ 96 точек на дюйм. Размер файла не должен превышать 10 КБ.  
  
    
    Set-AdfsWebTheme -TargetName default -Logo @{path="c:\Contoso\logo.png"}  

  
> [!NOTE]  
> Параметр `TargetName` обязательный. Тема по умолчанию, предоставляемая в AD FS называется *по умолчанию*.  

## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)  
