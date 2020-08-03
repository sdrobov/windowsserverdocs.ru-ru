---
ms.assetid: 28043fc4-a34d-4710-ac3b-5c9d4d6a895c
title: Изменение названия компании на странице входа AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 3b6489ae115fb236e19214bceb291cd8f6dfacba
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87519813"
---
# <a name="change-the-company-name-on-the-ad-fs-sign-in-page"></a>Изменение названия компании на странице входа AD FS

Чтобы изменить имя компании, отображаемое на \- странице входа, используйте следующий командлет и синтаксис Windows PowerShell. Это значение настраивается по умолчанию с помощью значения из отображаемого имени службы федерации, вводимого во время настройки.

![изменить имя](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1.png)

```powershell
    Set-AdfsGlobalWebContent –CompanyName "Contoso Corp"
```

> [!NOTE]
> Можно также использовать интегрированную среду сценариев Windows PowerShell \( \) для изменения названия компании. С помощью интегрированной среды сценариев Windows PowerShell можно отображать содержимое в среде, \- совместимой с Юникодом. Дополнительные сведения см. в разделе [Знакомство с Windows PowerShell ISE](/previous-versions/mt707506(v=msdn.10)).

## <a name="additional-references"></a>Дополнительные ссылки

- [AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)
