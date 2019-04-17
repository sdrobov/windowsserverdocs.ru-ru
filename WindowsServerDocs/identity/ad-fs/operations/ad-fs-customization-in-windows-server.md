---
ms.assetid: 25f5aff1-6abf-4dea-b531-f1d9943bc181
title: "Настройка AD FS в Windows Server 2016"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 2e4d463f5f25fe85dc95d767c9c75b722e60b012
ms.sourcegitcommit: a2699e93a0a19cb138c1fde0c9af36774a12f865
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2017
---
# <a name="ad-fs-customization-in-windows-server-2016"></a>Настройка AD FS в Windows Server 2016

>Область применения: Windows Server 2016

В ответ на отзывы от организации, с помощью Служб федерации Active Directory мы добавили дополнительные средства для настройки пользователя входа в взаимодействие для отдельных приложений, защищенных с помощью AD FS.  
Помимо задания содержимого веб-приложения, например текст описания и ссылки, теперь можно указать весь веб-темы каждого приложения.  Сюда входят логотип, иллюстрация, стилей или файл весь onload.js.  
  
## <a name="global-settings"></a>Глобальные параметры    
Общие глобальные параметры можно ссылаться на [Customizing the AD FS Sign-in Pages](https://technet.microsoft.com/library/dn280950.aspx), поставляемых с AD FS в Windows Server 2012 R2.  
  
## <a name="pre-requisites"></a>Необходимые компоненты  
Прежде чем процедуры, описанные в данном документе требуются следующие необходимые условия.  
  
-   AD FS в Windows Server 2016 TP4 или более поздней версии  
  
## <a name="configure-ad-fs-relying-parties"></a>Настройка AD FS проверяющими сторонами  
Каждой проверяющей стороной входа в Интернете элементов и темы могут настраиваться с использованием приведенных ниже примерах PowerShell:  
  
### <a name="customize-messages"></a>Настройка сообщений  
  
```  
PS C:\>Set-AdfsRelyingPartyWebContent  
    -TargetRelyingPartyName "<RP trust Name>"  
    -CompanyName "This text appears in place of the federation service display name"  
    -OrganizationalNameDescriptionText "This text appears right below the company name"  
    -SignInPageDescription "This text appears below the credential prompt"  
```  
  
### <a name="customize-company-name-logo-and-image"></a>Настройка название компании, логотип и изображения  
  
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
  
## <a name="custom-themes-and-advanced-custom-themes"></a>Темы с настраиваемыми и дополнительные настраиваемые темы  
  
Темы с настраиваемыми см. в [Customizing the AD FS Sign-in Pages](https://technet.microsoft.com/library/dn280950.aspx) и [Advanced Customization of AD FS Sign-in Pages.](https://technet.microsoft.com/library/dn636121.aspx)  
  
## <a name="assigning-custom-web-themes-per-rp"></a>Назначение настраиваемых веб-темы на RP  
  
Чтобы назначить пользовательскую тему на RP используйте следующую процедуру:  
  
1. Создать новую тему в качестве копии по умолчанию, глобальной темы в AD FS  
<code>New-AdfsWebTheme -Name AppSpecificTheme -SourceName default</code>  
2.  Экспортируйте тему для настройки <code>Export-AdfsWebTheme -Name AppSpecificTheme -DirectoryPath c:\appspecifictheme</code>3.настройки темы файлов (образов, css, onload.js) — в любом редакторе или замените файл 4. Импорт пользовательских файлов из файловой системы для службы федерации Active Directory (нацеливание новую тему) <code>Set-AdfsWebTheme -TargetName AppSpecificTheme -AdditionalFileResource @{Uri='/adfs/portal/script/onload.js';Path="c:\appspecifictheme\script\onload.js"}</code>5.Применение темы новых, специализированных для определенных RP (или его RP)
<code>Set-AdfsRelyingPartyWebTheme -TargetRelyingPartyName urn:app1 -SourceWebThemeName AppSpecificTheme</code>  
  
## <a name="home-realm-discovery"></a>Обнаружение домашней области  
Для обнаружения домашней области в разделе настройки [Customizing the AD FS Sign-in Pages](https://technet.microsoft.com/library/dn280950.aspx).  
  
## <a name="updated-password-page"></a>Страница новый пароль  
Сведения о настройке страница обновления паролей в разделе [настройка страниц AD FS Sign-in](https://technet.microsoft.com/library/dn280950.aspx).  
  
## <a name="customizing-and-alternate-ids"></a>Настройка и альтернативные идентификаторы  
Пользователи могут входить в службы федерации Active Directory (AD FS)-приложениями, с помощью идентификатора пользователя, которая принимается доменными службами Active Directory (AD DS) в любой форме. К ним относятся имена участника-пользователя (UPN) (johndoe@contoso.com) или домена полные имена учетной записи sam (contoso\johndoe или contoso.com\johndoe).  Дополнительные сведения см. в этой статье [идентификатор настройка альтернативного входа.](Configuring-Alternate-Login-ID.md)  
  
Кроме того, можно настроить страницы входа AD FS чтобы дать пользователям некоторые подсказку о идентификатора альтернативного входа. Его можно сделать, добавив описание настроенной страницы Дополнительные сведения см. в разделе [настройка страниц AD FS Sign-in.](https://technet.microsoft.com/library/dn280950.aspx)   
  
Также это можно сделать, настроив Строка «вход с учетной записью организации» над полем имени пользователя.  Дополнительные сведения см. в этой статье [Advanced Customization of AD FS Sign-in Pages](https://technet.microsoft.com/library/dn636121.aspx).  

## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)  
