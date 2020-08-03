---
ms.assetid: a4526500-24b3-423d-805c-24b0d8061aba
title: Изменение иллюстрации на странице входа AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 47a71fffc864f6ae5ecb46d562f92d2d9cece092
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87519793"
---
# <a name="change-the-illustration-on-the-ad-fs-sign-in-page"></a>Изменение иллюстрации на странице входа AD FS

## <a name="change-the-illustration"></a>Изменение иллюстрации

Чтобы изменить иллюстрацию, рисунок слева, отображаемый на \- странице входа, должен использовать следующий командлет и синтаксис Windows PowerShell.

![изменить иллюстрацию](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)

> [!IMPORTANT]
> Рекомендуемые размеры иллюстрации —1420 x 1080 пикселей @ 96 точек на дюйм. Размер файла не должен превышать 200 КБ.

```powershell
Set-AdfsWebTheme -TargetName default -Illustration @{path="c:\Contoso\illustration.png"}
```

## <a name="additional-references"></a>Дополнительные ссылки

[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)
