---
ms.assetid: da035189-e87f-4597-9933-49bf391a8d5d
title: Добавление ссылки на домашнюю страницу
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: f4a6210b1b7475a4ec34bbe0575915f376381fe1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859387"
---
# <a name="add-home-link"></a>Добавление ссылки на домашнюю страницу 

Чтобы добавить ссылку Home, которая отображается на странице входа\-на страницу, используйте следующий командлет и синтаксис Windows PowerShell. 


![Добавить домашнюю ссылку](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png) 
  

`Set-AdfsGlobalWebContent -HomeLink https://fs1.contoso.com/home/ -HomeLinkText Home ` 
 
  
> [!IMPORTANT]  
> Параметр `linkText` в этом командлете не является обязательным, за исключением случаев использования значения, отличного от значения по умолчанию — *Home* (главная). Преимущество использования значения по умолчанию — локализация на все языковые стандарты клиента. После настройки знака\-на странице Параметры настройки имеют приоритет. Поэтому следует настроить для всех языков, которые требуется поддерживать.

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
