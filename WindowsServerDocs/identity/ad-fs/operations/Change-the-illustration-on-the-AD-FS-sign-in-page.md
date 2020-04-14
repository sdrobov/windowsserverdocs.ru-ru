---
ms.assetid: a4526500-24b3-423d-805c-24b0d8061aba
title: Изменение иллюстрации на странице входа AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: de0fc7af4c4eecad59b7af6b08426ef207da5db1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859957"
---
# <a name="change-the-illustration-on-the-ad-fs-sign-in-page"></a>Изменение иллюстрации на странице входа AD FS

## <a name="change-the-illustration"></a>Изменение иллюстрации  


Чтобы изменить иллюстрацию, рисунок слева, отображаемый на странице Sign\-to, используйте следующий командлет и синтаксис Windows PowerShell.  

![изменить иллюстрацию](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  
> [!IMPORTANT]  
> Рекомендуемые размеры иллюстрации —1420 x 1080 пикселей @ 96 точек на дюйм. Размер файла не должен превышать 200 КБ.  
  
 
    Set-AdfsWebTheme -TargetName default -Illustration @{path="c:\Contoso\illustration.png"}  

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
  
  
