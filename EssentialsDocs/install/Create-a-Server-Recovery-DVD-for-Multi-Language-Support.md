---
title: Создание DVD-диска восстановления сервера с многоязычной поддержкой
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c7da0f6c-9732-4784-9c28-7dad72c4071d
4author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: e2bbc7bf7af71c671153bf7ba3356ddc08dcc38b
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433633"
---
# <a name="create-a-server-recovery-dvd-for-multi-language-support"></a>Создание DVD-диска восстановления сервера с многоязычной поддержкой

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

##  <a name="BKMK_MLHeadedRecovery"></a> Создать программу установки сервера и DVD-диска восстановления сервера для поддержки нескольких языков на локально администрируемых серверов  
  
> [!NOTE]
>  Необходимо сначала создать многоязыковой образ Windows, как описано в разделе [Пошаговое руководство: Создание многоязыкового образа Windows](https://technet.microsoft.com/library/jj126995) перед добавлением в install.wim языковой пакет Windows Server Essentials.  
  
 Существует два этапа установки: среда предустановки Windows (Windows PE) и начальная настройка. По умолчанию страница выбора языка при начальной настройке не отображается.  
  
- В случае установки, удаленно администрируемой поставщиком вычислительной техники, или сценария предустановки у ПВТ необходимо добавить раздел реестра, используя следующую команду для отображения страницы выбора языка в ходе начальной настройки.  
  
  ```  
  %systemroot%\system32\reg.exe add "HKLM\Software\microsoft\windows server\setup" /v ShowPreinstallPages /t REG_SZ /d true /f  
  ```  
  
  > [!IMPORTANT]
  >  При создании образа в лаборатории поставщики вычислительной техники должны выбирать **английский** язык на этапе установки среды предустановки Windows.  
  
- В сценарии использования набора для торговых посредников Reseller Option Kit (ROK) пользователи получают DVD-диск, а иногда и некоторое оборудование. Пользователь должен иметь возможность выбрать язык при установке среды предустановки Windows, и страница выбора языка больше не отображается при начальной настройке.  
  
  Можно выбрать вариант отправки одного двухслойного DVD-диска, содержащего пакеты на нескольких языках.  
  
  В этом разделе приведено описание добавления языковой поддержки в программу установки Windows. Основное средство настройки среды предустановки Windows версии 3.0 - это программа командной строки "Система обслуживания образов развертывания и управления ими" (DISM). Данное решение обеспечивает выполнение следующих сценариев:  
  
1.  создание многоязычных установок;  
  
2.  создание распространяемых носителей.  
  
### <a name="prerequisites"></a>предварительные требования  
 Чтобы добавить многоязычную поддержку в программу установки Windows, необходимо следующее:  
  

-   Обслуживающий компьютер со всеми средствами и исходными файлами, необходимыми для создания настраиваемого образа среды предустановки Windows. Дополнительные сведения см. в разделе [Prepare the Technician Computer](Prepare-the-Technician-Computer.md).  

-   Обслуживающий компьютер со всеми средствами и исходными файлами, необходимыми для создания настраиваемого образа среды предустановки Windows. Дополнительные сведения см. в разделе [Prepare the Technician Computer](../install/Prepare-the-Technician-Computer.md).  

  
-   Windows Server Essentials DVD-диска.  
  
-   Windows Server Essentials языкового пакета DVD-диска.  
  
###  <a name="BKMK_Steps"></a> Добавление поддержки нескольких языков  
 Чтобы добавить поддержку нескольких языков в программу установки Windows необходимо обновить файл Install.wim, добавив в Windows Server 2012 и Windows Server Essentials языковых пакетов к нему.  
  
#### <a name="update-installwim"></a>Обновление файла install.wim  
 На этом шаге добавьте Windows Server 2012 и языковые пакеты Windows Server Essentials в Install.wim.  
  
> [!NOTE]
>  Убедитесь, что установить языковые пакеты для Windows Server 2012. Это обеспечит использование надлежащей фирменной символики. Windows Server 2012 многоязыкового пользовательского интерфейса языка доступны на [Microsoft.com](https://www.microsoft.com/OEM/en/installation/downloads/Pages/technical-downloads.aspx). Следуйте инструкциям, описанным в [Пошаговое руководство: Создание многоязыкового образа Windows создание](https://technet.microsoft.com/library/jj126995.aspx) на создании многоязыкового образа Windows перед добавлением языкового пакета Windows Server Essentials в install.wim.  
>   
>  Языковые пакеты Windows Server Essentials находятся на носителе языковых пакетов в пакеты \Language\\< CultureName\>.  
  
> [!NOTE]
>  Не все языковые пакеты могут быть доступны до выхода Windows Server 2012.  
  
###### <a name="to-add-language-packs-to-installwim"></a>Добавление языковых пакетов в файл install.wim  
  
1.  Добавьте языковые пакеты операционной системы и продукта в файл install.wim следующим образом (в данном примере используется французский язык):  
  
    ```  
    Dism /Mount-Wim /WimFile:C:\my_distribution\sources\install.wim /index:1 /MountDir:C:\InstallMount  
    Mkdir c:\temp_Scratch  
    Dism /Image:C:\InstallMount /ScratchDir:C:\temp_Scratch /Add-Package /PackagePath:<path_to_OS_language_packs>\fr-fr\lp.cab  
    Dism /Image:C:\InstallMount /ScratchDir:C:\temp_Scratch /Add-Package /PackagePath:<OCD\Language Packs\FR-FR\lp.cab  
  
    ```  
  

2.  Добавьте языковые файлы для поддержки создания USB восстановление резервной копии клиента флэш-памяти, выполнив процедуру, описанную в [Создание многоязычного носителя для восстановления клиента](Build-Multi-Language-Client-Restore-Media.md).  

2.  Добавьте языковые файлы для поддержки создания USB восстановление резервной копии клиента флэш-памяти, выполнив процедуру, описанную в [Создание многоязычного носителя для восстановления клиента](../install/Build-Multi-Language-Client-Restore-Media.md).  

  
3.  Используя команду `DISM /Gen-LangINI` , заново создайте файл Lang.ini на съемном носителе для отражения поддержки дополнительных языков, например:  
  
    ```  
    Dism /image:C:\InstallMount /Gen-LangINI /distribution:C:\my_distribution  
  
    ```  
  
4.  Сохраните внесенные изменения в образе, используя команду `DISM /unmount /commit` , например:  
  
    ```  
    Dism /Unmount-Wim /MountDir:C:\InstallMount /Commit  
    ```  
  
## <a name="see-also"></a>См. также  

 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

