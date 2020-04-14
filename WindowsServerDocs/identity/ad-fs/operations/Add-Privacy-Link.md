---
ms.assetid: 1ca6f87f-7272-4767-b609-3e295ac7d32f
title: Добавление ссылки на заявление о конфиденциальности
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: cf111fbfc14665d489201f7d88419bdeffb737f9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859397"
---
# <a name="add-privacy-link"></a>Добавление ссылки на заявление о конфиденциальности 


Чтобы добавить ссылку "Конфиденциальность", отображаемую на странице "вход\-", используйте следующий командлет и синтаксис Windows PowerShell.  

![Добавить ссылку на конфиденциальность](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png) 
  
 
`Set-AdfsGlobalWebContent -PrivacyLink https://fs1.contoso.com/privacy/ -PrivacyLinkText Privacy`  
 
  
> [!IMPORTANT]  
> Параметр `linkText` в этом командлете не является обязательным, за исключением случаев использования значения, отличного от значения по умолчанию — *Privacy* (конфиденциальность). Преимущество использования значения по умолчанию — локализация страниц на все языковые стандарты клиента. После настройки знака\-на странице Параметры настройки имеют приоритет. Поэтому следует настроить для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр, определяющий языковой стандарт. При настройке локализованного содержимого его следует настроить с использованием страны\-меньше языкового стандарта, например en, перед настройкой страны и региона\-определенного языкового стандарта, например en\-US.  

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
