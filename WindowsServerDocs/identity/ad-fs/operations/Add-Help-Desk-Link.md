---
ms.assetid: 2bac7744-9de3-491a-b0a2-4e843cec7344
title: "Добавление ссылки на службу технической поддержки"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 6d16cc0a75bfe636c29b44687b669e87f31b69ce
ms.sourcegitcommit: 76e57a5453d6ee9a04dcff6a8cca087132cb1d5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2018
---
# <a name="add-help-desk-link"></a>Добавление ссылки на службу технической поддержки 

>Область применения: Windows Server 2016, Windows Server 2012 R2


## <a name="to-add-a-help-desk-link"></a>Для добавления ссылки на службу технической поддержки  
Для добавления ссылки поддержки справки, которая отображается на странице входа, используйте следующий командлет Windows PowerShell PowerShell и синтаксисом.  

![Добавление поддержки](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  

`Set-AdfsGlobalWebContent -HelpDeskLink https://fs1.contoso.com/help/ -HelpDeskLinkText Help`  
 
  
> [!IMPORTANT]  
> `linkText`В этом командлете не требуется, если не используется другой значения по умолчанию, который является *помочь*. Преимущество использования значения по умолчанию — что локализация на все языковые стандарты клиента. После настройки страницы вступают в силу настройки; Таким образом необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать.  


## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)  
