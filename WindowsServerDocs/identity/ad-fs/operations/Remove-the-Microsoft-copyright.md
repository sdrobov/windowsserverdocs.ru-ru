---
ms.assetid: c89a977c-b09f-44ec-be42-41e76a6cf3ad
title: Удалить об авторских правах Майкрософт
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: aa27a014b0803712a20fdd23f075486dc35f33c2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59820985"
---
# <a name="remove-the-microsoft-copyright"></a>Удалить об авторских правах Майкрософт 

>Область применения. Windows Server 2016, Windows Server 2012 R2
 
По умолчанию на страницах службы федерации Active Directory содержат об авторских правах Майкрософт. Для удаления этих сведений с настроенных страниц можно воспользоваться следующей процедурой. 

![удалить авторские права](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1.png) 
  
## <a name="to-remove-the-microsoft-copyright"></a>Удаление сведений об авторских правах Майкрософт  
  
1. Создайте пользовательскую тему на основе стандартной.

   ```powershell
   New-AdfsWebTheme –Name custom –SourceName default
   ```

2. Экспортируйте тему в указанную папку вывода.  

   ```powershell
   Export-AdfsWebTheme -Name custom -DirectoryPath C:\CustomWebTheme
   ```

3. Найдите `Style.css` файл, расположенный в папке выходных данных. С помощью предыдущего примера, путь будет иметь `C:\CustomWebTheme\Css\Style.css.`
  
4. Откройте `Style.css` файла с редактором, например в блокноте.  
  
5. Найдите часть `#copyright` и измените ее следующим образом:  

   ```css
   #copyright {color:#696969; display:none;}
   ```

6. Создайте пользовательскую тему, основанный на новом `Style.css` файл.  

   ```powershell
   Set-AdfsWebTheme -TargetName custom -StyleSheet @{locale="";path="C:\customWebTheme\css\style.css"}
   ```

7. Активируйте новую тему.  

   ```powershell
   Set-AdfsWebConfig -ActiveThemeName custom
   ```

Сейчас вы больше не увидите авторских прав в нижней части страницы входа.

![удалить авторские права](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1a.png) 

## <a name="additional-references"></a>Дополнительная справка 
[Настройка входа AD FS пользователя](AD-FS-user-sign-in-customization.md) 
