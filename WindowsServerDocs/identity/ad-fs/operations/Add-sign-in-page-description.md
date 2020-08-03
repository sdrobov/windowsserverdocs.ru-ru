---
ms.assetid: 330c7b61-dde0-432f-9b74-d250ad9cc808
title: Добавление описания страницы входа
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: d16165894b455c4e3ff33b77e84ccce9e30f3be0
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87519833"
---
# <a name="add-sign-in-page-description"></a>Добавить \- Описание страницы входа

## <a name="to-add-sign-in-page-description"></a>Добавление \- описания страницы входа
Чтобы добавить \- Описание страницы входа на \- страницу входа, используйте следующий командлет и синтаксис Windows PowerShell.

![добавить описание входа](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)

```powershell
Set-AdfsGlobalWebContent -SignInPageDescriptionText "<p>Sign-in to Contoso requires device registration. Click <A href='http://fs1.contoso.com/deviceregistration/'>here</A> for more information.</p>"
```

> [!IMPORTANT]
> Строка для параметра `SignInPageDescriptionText` поддерживает чистый HTML-код с тегами и без них. Таким образом, можно также выполнить следующий командлет, не используя &lt; тег p &gt; .  `Set-AdfsGlobalWebContent -SignInPageDescriptionText "Sign-in to Contoso requires device registration. Click <A href='http://fs1.contoso.com/deviceregistration/'>here</A> for more information." `

Когда страница входа \- настроена, настройка имеет приоритет, поэтому следует настроить для всех языков, которые требуется поддерживать. Все настроенное содержимое принимает параметр, определяющий языковой стандарт. При настройке локализованного содержимого перед настройкой \- региональных стандартов страны и региона, \- например "en US", необходимо сначала настроить страну меньше языкового стандарта, например "en" \- .

## <a name="additional-references"></a>Дополнительные ссылки

[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)
