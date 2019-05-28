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
ms.openlocfilehash: fe5c138466ea288b5dfb8c7c284603150ab9d874
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66190028"
---
# <a name="changing-the-company-logo-on-the-ad-fs-sign-in-page"></a>Изменение эмблемы компании на страницы входа AD FS

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
