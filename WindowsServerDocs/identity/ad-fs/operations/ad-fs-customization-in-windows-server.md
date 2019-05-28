---
ms.assetid: 25f5aff1-6abf-4dea-b531-f1d9943bc181
title: Настройка AD FS в Windows Server 2016
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: b5aa22ad99529d99e2d7381a434916e8e749f185
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66188761"
---
# <a name="ad-fs-customization-in-windows-server-2016"></a>Настройка AD FS в Windows Server 2016


В ответ на отзывы от организаций, с помощью AD FS мы добавили дополнительные средства для настройки пользователя вход в систему для отдельных приложений, которые защищены AD FS.  
Помимо указания содержимого веб-приложения, например текст описания и ссылки, теперь можно указать всего веб-темы каждого приложения.  Сюда входят логотип, иллюстрация, стилей или файл всей onload.js.  
  
## <a name="global-settings"></a>Глобальные параметры    
Общие глобальных параметров см. в [Customizing the AD FS Sign-in Pages](https://technet.microsoft.com/library/dn280950.aspx) , поставляемых с AD FS в Windows Server 2012 R2.  
  
## <a name="pre-requisites"></a>Предварительные требования  
Перед выполнением процедуры, описанные в этом документе, необходимы следующие предварительные требования.  
  
-   AD FS в Windows Server 2016 TP4 или более поздней версии  
  
## <a name="configure-ad-fs-relying-parties"></a>Настройка AD FS проверяющим сторонам  
На доверяющей стороной вход веб элементов и темы можно настроить с помощью приведенных ниже примерах PowerShell:  
  
### <a name="customize-messages"></a>Настройка сообщений  
  
```  
PS C:\>Set-AdfsRelyingPartyWebContent  
    -TargetRelyingPartyName "<RP trust Name>"  
    -CompanyName "This text appears in place of the federation service display name"  
    -OrganizationalNameDescriptionText "This text appears right below the company name"  
    -SignInPageDescription "This text appears below the credential prompt"  
```  
  
### <a name="customize-company-name-logo-and-image"></a>Настроить название компании, логотип и изображения  
  
```  
PS C:\>Set-AdfsRelyingPartyWebTheme  
    -TargetRelyingPartyName "<RP trust Name>"  
    -Logo @{path="C:\Images\applogo.png"}  
    -Illustration @{path="C:\Images\appillustration.jpg"}  
```  
  
### <a name="customize-entire-page"></a>Настройка всей страницы  
  
```  
PS C:\>Set-AdfsRelyingPartyWebTheme  
    -TargetRelyingPartyName "<RP trust Name>"  
    -OnLoadScriptPath @{path="c:\scripts\adfstheme\onload.js"}  
```  
  
## <a name="custom-themes-and-advanced-custom-themes"></a>Пользовательские темы и расширенные пользовательские темы  
  
Пользовательские темы см. в статье [Customizing the AD FS Sign-in Pages](https://technet.microsoft.com/library/dn280950.aspx) и [Advanced Customization of AD FS Sign-in Pages.](https://technet.microsoft.com/library/dn636121.aspx)  
  
## <a name="assigning-custom-web-themes-per-rp"></a>Назначение пользовательских веб-тем в RP  
  
Чтобы назначить пользовательскую тему на RP используйте следующую процедуру:  
  
1. Создать новую тему в качестве копии по умолчанию, глобальной темы в AD FS  
<code>New-AdfsWebTheme -Name AppSpecificTheme -SourceName default</code> 2.  Экспортируйте тему для настройки <code>Export-AdfsWebTheme -Name AppSpecificTheme -DirectoryPath c:\appspecifictheme</code>  
3. Настройка темы файлов (изображений, css, onload.js) - в любом редакторе или заменить файл 4. Импорт настроенных файлов из файловой системы в AD FS (предназначенных для новой темы) <code>Set-AdfsWebTheme -TargetName AppSpecificTheme -AdditionalFileResource @{Uri='/adfs/portal/script/onload.js';Path="c:\appspecifictheme\script\onload.js"}</code>  
5. Применить тему новых, специализированных конкретного поставщика Ресурсов (или Доверяющей стороны) <code>Set-AdfsRelyingPartyWebTheme -TargetRelyingPartyName urn:app1 -SourceWebThemeName AppSpecificTheme</code>  
  
## <a name="home-realm-discovery"></a>Обнаружение домашней области  
Для обнаружения домашней области настройки см. в разделе [Customizing the AD FS Sign-in Pages](https://technet.microsoft.com/library/dn280950.aspx).  
  
## <a name="updated-password-page"></a>Пароль, измененный страницы  
Сведения о настройке страница обновления паролей см. в разделе [Customizing the AD FS Sign-in Pages](https://technet.microsoft.com/library/dn280950.aspx).  
  
## <a name="customizing-and-alternate-ids"></a>Настройка и альтернативные идентификаторы  
Пользователи могут входить в службы федерации Active Directory (AD FS)-приложениями с помощью идентификатора пользователя, которая принимается доменными службами Active Directory (AD DS) в любой форме. К ним относятся имена участника-пользователя (UPN) (johndoe@contoso.com) или домена полные имена учетной записи sam (contoso\johndoe или contoso.com\johndoe).  Дополнительные сведения о см. в разделе [настройка альтернативного имени пользователя.](Configuring-Alternate-Login-ID.md)  
  
Кроме того можно настроить страницу входа AD FS по предоставлению конечным пользователям подсказка о альтернативного имени пользователя. Это можно сделать, добавив дополнительные сведения см. описание настроенной страницы входа в систему [Customizing the AD FS Sign-in Pages.](https://technet.microsoft.com/library/dn280950.aspx)   
  
Кроме того, это можно сделать, настроив «Войти с учетной записью организации» строку над полем имени пользователя.  Сведения о см. в разделе [Advanced Customization of AD FS Sign-in Pages](https://technet.microsoft.com/library/dn636121.aspx).  

## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md)  
