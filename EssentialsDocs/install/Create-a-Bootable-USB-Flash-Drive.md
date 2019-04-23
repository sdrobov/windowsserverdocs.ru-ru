---
title: Создание загрузочного USB-устройства флэш-памяти
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 05/04/2018
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fe8e35c-69f9-40b3-a270-22e2402510d8
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 2716ffb7ce8f74d7c729565064de91e0598d0753
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59884685"
---
# <a name="create-a-bootable-usb-flash-drive"></a>Создание загрузочного USB-устройства флэш-памяти

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Можно создать загрузочное USB флэш-памяти для использования для развертывания Windows Server Essentials. Первым этапом является подготовка USB-устройства флэш-памяти с помощью служебной программы командной строки DiskPart. Сведения о DiskPart см. в статье [Параметры командной строки DiskPart](https://go.microsoft.com/fwlink/?LinkId=207073).  


> [!TIP]
> Чтобы создать загрузочное USB флэш-памяти для использования в восстановлении или переустановке Windows на ПК или на сервере, см. в разделе [создать диск восстановления](https://support.microsoft.com/help/4026852/windows-create-a-recovery-drive).
  
 Дополнительные сценарии, в которых вам может понадобиться создание или использование загрузочного USB-устройства флэш-памяти, см. в следующих темах:  
  
-   [Полное восстановление системы из существующей резервной копии компьютера клиента](../manage/restore-a-full-system-from-an-existing-client-computer-backup.md)  
  
-   [Восстановление или исправление сервера под управлением Windows Server Essentials](../manage/restore-or-repair-your-server-running-windows-server-essentials.md)  

  
### <a name="to-create-a-bootable-usb-flash-drive"></a>Создание загрузочного USB-устройства флэш-памяти  
  
1.  Вставьте USB-устройство флэш-памяти в работающий компьютер.  
  
2.  Откройте окно командной строки от имени администратора.  
  
3.  Введите `diskpart`.  
  
4.  В открывшемся новом окне командной строки введите `list disk`, чтобы указать номер загрузочного USB-устройства флэш-памяти или букву диска, затем нажмите клавишу ВВОД. Команда `list disk` отображает все диски компьютера. Запишите номер диска или букву диска USB-устройства флэш-памяти.  
  
5.  В командной строке введите `select disk <X>`, где X - номер диска или букву диска USB-устройства флэш-памяти, а затем нажмите клавишу ВВОД.  
  
6.  Введите `clean`и нажмите клавишу ВВОД. Эта команда удаляет все данные с USB-устройства флэш-памяти.  
  
7.  Чтобы создать новый основной раздел на USB-устройстве флэш-памяти, введите `create part pri`, и нажмите клавишу ВВОД.  
  
8.  Чтобы выбрать созданный раздел, введите `select part 1`и нажмите клавишу ВВОД.  
  
9. Чтобы отформатировать раздел, введите `format fs=ntfs quick`и нажмите клавишу ВВОД.  
  
    > [!IMPORTANT]
    >  Если серверная платформа поддерживает Единый интерфейс EFI (UEFI), следует отформатировать USB-устройство флэш-памяти в файловой системе FAT32, а в NTFS. Чтобы отформатировать раздел в файловой системе FAT32, введите `format fs=fat32 quick`и нажмите клавишу ВВОД.  
  
10. Введите `active`и нажмите клавишу ВВОД.  
  
11. Введите `exit`и нажмите клавишу ВВОД.  
  
12. После завершения подготовки настраиваемого образа сохраните его в корневом каталоге USB-устройства флэш-памяти.  
  
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

 [Как мы можем вам помочь?](https://windows.microsoft.com/windows/support)
