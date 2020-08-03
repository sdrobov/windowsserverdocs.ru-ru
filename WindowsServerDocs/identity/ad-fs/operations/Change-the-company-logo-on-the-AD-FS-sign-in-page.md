---
ms.assetid: f7f6bac2-1100-4b00-a248-4ca3eb3cdbe9
title: Изменение логотипа компании на странице входа AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 03/08/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: b61f7321dc75613a3450998284536673bd790f2b
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87519823"
---
# <a name="changing-the-company-logo-on-the-ad-fs-sign-in-page"></a>Изменение логотипа компании на странице входа AD FS

## <a name="change-company-logo"></a>Изменение логотипа компании

Чтобы изменить эмблему компании, отображаемую на \- странице входа, используйте следующий командлет PowerShell Windows PowerShell и синтаксис.

![изменить логотип](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)

> [!IMPORTANT]
> Рекомендуемые размеры логотипа — 260 x 35 @ 96 точек на дюйм. Размер файла не должен превышать 10 КБ.

```powershell
Set-AdfsWebTheme -TargetName default -Logo @{path="c:\Contoso\logo.png"}
```

> [!NOTE]
> Параметр `TargetName` является обязательным. Тема по умолчанию, которая выпускается с AD FS, называется *Default*.

## <a name="additional-references"></a>Дополнительные ссылки

[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)
