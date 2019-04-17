---
ms.assetid: da035189-e87f-4597-9933-49bf391a8d5d
title: "Добавление ссылки на домашнюю страницу"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: fb903c62e717e36099934e64e1c939a502f691a3
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="add-home-link"></a>Добавление ссылки на домашнюю страницу 

>Область применения: Windows Server 2016, Windows Server 2012 R2

Чтобы добавить ссылки на домашнюю страницу, отображаемый на странице входа, используйте следующий командлет Windows PowerShell и синтаксисом. 


![Добавление ссылки на домашнюю страницу](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png) 
  

`Set-AdfsGlobalWebContent -HomeLink https://fs1.contoso.com/home/ -HomeLinkText Home ` 
 
  
> [!IMPORTANT]  
> `linkText`В этом командлете не требуется, если не используется другой значения по умолчанию, который является *Главная*. Преимущество использования значения по умолчанию — что локализация на все языковые стандарты клиента. После настройки страницы входа вступают в силу настройки; Таким образом необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать.

## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)  
