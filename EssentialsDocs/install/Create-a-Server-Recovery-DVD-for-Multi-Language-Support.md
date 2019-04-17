---
title: "Создание DVD-диска восстановления сервера для многоязычной поддержки"
description: "Описывается, как использовать Windows Server Essentials"
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
ms.openlocfilehash: ac547f97b48e4cd0ebf87e0935cadc2c539b4d0b
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="create-a-server-recovery-dvd-for-multi-language-support"></a>Создание DVD-диска восстановления сервера для многоязычной поддержки

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

##  <a name="BKMK_MLHeadedRecovery"></a>Создание установки сервера и DVD-диска восстановления сервера для поддержки нескольких языков на локально администрируемых серверах  
  
> [!NOTE]
>  Сначала необходимо создать многоязыковой образ Windows, как описано в [Пошаговое руководство: создание многоязыкового образа Windows](https://technet.microsoft.com/library/jj126995) перед добавлением Windows Server Essentials в install.wim языковой пакет.  
  
 Существует два этапа установки: среда предустановки Windows (Windows PE) и начальная настройка. По умолчанию страница выбора языка при начальной настройке не отображается.  
  
-   Для установки удаленно администрируемой поставщиком вычислительной Техники или сценария предустановки у ПВТ необходимо добавить раздел реестра, используя следующую команду для отображения страницы выбора языка в ходе начальной настройки.  
  
    ```  
    %systemroot%\system32\reg.exe add "HKLM\Software\microsoft\windows server\setup" /v ShowPreinstallPages /t REG_SZ /d true /f  
    ```  
  
    > [!IMPORTANT]
    >  После создания образа в лаборатории поставщики вычислительной техники техники должны выбирать **английского** языком программы установки на этапе среды Предустановки Windows.  
  
-   При использовании сценария торгового посредника Option Kit (ROK) пользователи получают DVD-диска, а иногда и некоторое оборудование. Пользователь должен иметь возможность выбрать язык при установке среды Предустановки Windows, и страница выбора языка больше не отображается при начальной настройки.  
  
 Можно выбрать вариант отправки одного двухслойного DVD-диска, содержащего множество языков.  
  
 В этом разделе описывается добавление поддержки языков в программу установки Windows. Основное средство настройки среды Предустановки Windows версии 3.0 является система обслуживания образов развертывания и управления ими (DISM), средство командной строки. Данное решение обеспечивает следующие сценарии:  
  
1.  Создание многоязычных установок  
  
2.  Создание распространяемых носителей.  
  
### <a name="prerequisites"></a>Предварительные требования  
 Чтобы добавить многоязычную поддержку в программу установки Windows, вам потребуется следующее:  
  

-   Обслуживающий компьютер со средствами и исходными файлами, необходимыми для создания настраиваемого образа среды предустановки Windows. Дополнительные сведения см. в разделе [Подготовка обслуживающего компьютера](Prepare-the-Technician-Computer.md).  

-   Обслуживающий компьютер со средствами и исходными файлами, необходимыми для создания настраиваемого образа среды предустановки Windows. Дополнительные сведения см. в разделе [Подготовка обслуживающего компьютера](../install/Prepare-the-Technician-Computer.md).  

  
-   Windows Server Essentials DVD-диска.  
  
-   Windows Server Essentials DVD с языковым пакетом.  
  
###  <a name="BKMK_Steps"></a>Добавление поддержки нескольких языков  
 Чтобы добавить поддержку нескольких языков в программу установки Windows, необходимо обновить файл Install.wim, добавив Windows Server 2012 и Windows Server Essentials языковых пакетов к нему.  
  
#### <a name="update-installwim"></a>Обновление Install.wim  
 На этом шаге вы добавляете Windows Server 2012 и языковые пакеты Windows Server Essentials в Install.wim.  
  
> [!NOTE]
>  Убедитесь, что языковые пакеты для Windows Server 2012. Это обеспечит использование надлежащей фирменной символики. Windows Server 2012 пакеты многоязыкового пользовательского интерфейса языка будут доступны на [Microsoft.com](https://www.microsoft.com/OEM/en/installation/downloads/Pages/technical-downloads.aspx). Следуйте инструкциям, описанным в [Пошаговое руководство: создание многоязычного образа Windows на создание](https://technet.microsoft.com/library/jj126995.aspx) на создание многоязыкового образа Windows перед добавлением языкового пакета Windows Server Essentials в Install.wim.  
>   
>  Языковые пакеты Windows Server Essentials доступны на носителе языковых пакетов в \Language Packs\\ < CultureName\ >.  
  
> [!NOTE]
>  Не все языковые пакеты могут быть доступны до выхода Windows Server 2012.  
  
###### <a name="to-add-language-packs-to-installwim"></a>Добавление языковых пакетов в Install.wim  
  
1.  Добавьте языковые пакеты операционной системы и продукта в файл Install.wim следующим образом (в этом примере используется французский язык):  
  
    ```  
    Dism /Mount-Wim /WimFile:C:\my_distribution\sources\install.wim /index:1 /MountDir:C:\InstallMount  
    Mkdir c:\temp_Scratch  
    Dism /Image:C:\InstallMount /ScratchDir:C:\temp_Scratch /Add-Package /PackagePath:<path_to_OS_language_packs>\fr-fr\lp.cab  
    Dism /Image:C:\InstallMount /ScratchDir:C:\temp_Scratch /Add-Package /PackagePath:<OCD\Language Packs\FR-FR\lp.cab  
  
    ```  
  

2.  Добавьте языковые файлы для поддержки создания USB восстановление резервной копии клиента флэш-накопителя, выполнив процедуру, описанную в [Создание многоязычного носителя для восстановления клиента ](Build-Multi-Language-Client-Restore-Media.md).  

2.  Добавьте языковые файлы для поддержки создания USB восстановление резервной копии клиента флэш-накопителя, выполнив процедуру, описанную в [Создание многоязычного носителя для восстановления клиента ](../install/Build-Multi-Language-Client-Restore-Media.md).  

  
3.  Повторно создайте файл Lang.ini на съемном носителе для отражения поддержки дополнительных языков с помощью `DISM /Gen-LangINI`команды, например:  
  
    ```  
    Dism /image:C:\InstallMount /Gen-LangINI /distribution:C:\my_distribution  
  
    ```  
  
4.  Сохраните внесенные изменения в образе с помощью `DISM /unmount /commit`команды, например:  
  
    ```  
    Dism /Unmount-Wim /MountDir:C:\InstallMount /Commit  
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

