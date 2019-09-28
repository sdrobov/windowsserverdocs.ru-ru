---
ms.assetid: a4526500-24b3-423d-805c-24b0d8061aba
title: Изменение иллюстрации на странице входа AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 3da7726ca625c32728fb0ae64d291ae599b6cd8d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71358287"
---
# <a name="change-the-illustration-on-the-ad-fs-sign-in-page"></a>Изменение иллюстрации на странице входа AD FS

## <a name="change-the-illustration"></a>Изменение иллюстрации  


Чтобы изменить рисунок, рисунок слева, отображаемый на странице Sign @ no__t-0in, должен использовать следующий командлет и синтаксис Windows PowerShell.  

![изменить иллюстрацию](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  
> [!IMPORTANT]  
> Рекомендуемые размеры иллюстрации —1420 x 1080 пикселей @ 96 точек на дюйм. Размер файла не должен превышать 200 КБ.  
  
 
    Set-AdfsWebTheme -TargetName default -Illustration @{path="c:\Contoso\illustration.png"}  

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
  
  
