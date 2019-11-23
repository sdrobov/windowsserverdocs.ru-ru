---
ms.assetid: 330c7b61-dde0-432f-9b74-d250ad9cc808
title: Добавить знак\-в описании страницы
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 3b34a4e54aebd5b9dc3655eecd770a25f7ea97cf
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407749"
---
# <a name="add-sign-in-page-description"></a>Добавить знак\-в описании страницы


## <a name="to-add-sign-in-page-description"></a>Добавление\-знака в описание страницы  
Чтобы добавить знак\-в поле Описание страницы на страницу входа\-на странице, используйте следующий командлет и синтаксис Windows PowerShell.  

![добавить описание входа](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)

    Set-AdfsGlobalWebContent -SignInPageDescriptionText "<p>Sign-in to Contoso requires device registration. Click <A href='http://fs1.contoso.com/deviceregistration/'>here</A> for more information.</p>" 
 
  
> [!IMPORTANT]  
> Строка для параметра `SignInPageDescriptionText` поддерживает чистый HTML-код с тегами и без них. Таким образом, можно также выполнить следующий командлет, не используя тег &lt;p&gt;.  `Set-AdfsGlobalWebContent -SignInPageDescriptionText "Sign-in to Contoso requires device registration. Click <A href='http://fs1.contoso.com/deviceregistration/'>here</A> for more information." ` 

После настройки знака\-на странице Параметры настройки имеют приоритет. Поэтому следует настроить для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр, определяющий языковой стандарт. При настройке локализованного содержимого его необходимо настроить с использованием страны\-меньше языкового стандарта, например en, перед настройкой страны и региона\-определенного языкового стандарта, например en\-US.  

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
