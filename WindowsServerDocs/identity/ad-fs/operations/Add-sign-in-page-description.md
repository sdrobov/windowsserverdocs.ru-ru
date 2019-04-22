---
ms.assetid: 330c7b61-dde0-432f-9b74-d250ad9cc808
title: Добавление функций\-в описание страницы
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 553cdcf2ac98b23d06cc43a64220cf8433117fc8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814015"
---
# <a name="add-sign-in-page-description"></a>Добавление функций\-в описание страницы

>Область применения. Windows Server 2016, Windows Server 2012 R2

## <a name="to-add-sign-in-page-description"></a>Чтобы добавить знак\-в описание страницы  
Чтобы добавить знак\-в описание страницы входа\-на странице, используйте следующий командлет Windows PowerShell и синтаксис.  

![Добавление функций в описании](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)

    Set-AdfsGlobalWebContent -SignInPageDescriptionText "<p>Sign-in to Contoso requires device registration. Click <A href='http://fs1.contoso.com/deviceregistration/'>here</A> for more information.</p>" 
 
  
> [!IMPORTANT]  
> Строка для параметра `SignInPageDescriptionText` поддерживает чистый HTML-код с тегами и без них. Следовательно, для выполнения следующего командлета без использования &lt;p&gt; тега.  `Set-AdfsGlobalWebContent -SignInPageDescriptionText "Sign-in to Contoso requires device registration. Click <A href='http://fs1.contoso.com/deviceregistration/'>here</A> for more information." ` 

После знака\-странице имеет силу пользовательские настройки имеет более высокий приоритет; таким образом, необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр, определяющий языковой стандарт. При настройке локализованного содержимого должен быть настроен со страной\-меньше языковой стандарт во-первых, например, «en», прежде чем настраивать страны и региона\-конкретного языкового стандарта, например «en\-США».  

## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)  
