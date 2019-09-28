---
ms.assetid: f7f6bac2-1100-4b00-a248-4ca3eb3cdbe9
title: Изменение логотипа компании на странице входа AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 03/08/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: b22c969e0113081e1ca8a662ae81a2ee24829835
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71358303"
---
# <a name="changing-the-company-logo-on-the-ad-fs-sign-in-page"></a>Изменение логотипа компании на странице входа AD FS

#### <a name="change-company-logo"></a>Изменение логотипа компании  
Чтобы изменить эмблему компании, которая отображается на странице Sign @ no__t-0in, используйте следующий командлет PowerShell Windows PowerShell и синтаксис.  

![изменить логотип](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  
> [!IMPORTANT]  
> Рекомендуемые размеры логотипа — 260 x 35 @ 96 точек на дюйм. Размер файла не должен превышать 10 КБ.  
  
    
    Set-AdfsWebTheme -TargetName default -Logo @{path="c:\Contoso\logo.png"}  

  
> [!NOTE]  
> Параметр `TargetName` обязательный. Тема по умолчанию, которая выпускается с AD FS, называется *Default*.  

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
