---
title: "Создание загрузочного USB-устройства флэш-памяти"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fe8e35c-69f9-40b3-a270-22e2402510d8
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 9d587329e1141040b2511e1574649f1844dcec90
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="create-a-bootable-usb-flash-drive"></a>Создание загрузочного USB-устройства флэш-памяти

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Можно создать загрузочный флэш-накопитель USB, чтобы использовать для развертывания Windows Server Essentials. Первым шагом является Подготовка USB-накопителя с помощью DiskPart служебной программы командной строки. Сведения о DiskPart см. в разделе [параметры командной строки DiskPart](https://go.microsoft.com/fwlink/?LinkId=207073).  
  
 Дополнительные сценарии, в которых можно создавать или использовать загрузочное USB-устройство флэш-памяти, см. в следующих разделах:  
  
-   [Полное восстановление системы из существующей резервной копии компьютера клиента](https://technet.microsoft.com/library/jj713539.aspx#BKMK_CreateBootable)  
  
-   [Восстановление или исправление сервера под управлением Windows Server Essentials](https://technet.microsoft.com/library/jj593197.aspx#BKMK_Restore_2)  
  
### <a name="to-create-a-bootable-usb-flash-drive"></a>Чтобы создать загрузочное USB-устройство флэш-накопителя  
  
1.  Вставьте USB-накопитель в работающий компьютер.  
  
2.  Откройте окно командной строки от имени администратора.  
  
3.  Тип `diskpart`.  
  
4.  В новом окне командной строки, которая открывает, чтобы определить, USB-устройства флэш-номер диска или букву диска, в командной строке, введите `list disk`и нажмите клавишу ВВОД. `list disk` Команда отображает все диски на компьютере. Обратите внимание, номер диска или букву диска USB-накопителя.  
  
5.  В командной строке введите `select disk <X>`, где X — это номер или букву диска USB-устройства флэш-накопитель и нажмите клавишу ВВОД.  
  
6.  Тип `clean`и нажмите клавишу ВВОД. Эта команда удаляет все данные на USB-накопителе флэш-памяти.  
  
7.  Чтобы создать новый основной раздел на USB-накопителя, введите `create part pri`и нажмите клавишу ВВОД.  
  
8.  Чтобы выбрать только что созданный раздел, введите `select part 1`и нажмите клавишу ВВОД.  
  
9. Чтобы отформатировать раздел, введите `format fs=ntfs quick`и нажмите клавишу ВВОД.  
  
    > [!IMPORTANT]
    >  Если серверная платформа поддерживает единый интерфейс (UEFI), следует отформатировать USB-накопитель флэш-памяти в файловой системе FAT32, а в NTFS. Чтобы отформатировать раздел в файловой системе FAT32, введите `format fs=fat32 quick`и нажмите клавишу ВВОД.  
  
10. Тип `active`и нажмите клавишу ВВОД.  
  
11. Тип `exit`и нажмите клавишу ВВОД.  
  
12. После завершения подготовки настраиваемого образа сохраните его в корневой каталог USB-накопителя.  
  
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

 [Как мы можем вам?](https://windows.microsoft.com/windows/support)
