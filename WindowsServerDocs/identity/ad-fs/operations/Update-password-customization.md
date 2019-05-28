---
ms.assetid: 7e804590-6d6c-4cca-ac14-02d4dff06cec
title: Обновить настройки пароль
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: e67c04c98a53f4f1db36e6586fa77bcf181a8d5a
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66188974"
---
# <a name="update-password-customization"></a>Обновить настройки пароль 


Возможны ситуации, когда пользователи не смогут подключиться к корпоративной сети, чтобы изменить пароль к своей учетной записи. Это может создавать проблемы, особенно для удаленных сотрудников, которые зачастую живут далеко от ближайшего офиса компании. Для подобных особых случаев страница обновления паролей может использоваться только при наличии подключения к Интернету.  
  
Можно настроить страницу обновления пароля, предоставив собственное описание страницы.  
  
> Для включения страницы обновления паролей перейдите в раздел "Управление AD FS" в области "Конечные точки". Конечная точка для обновления пароля расположена внизу, под заголовком "Прочие" — /adfs/portal/updatepassword/. Включив конечную точку, необходимо перезапустить службу AD FS. Это делается вручную. Затем можно перейти по ссылке https://<fqdn>/adfs/portal/updatepassword/ с присоединенного к рабочему месту устройства, отобразится страница обновления пароля.  
  
![обновление](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom5.png)  
  
## <a name="customize-the-update-password-page-description"></a>Настройка описания страницы обновления пароля  
Чтобы настроить описание страницы обновления пароля, используйте следующий командлет Windows PowerShell и синтаксисом.  
  

    Set-AdfsGlobalWebContent -UpdatePasswordPageDescriptionText "This is the Contoso Update Password page."  

## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)  
