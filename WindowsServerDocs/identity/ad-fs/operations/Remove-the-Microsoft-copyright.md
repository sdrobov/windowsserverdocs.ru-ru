---
ms.assetid: c89a977c-b09f-44ec-be42-41e76a6cf3ad
title: Удаление авторского права Майкрософт
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 9306950ab83ea94c1ff814ea9a404c0efeff0e40
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80816217"
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

3. Найти файл `Style.css`, расположенный в выходной папке. Используя предыдущий пример, путь будет `C:\CustomWebTheme\Css\Style.css.`
  
4. Откройте файл `Style.css` в редакторе, например в блокноте.  
  
5. Найдите часть `#copyright` и измените ее следующим образом:  

   ```css
   #copyright {color:#696969; display:none;}
   ```

6. Создайте пользовательскую тему на основе нового файла `Style.css`.  

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
