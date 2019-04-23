---
ms.assetid: a4526500-24b3-423d-805c-24b0d8061aba
title: Изменение иллюстрации, на странице входа AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 4f1cba9862766092c2beadb894cbac092d146887
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858245"
---
# <a name="change-the-illustration-on-the-ad-fs-sign-in-page"></a>Изменение иллюстрации, на странице входа AD FS

>Область применения. Windows Server 2016, Windows Server 2012 R2

## <a name="change-the-illustration"></a>Изменение иллюстрации  


Чтобы изменить иллюстрацию, то изображение в левой части которой отображается на странице входа\-на странице, используйте следующий командлет Windows PowerShell и синтаксис.  

![Изменение иллюстрации](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  
> [!IMPORTANT]  
> Рекомендуемые размеры иллюстрации —1420 x 1080 пикселей @ 96 точек на дюйм. Размер файла не должен превышать 200 КБ.  
  
 
    Set-AdfsWebTheme -TargetName default -Illustration @{path="c:\Contoso\illustration.png"}  

## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)  
  
  
