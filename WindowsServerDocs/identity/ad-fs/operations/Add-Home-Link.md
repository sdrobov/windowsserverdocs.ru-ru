---
ms.assetid: da035189-e87f-4597-9933-49bf391a8d5d
title: Добавление ссылки на домашнюю страницу
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: a9a043390f5bfb412e549779ed4a9048d1c8a0b5
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66190179"
---
# <a name="add-home-link"></a>Добавление ссылки на домашнюю страницу 

Чтобы добавить ссылки на домашнюю страницу, отображаемый на странице входа\-на странице, используйте следующий командлет Windows PowerShell и синтаксис. 


![Добавление ссылки на домашнюю страницу](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png) 
  

`Set-AdfsGlobalWebContent -HomeLink https://fs1.contoso.com/home/ -HomeLinkText Home ` 
 
  
> [!IMPORTANT]  
> Параметр `linkText` в этом командлете не является обязательным, за исключением случаев использования значения, отличного от значения по умолчанию — *Home*(главная). Преимущество использования значения по умолчанию — локализация на все языковые стандарты клиента. После знака\-странице имеет силу пользовательские настройки имеет более высокий приоритет; таким образом, необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать.

## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)  
