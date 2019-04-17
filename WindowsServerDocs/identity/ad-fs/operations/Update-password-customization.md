---
ms.assetid: 7e804590-6d6c-4cca-ac14-02d4dff06cec
title: "Настройки обновления пароля"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 4b06992bfb398b66988ad4882217a8a83738365e
ms.sourcegitcommit: 78d8839ccafa9530784cb9e38c3127ed2c215423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="update-password-customization"></a>Настройки обновления пароля 

>Область применения: Windows Server 2016, Windows Server 2012 R2

В некоторых случаях пользователи не смогут подключиться к корпоративной сети, чтобы изменить пароль учетной записи. Это может создавать проблемы, особенно для удаленных сотрудников, которые зачастую живут далеко от ближайшего офиса компании. Для подобных особых случаев страница обновления паролей может использоваться только при наличии подключения к Интернету.  
  
Можно настроить страницу обновления пароля, предоставив собственное описание страницы.  
  
> Чтобы включить страницы обновления пароля, перейдите к управления AD FS в группе конечных точек. Конечная точка для обновления пароля расположена внизу, под заголовком прочие — / adfs/portal/updatepassword /. Включив конечную точку, необходимо перезапустить службу AD FS. Это делается вручную. Затем можно перейти к https://<fqdn>/adfs/portal/updatepassword/на рабочих местах устройства, подключенного к, отобразится страница обновления паролей.  
  
![обновление](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom5.png)  
  
## <a name="customize-the-update-password-page-description"></a>Настройка описания страницы обновления пароля  
Чтобы настроить описание страницы обновления пароля, используйте следующий командлет Windows PowerShell и синтаксисом.  
  

    Set-AdfsGlobalWebContent -UpdatePasswordPageDescriptionText "This is the Contoso Update Password page."  

## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)  
