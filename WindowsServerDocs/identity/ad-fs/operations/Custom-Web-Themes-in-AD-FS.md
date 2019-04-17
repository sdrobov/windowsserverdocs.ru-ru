---
ms.assetid: 0379abc3-25c7-46ab-9a6b-80a5152365b0
title: "Пользовательские веб-темы в AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 300c9fda84285ddfc52a4f47ea0198deb6fd33ef
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="custom-web-themes-in-ad-fs"></a>Пользовательские веб-темы в AD FS 

>Область применения: Windows Server 2016, Windows Server 2012 R2

Тема, предоставляемая в заводской out\-of\-the\-box называется по умолчанию. Можно экспортировать тему по умолчанию и воспользоваться ей, чтобы быстро приступить к работе. Можно настроить внешний вид и поведение, включая настройку макета путем изменения CSS-файла, импортировать и применить эту новую тему, а затем можно использовать настраиваемый внешний вид и поведение. С помощью CSS-файл также упрощает для работы с веб-дизайнерами.  
  
Следующий командлет создает пользовательскую веб-тему, дублирующую веб-тему по умолчанию.  
  
  
`New-AdfsWebTheme –Name custom –SourceName default ` 

  
Можно изменить CSS-файл и настроить новую веб-тему с помощью нового CSS-файла. Чтобы экспортировать веб-тему, используйте следующий командлет.  
  

    Export-AdfsWebTheme –Name default –DirectoryPath c:\theme  

  
Для применения CSS-файла к новой теме, используйте следующий командлет.  
  

    Set-AdfsWebTheme –TargetName custom –StyleSheet @{path=”c:\NewTheme.css”}  
  
  
Следующий командлет создает пользовательскую веб-тему из новой таблицы стилей.  
  
  
`New-AdfsWebTheme –Name custom –StyleSheet @{path=”c:\NewTheme.css”} –RTLStyleSheetPath c:\NewRtlTheme.css ` 
  
  
  
Для применения пользовательской веб-темы к AD FS, используйте следующий командлет.  
  

`Set-AdfsWebConfig -ActiveThemeName custom`  

  
Для добавления JavaScript в AD FS, используйте следующий командлет.  
  
 
    Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri=’ /adfs/portal/script/onload.js’;path="D:\inetpub\adfsassets\script\onload.js"}  


## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md)  
