---
title: Важная информация для использования ADK Windows Server Essentials
description: Описание использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 26cb2992-1250-4672-98ee-8b870baa45d5
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 9a06f3b6431ae6079869e1d7fe9bc3f0ef5e597b
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80311747"
---
# <a name="important-information-for-using-the-windows-server-essentials-adk"></a>Важная информация для использования ADK Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Для создания и настройки образа Windows Server Essentials используются многие средства в [Windows 8 ADK](https://go.microsoft.com/fwlink/?LinkId=248647), но существуют некоторые важные различия между Windows 8 ADK и Windows Server Essentials ADK.  
  
 Следует учитывать следующие важные отличия.  
  
-   В **%windir%\setup\script\SetupComplete.cmd** изменились некоторые параметры. Если необходимо использовать эту команду, можно добавить дополнительные командлеты, но не удаляйте существующие строки.  
  
## <a name="working-with-passwords"></a>Работа с паролями  
  
-   Пароль администратора имеет значение Admin@123 и автоматический вход в систему включен в install. вим\унаттенд.ксмл. Поэтому нет необходимости вводить пароль несколько раз при начальной настройке сервера. Если в корне съемного носителя находится файл unattend.xml с пользовательскими настройками, эти настройки будут изменены, и потребуется задать пароль и выполнять вход при запуске.  
  
-   В ходе начальной настройки пользователю предлагается создать новую учетную запись и пароль. Эта учетная запись становится сетевой учетной записью администратора для операционной системы. Учетная запись администратора и автоматический доступ в систему после этого отключается. В процессе тестирования с целью проверки качества можно автоматизировать этот процесс с помощью файла cfg.ini.  
  
-   Сведения о создании файла unattend.xml см. в документации [Windows 8 ADK](https://go.microsoft.com/fwlink/?LinkId=248694) .  
  
## <a name="see-also"></a>См. также  

 [Начало работы с Windows Server ESSENTIALS ADK](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и Настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа к развертыванию](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Начало работы с Windows Server ESSENTIALS ADK](../install/Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и Настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа к развертыванию](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

