---
title: Важная информация для использования ADK Windows Server Essentials
description: Описание использования Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: 26cb2992-1250-4672-98ee-8b870baa45d5
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 2dd0692237f268452d748dc26bd9134f250b4609
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80817837"
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

