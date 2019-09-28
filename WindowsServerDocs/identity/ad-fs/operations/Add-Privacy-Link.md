---
ms.assetid: 1ca6f87f-7272-4767-b609-3e295ac7d32f
title: Добавление ссылки на заявление о конфиденциальности
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: cd559e38c38e96d1417257fe7d6ff8ccfa180c6b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71358423"
---
# <a name="add-privacy-link"></a>Добавление ссылки на заявление о конфиденциальности 


Чтобы добавить ссылку на конфиденциальность, которая отображается на странице Sign @ no__t-0in, используйте следующий командлет и синтаксис Windows PowerShell.  

![Добавить ссылку на конфиденциальность](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png) 
  
 
`Set-AdfsGlobalWebContent -PrivacyLink https://fs1.contoso.com/privacy/ -PrivacyLinkText Privacy`  
 
  
> [!IMPORTANT]  
> Параметр `linkText` в этом командлете не является обязательным, за исключением случаев использования значения, отличного от значения по умолчанию — *Privacy*(конфиденциальность). Преимущество использования значения по умолчанию — локализация страниц на все языковые стандарты клиента. После настройки страницы Sign @ no__t-0in Настройка имеет приоритет. Поэтому следует настроить для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр, определяющий языковой стандарт. При настройке локализованного содержимого необходимо сначала настроить языковой стандарт Country @ no__t-0less, например en, перед настройкой страны и региона @ no__t-1specific locale, например "EN @ no__t-2US".  

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
