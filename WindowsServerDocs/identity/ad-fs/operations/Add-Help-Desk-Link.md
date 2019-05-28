---
ms.assetid: 2bac7744-9de3-491a-b0a2-4e843cec7344
title: Добавление ссылки на службу технической поддержки
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: fb186c3ba5cfb3acb9bfd0c3139b09b992fb8863
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66190211"
---
# <a name="add-help-desk-link"></a>Добавление ссылки на службу технической поддержки 


## <a name="to-add-a-help-desk-link"></a>Чтобы добавить ссылки на службу поддержки справки  
Чтобы добавить ссылки на службу поддержки справки, отображаемый на странице входа\-на странице, используйте следующий командлет Windows PowerShell и синтаксис.  

![добавить службу технической поддержки](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  

`Set-AdfsGlobalWebContent -HelpDeskLink https://fs1.contoso.com/help/ -HelpDeskLinkText Help`  
 
  
> [!IMPORTANT]  
> Параметр `linkText` в этом командлете не является обязательным, за исключением случаев использования значения, отличного от значения по умолчанию — *Help*(справка). Преимущество использования значения по умолчанию — локализация на все языковые стандарты клиента. После настройки страницы входа вступают в силу пользовательские настройки. Следовательно, необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать.  


## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)  
