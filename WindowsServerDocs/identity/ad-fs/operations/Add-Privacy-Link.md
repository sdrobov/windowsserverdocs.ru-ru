---
ms.assetid: 1ca6f87f-7272-4767-b609-3e295ac7d32f
title: Добавление ссылки на заявление о конфиденциальности
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 81a453b45693b8222bdfc0231885b506fdfcd2fc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59836805"
---
# <a name="add-privacy-link"></a>Добавление ссылки на заявление о конфиденциальности 

>Область применения. Windows Server 2016, Windows Server 2012 R2

Чтобы добавить ссылки конфиденциальности, которая отображается на странице входа\-на странице, используйте следующий командлет Windows PowerShell и синтаксис.  

![Добавление ссылки на конфиденциальность](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png) 
  
 
`Set-AdfsGlobalWebContent -PrivacyLink https://fs1.contoso.com/privacy/ -PrivacyLinkText Privacy`  
 
  
> [!IMPORTANT]  
> Параметр `linkText` в этом командлете не является обязательным, за исключением случаев использования значения, отличного от значения по умолчанию — *Privacy*(конфиденциальность). Преимущество использования значения по умолчанию — локализация страниц на все языковые стандарты клиента. После знака\-странице имеет силу пользовательские настройки имеет более высокий приоритет; таким образом, необходимо выполнить пользовательскую настройку для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр, определяющий языковой стандарт. При настройке локализованного содержимого необходимо настроить со страной\-меньше языкового стандарта первой, например, «en», прежде чем настраивать страны и региона\-конкретного языкового стандарта, например «en\-США».  

## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)  
