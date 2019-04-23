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
ms.openlocfilehash: 1654add6a81169b3d4831d6ebba320402e0734c5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59849865"
---
# <a name="add-help-desk-link"></a>Добавление ссылки на службу технической поддержки 

>Область применения. Windows Server 2016, Windows Server 2012 R2


## <a name="to-add-a-help-desk-link"></a>Чтобы добавить ссылки на службу поддержки справки  
Чтобы добавить ссылки на службу поддержки справки, отображаемый на странице входа\-на странице, используйте следующий командлет Windows PowerShell и синтаксис.  

![добавить службу технической поддержки](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)
  

`Set-AdfsGlobalWebContent -HelpDeskLink https://fs1.contoso.com/help/ -HelpDeskLinkText Help`  
 
  
> [!IMPORTANT]  
> Параметр `linkText` в этом командлете не является обязательным, за исключением случаев использования значения, отличного от значения по умолчанию — *Help*(справка). Преимущество использования значения по умолчанию — локализация на все языковые стандарты клиента. После настройки страницы входа вступают в силу пользовательские настройки. Следовательно, необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать.  


## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)  
