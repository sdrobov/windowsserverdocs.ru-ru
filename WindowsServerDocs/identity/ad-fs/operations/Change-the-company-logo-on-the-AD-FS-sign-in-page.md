---
ms.assetid: f7f6bac2-1100-4b00-a248-4ca3eb3cdbe9
title: Изменение логотипа компании на странице входа AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 03/08/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: d12429b22265495cb8168ce3e5993a5cf3e74a0c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859977"
---
# <a name="changing-the-company-logo-on-the-ad-fs-sign-in-page"></a>Изменение логотипа компании на странице входа AD FS

#### <a name="change-company-logo"></a>Изменение логотипа компании  
Чтобы изменить эмблему компании, которая отображается на странице входа\-на страницу, используйте следующий командлет PowerShell Windows PowerShell и синтаксис.  

![изменить логотип](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  
> [!IMPORTANT]  
> Рекомендуемые размеры логотипа — 260 x 35 @ 96 точек на дюйм. Размер файла не должен превышать 10 КБ.  
  
    
    Set-AdfsWebTheme -TargetName default -Logo @{path="c:\Contoso\logo.png"}  

  
> [!NOTE]  
> Параметр `TargetName` обязательный. Тема по умолчанию, которая выпускается с AD FS, называется *Default*.  

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
