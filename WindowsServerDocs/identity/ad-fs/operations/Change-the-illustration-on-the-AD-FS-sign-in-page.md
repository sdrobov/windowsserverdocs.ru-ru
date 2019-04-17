---
ms.assetid: a4526500-24b3-423d-805c-24b0d8061aba
title: "Изменение иллюстрации на страницу входа AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: ac5e60aaad864248b58a3908e7aa9622165fbc14
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="change-the-illustration-on-the-ad-fs-sign-in-page"></a>Изменение иллюстрации на страницу входа AD FS

>Область применения: Windows Server 2016, Windows Server 2012 R2

## <a name="change-the-illustration"></a>Изменение иллюстрации  


Чтобы изменить иллюстрацию, то изображение в левой части будет отображаться на странице входа, используйте следующий командлет Windows PowerShell PowerShell и синтаксисом.  

![Изменение иллюстрации](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  
> [!IMPORTANT]  
> Рекомендуемые размеры иллюстрации — 1420 x 1080 пикселей @ 96 точек на ДЮЙМ, размер файла не должен превышать 200 КБ.  
  
 
    Set-AdfsWebTheme -TargetName default -Illustration @{path="c:\Contoso\illustration.png"}  

## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)  
  
  
