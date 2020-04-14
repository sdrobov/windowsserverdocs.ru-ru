---
ms.assetid: 0379abc3-25c7-46ab-9a6b-80a5152365b0
title: Пользовательские веб-темы в AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 69255eeaecd3e5198054242c1ab6dd1d0a58ce33
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80816427"
---
# <a name="custom-web-themes-in-ad-fs"></a>Пользовательские веб-темы в AD FS 

Тема, которая поставляется\-\-\-Box, называется по умолчанию. Можно экспортировать тему по умолчанию и воспользоваться ей, чтобы быстро приступить к работе. Можно настроить внешний вид и поведение, включая настройку макета (путем изменения CSS-файла), импортировать и применить эту новую тему, а затем работать с настроенными внешним видом и поведением. Использование CSS-файла упрощает взаимодействие с веб-дизайнерами.  
  
Следующий командлет позволяет создать пользовательскую веб-тему, дублирующую веб-тему по умолчанию.  
  
  
`New-AdfsWebTheme –Name custom –SourceName default ` 

  
Можно изменить CSS-файл и настроить новую веб-тему с помощью нового CSS-файла. Для экспорта веб-темы воспользуйтесь следующим командлетом.  
  

    Export-AdfsWebTheme –Name default –DirectoryPath c:\theme  

  
Для применения CSS-файла к новой теме воспользуйтесь следующим командлетом.  
  

    Set-AdfsWebTheme –TargetName custom –StyleSheet @{path="c:\NewTheme.css"}  
  
  
Следующий командлет позволяет создать пользовательскую веб-тему из новой таблицы стилей.  
  
  
`New-AdfsWebTheme –Name custom –StyleSheet @{path="c:\NewTheme.css"} –RTLStyleSheetPath c:\NewRtlTheme.css ` 
  
  
  
Чтобы применить пользовательскую веб-тему к AD FS, используйте следующий командлет.  
  

`Set-AdfsWebConfig -ActiveThemeName custom`  

  
Чтобы добавить JavaScript в AD FS, используйте следующий командлет.  
  
 
    Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri=' /adfs/portal/script/onload.js';path="D:\inetpub\adfsassets\script\onload.js"}  


## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md)  
