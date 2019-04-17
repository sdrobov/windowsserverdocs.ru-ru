---
title: "Создание носителя для восстановления клиента нескольких языков"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fdbc016-d464-43cb-bd75-8a63e61588a2
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 1ad934d297c3092050bd6adbb6bb0f50d1ec6f36
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="build-multi-language-client-restore-media"></a>Создание носителя для восстановления клиента нескольких языков

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

> [!NOTE]
>  Сначала необходимо создать многоязыковой образ Windows, как описано в [Пошаговое руководство: создание многоязыкового образа Windows](https://technet.microsoft.com/library/jj126995) перед добавлением Windows Server Essentials в install.wim языковой пакет.  
  
 При создании многоязычного установочного DVD-диска, языковые пакеты будут устанавливаться для сервера install.wim. Локализованные ресурсы для мастера восстановления устанавливаются в составе языковых пакетов.  
  
### <a name="to-build-a-multi-language-client-restore-media"></a>Создание носителя для восстановления клиента нескольких языков  
  
1.  Подключите install.wim в c:\mount в папку c:\mount\Program Files\Windows Server\bin\ClientRestore вызываем качестве корневой для носителя для восстановления клиента: [RestoreMediaRoot] ниже:  
  
    ```  
    dism /mount-wim /wimfile:install.wim /index:1 /mountdir:c:\mount  
    ```  
  
2.  WIM-файл восстановления клиента в [RestoreMediaRoot]\Sources\Boot.wim (же шаги необходимо выполнить для boot_x86.wim слишком). В командной строке указано:  
  
    ```  
    dism /mount-wim /wimfile:boot.wim /index:1 /mountdir:c:\mountRestore  
    ```  
  
3.  Добавьте пакет WinPE-Setup.cab на носитель для восстановления, запустив:  
  
    ```  
    dism /image:c:\mountRestore /add-package /packagepath:WinPE-Setup.cab  
    ```  
  
4.  С помощью блокнота отредактируйте c:\mountRestore\windows\system32\winpeshl.ini, впишите следующее содержимое:  
  
    ```  
    [LaunchApp]  
    AppPath = %SYSTEMDRIVE%\sources\SelectLanguage.exe  
    ```  
  
5.  Добавьте языковые пакеты на носитель для восстановления. Добавление языковых пакетов, можно выполнить следующую команду:  
  
    ```  
    dism /image:c:\mountRestore /add-package /packagepath:[language pack path]  
    ```  
  
     Следующие языковые пакеты необходимо добавить:  
  
    1.  WinPE языковой пакет (lp.cab)  
  
    2.  Языковой пакет установки среды предустановки Windows (WinPE-Setup_ [lang] .cab, например, WinPE-Setup_en-us.cab)  
  
    3.  Для азиатских шрифтов, включая zh-cn, zh-tw, zh-hk, ko-kr, ja-jp, необходимо установить дополнительный пакет шрифтов (winpe - fontsupport-[lang] .cab, например, winpe-fontsupport-zh-cn.cab)  
  
6.  Создайте новый файл Lang.ini командой:  
  
    ```  
    dism /image:c:\mountRestore /Gen-LangINI /distribution:mount  
    ```  
  
7.  Зафиксируйте и отключите образ, выполнив:  
  
    ```  
    dism /unmount-wim /mountdir:c:\mountRestore /commit  
    ```  
  
8.  Повторите шаг 2 к шагу 7 для [RestoreMediaroot]\Sources\Boot_x86.wim.  
  
9. Зафиксируйте и отключите образ, выполнив:  
  
    ```  
    dism /unmount-wim /mountdir:c:\mount /commit  
    ```  
  
## <a name="see-also"></a>См. также:  

 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

