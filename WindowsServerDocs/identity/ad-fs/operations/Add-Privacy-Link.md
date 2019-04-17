---
ms.assetid: 1ca6f87f-7272-4767-b609-3e295ac7d32f
title: "Добавление ссылки на конфиденциальность"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 81a453b45693b8222bdfc0231885b506fdfcd2fc
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="add-privacy-link"></a>Добавление ссылки на конфиденциальность 

>Область применения: Windows Server 2016, Windows Server 2012 R2

Чтобы добавить личную ссылку, которая отображается на странице входа, используйте следующий командлет Windows PowerShell и синтаксисом.  

![Добавление ссылки на конфиденциальность](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png) 
  
 
`Set-AdfsGlobalWebContent -PrivacyLink https://fs1.contoso.com/privacy/ -PrivacyLinkText Privacy`  
 
  
> [!IMPORTANT]  
> `linkText`В этом командлете не требуется, если не используется другой значения по умолчанию, который является *конфиденциальности*. Преимущество использования значения по умолчанию — локализация страниц на все языковые стандарты клиента. После настройки страницы входа вступают в силу настройки; Таким образом необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр языкового стандарта. При настройке локализованного содержимого, следует настроить запись в языковом стандарте country\ менее во-первых, например, «en», прежде чем настраивать страны и region\ языковой стандарт, таких как «en\-us».  

## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)  
