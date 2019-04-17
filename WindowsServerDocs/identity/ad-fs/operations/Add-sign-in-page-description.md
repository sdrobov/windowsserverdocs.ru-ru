---
ms.assetid: 330c7b61-dde0-432f-9b74-d250ad9cc808
title: "Добавление описания страницы входа"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 128a4ffd8d4b9dfcfe5f0e8e2df8a0e1505cbb24
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="add-sign-in-page-description"></a>Добавление описания страницы входа

>Область применения: Windows Server 2016, Windows Server 2012 R2

## <a name="to-add-sign-in-page-description"></a>Чтобы добавить описание страницы входа  
Чтобы добавить описание страницы входа на страницу входа в систему, используйте следующий командлет Windows PowerShell PowerShell и синтаксисом.  

![Добавьте в описании журнала](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)

    Set-AdfsGlobalWebContent -SignInPageDescriptionText "<p>Sign-in to Contoso requires device registration. Click <A href='http://fs1.contoso.com/deviceregistration/'>here</A> for more information.</p>" 
 
  
> [!IMPORTANT]  
> Строка для `SignInPageDescriptionText`поддерживает оба чистый HTML-код с тегами и без. Таким образом, можно выполнить следующий командлет без использования &lt;p&gt; тег.  `Set-AdfsGlobalWebContent -SignInPageDescriptionText "Sign-in to Contoso requires device registration. Click <A href='http://fs1.contoso.com/deviceregistration/'>here</A> for more information." ` 

После настройки страницы входа вступают в силу настройки; Таким образом необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр языкового стандарта. При настройке локализованного содержимого, он должны быть настроены country\ языкового во-первых, например, «en», прежде чем настраивать страны и языковой стандарт region\ таких как «en\-us».  

## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)  
