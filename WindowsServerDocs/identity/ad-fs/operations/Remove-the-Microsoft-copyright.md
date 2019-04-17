---
ms.assetid: c89a977c-b09f-44ec-be42-41e76a6cf3ad
title: "Удалить об авторских правах Майкрософт"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: c2e6f9445e53a5b5867a763d58ad4a6ca3600cbe
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="remove-the-microsoft-copyright"></a>Удалить об авторских правах Майкрософт 

>Область применения: Windows Server 2016, Windows Server 2012 R2
 
По умолчанию страницы AD FS содержат об авторских правах Майкрософт. Для удаления этих сведений с настроенных страниц, можно использовать следующую процедуру. 

![Удалите защищенные авторским правом](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1.png) 
  
## <a name="to-remove-the-microsoft-copyright"></a>Чтобы удалить об авторских правах Майкрософт  
  
1.  Создайте пользовательскую тему на основании по умолчанию.  
  

    `New-AdfsWebTheme –Name custom –SourceName default ` 
 
  
2.  Экспортируйте тему в указанную папку вывода.  

    `Export-AdfsWebTheme -Name custom -DirectoryPath C:\customWebTheme ` 

  
3.  Найдите файл Style.css, расположенный в папке вывода. В предыдущем примере, путь будет иметь C:\\CustomWebTheme\\Css\\Style.css.  
  
4.  Откройте файл Style.css редакторе, например в блокноте.  
  
5.  Найдите `#copyright` фрагмент и затем измените ее следующим:  
  `#copyright {color:#696969; display:none;} ` 
 
6.  Создайте пользовательскую тему на основе нового файла Style.css.  
  
    `Set-AdfsWebTheme -TargetName custom -StyleSheet @{locale="";path="C:\customWebTheme\css\style.css"}  `

7.  Активируйте новую тему.  
  

    `Set-AdfsWebConfig -ActiveThemeName custom ` 


Теперь вы больше не увидите об авторских правах в нижней части страницы входа.

![Удалите защищенные авторским правом](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1a.png) 

## <a name="additional-references"></a>Дополнительные ссылки 
[Настройка входа в AD FS пользователя](AD-FS-user-sign-in-customization.md) 
