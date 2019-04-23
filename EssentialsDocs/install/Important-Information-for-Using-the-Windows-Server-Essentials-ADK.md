---
title: Важная информация для использования ADK Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 26cb2992-1250-4672-98ee-8b870baa45d5
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 4dec1fdf01538ca119b991675f932d2d8ec1e097
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59838645"
---
# <a name="important-information-for-using-the-windows-server-essentials-adk"></a>Важная информация для использования ADK Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Для создания и настройки образа Windows Server Essentials, можно использовать разнообразные средства в [Windows 8 ADK](https://go.microsoft.com/fwlink/?LinkId=248647), но есть некоторые важные различия между Windows 8 ADK и Windows Server Essentials ADK.  
  
 Следует учитывать следующие важные отличия.  
  
-   В **%windir%\setup\script\SetupComplete.cmd** изменились некоторые параметры. Если необходимо использовать эту команду, можно добавить дополнительные командлеты, но не удаляйте существующие строки.  
  
## <a name="working-with-passwords"></a>Работа с паролями  
  
-   Пароль администратора присваивается Admin@123 и в Install.wim\unattend.xml разрешен. Поэтому нет необходимости вводить пароль несколько раз при начальной настройке сервера. Если в корне съемного носителя находится файл unattend.xml с пользовательскими настройками, эти настройки будут изменены, и потребуется задать пароль и выполнять вход при запуске.  
  
-   В ходе начальной настройки пользователю предлагается создать новую учетную запись и пароль. Эта учетная запись становится сетевой учетной записью администратора для операционной системы. Учетная запись администратора и автоматический доступ в систему после этого отключается. В процессе тестирования с целью проверки качества можно автоматизировать этот процесс с помощью файла cfg.ini.  
  
-   Сведения о создании файла unattend.xml см. в документации [Windows 8 ADK](https://go.microsoft.com/fwlink/?LinkId=248694) .  
  
## <a name="see-also"></a>См. также  

 [Начало работы с ADK Windows Server Essentials](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Начало работы с ADK Windows Server Essentials](../install/Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

