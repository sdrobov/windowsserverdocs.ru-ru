---
ms.assetid: 2bac7744-9de3-491a-b0a2-4e843cec7344
title: Добавление ссылки на службу технической поддержки
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 1673e6ee6357a9d59e8ac5891625d453bb434088
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71358465"
---
# <a name="add-help-desk-link"></a>Добавление ссылки на службу технической поддержки 


## <a name="to-add-a-help-desk-link"></a>Добавление ссылки службы поддержки  
Чтобы добавить ссылку службы поддержки, которая отображается на странице Sign @ no__t-0in, используйте следующий командлет и синтаксис Windows PowerShell.  

![Добавить службу поддержки](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  

`Set-AdfsGlobalWebContent -HelpDeskLink https://fs1.contoso.com/help/ -HelpDeskLinkText Help`  
 
  
> [!IMPORTANT]  
> Параметр `linkText` в этом командлете не является обязательным, за исключением случаев использования значения, отличного от значения по умолчанию — *Help*(справка). Преимущество использования значения по умолчанию — локализация на все языковые стандарты клиента. После настройки страницы входа вступают в силу пользовательские настройки. Следовательно, необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать.  


## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
