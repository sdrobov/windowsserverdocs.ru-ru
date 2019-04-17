---
title: "Важная информация для использования ADK Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
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
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="important-information-for-using-the-windows-server-essentials-adk"></a>Важная информация для использования ADK Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Для создания и настройки образа Windows Server Essentials, вы можете использовать множество инструментов [Windows 8 ADK](https://go.microsoft.com/fwlink/?LinkId=248647), но есть несколько важных отличий между Windows 8 ADK и Windows Server Essentials ADK.  
  
 Следует учитывать следующие важные отличия.  
  
-   Изменились некоторые параметры в **%windir%\setup\script\SetupComplete.cmd**. Если вы хотите использовать эту команду, можно добавить дополнительные командлеты, но не удаляйте существующие строки.  
  
## <a name="working-with-passwords"></a>Работа с паролями  
  
-   Задать пароль администратора Admin@123 и автоматический вход в Install.wim\unattend.xml. Поэтому не требуется вводить пароль несколько раз во время начальной настройки сервера. Если у вас есть настроенный файл unattend.xml в корне съемного носителя, эти настройки будут изменены и нужно будет задать пароль и входа в систему во время запуска...  
  
-   Во время начальной настройки пользователю предлагается создать новую учетную запись и пароль. Эта учетная запись становится сетевой учетной записи администратора для операционной системы. Учетная запись и автоматический вход администратора после этого отключается. Этот процесс можно автоматизировать с помощью файла cfg.ini используется для проверки качества.  
  
-   Обратитесь к [Windows 8 ADK](https://go.microsoft.com/fwlink/?LinkId=248694) Дополнительные сведения о создании файла unattend.xml.  
  
## <a name="see-also"></a>См. также:  

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

