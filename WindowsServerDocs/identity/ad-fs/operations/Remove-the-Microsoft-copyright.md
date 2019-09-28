---
ms.assetid: c89a977c-b09f-44ec-be42-41e76a6cf3ad
title: Удаление авторского права Майкрософт
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 0c24173dd03e03f9e8a19ef5981a6dc1259d62d7
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407512"
---
# <a name="remove-the-microsoft-copyright"></a>Удаление авторского права Майкрософт 


 
По умолчанию страницы AD FS содержат авторские права Майкрософт. Для удаления этих сведений с настроенных страниц можно воспользоваться следующей процедурой. 

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

3. Найти файл `Style.css`, расположенный в папке выходных данных. Используя предыдущий пример, путь будет иметь вид `C:\CustomWebTheme\Css\Style.css.`.
  
4. Откройте файл `Style.css` в редакторе, например в блокноте.  
  
5. Найдите часть `#copyright` и измените ее следующим образом:  

   ```css
   #copyright {color:#696969; display:none;}
   ```

6. Создайте пользовательскую тему, основанную на новом файле `Style.css`.  

   ```powershell
   Set-AdfsWebTheme -TargetName custom -StyleSheet @{locale="";path="C:\customWebTheme\css\style.css"}
   ```

7. Активируйте новую тему.  

   ```powershell
   Set-AdfsWebConfig -ActiveThemeName custom
   ```

Теперь вы больше не должны видеть авторские права в нижней части страницы входа.

![удалить авторские права](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1a.png) 

## <a name="additional-references"></a>Дополнительная справка 
[AD FS настройки входа пользователя](AD-FS-user-sign-in-customization.md) 
