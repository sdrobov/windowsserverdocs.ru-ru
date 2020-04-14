---
ms.assetid: 2bac7744-9de3-491a-b0a2-4e843cec7344
title: Добавление ссылки на службу технической поддержки
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 0aa57147ed2565db9cf8cde0addeb13432cb8856
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859407"
---
# <a name="add-help-desk-link"></a>Добавление ссылки на службу технической поддержки 


## <a name="to-add-a-help-desk-link"></a>Добавление ссылки службы поддержки  
Чтобы добавить ссылку службы поддержки, которая отображается на странице входа\-на страницу, используйте следующий командлет и синтаксис Windows PowerShell.  

![Добавить службу поддержки](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  

`Set-AdfsGlobalWebContent -HelpDeskLink https://fs1.contoso.com/help/ -HelpDeskLinkText Help`  
 
  
> [!IMPORTANT]  
> Параметр `linkText` в этом командлете не является обязательным, за исключением случаев использования значения, отличного от значения по умолчанию — *Help* (справка). Преимущество использования значения по умолчанию — локализация на все языковые стандарты клиента. После настройки страницы входа вступают в силу пользовательские настройки. Следовательно, необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать.  


## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
