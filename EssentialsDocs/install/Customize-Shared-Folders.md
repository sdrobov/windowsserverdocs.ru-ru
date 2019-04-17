---
title: "Настройка общих папок"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47bc4986-14eb-4a29-9930-83a25704a3a0
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: bcdd43183512bb225dd4afa916f2782c6eb79d7e
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="customize-shared-folders"></a>Настройка общих папок

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

По умолчанию папки сервера создаются в самом большом разделе данных на диске 0. Партнеры могут изменить их местоположение и указать дополнительные папки сервера, выполнив следующие действия:  
  
1.  Используя настраиваемую конфигурацию раздела, создайте заводской образ и затем создать новый раздел реестра Storage, прежде чем использовать средство sysprep. Во время начальную настройку (IC), задача начальной настройки хранилища проверяет этот раздел реестра. Если он существует, серверные папки по умолчанию создаются в каталоге C:\ServerFolders.  
  
    #### <a name="to-create-a-new-storage-registry-key"></a>Чтобы создать новый раздел реестра Storage  
  
    1.  На сервере, переместите указатель мыши в правый верхний угол экрана, а затем нажмите кнопку **поиска**.  
  
    2.  В поле поиска введите **regedit**, а затем нажмите кнопку **Regedit** приложения.  
  
    3.  В области навигации разверните **HKEY_LOCAL_MACHINE**, разверните **программного обеспечения**, а затем разверните **Microsoft**.  
  
    4.  Щелкните правой кнопкой мыши **Windows Server**, нажмите кнопку **New**, а затем нажмите кнопку **ключ**.  
  
    5.  Имя раздела **хранилища**.  
  
    6.  В области навигации щелкните правой кнопкой мыши новый хранилища реестра ключа, нажмите кнопку **New**, а затем нажмите кнопку **значение DWORD (32-разрядная версия)**.  
  
    7.  Имя строки **CreateFoldersOnSystem**.  
  
    8.  Щелкните правой кнопкой мыши **CreateFoldersOnSystem**, а затем нажмите кнопку **изменить**. **Изменение строкового** откроется диалоговое окно.  
  
    9. Задайте значение этот новый раздел, чтобы **1**, а затем нажмите кнопку **ОК**.  
  
2.  Чтобы переместить папки в другое расположение или создать дополнительные папки, используйте сценарий PostIC.cmd. См. в следующем примере: [пример 1: Создание настраиваемой папки и перемещение папок по умолчанию в новое расположение из PostIC.cmd с помощью Windows PowerShell](Customize-Shared-Folders.md#BKMK_Example1).  
  
3.  Чтобы переместить папки в другое расположение или создать дополнительные папки, используйте пакет SDK для решений Windows Server. См. в следующем примере: [пример 2: Создание настраиваемой папки и перемещение папок с помощью пакета SDK для решений Windows Server](Customize-Shared-Folders.md#BKMK_Example2).  
  
 При необходимости партнеры могут также оставлять папки данных на диске C. Это позволяет, конечный пользователь или продавец может определить структуру папок данных на дисках с данными.  
  
###  <a name="BKMK_Example1"></a>Пример 1: Создание настраиваемой папки и перемещение папок по умолчанию в новое расположение из PostIC.cmd с помощью Windows PowerShell  
  
1.  Создайте файл PostIC.cmd для выполнения задач начальной настройки, описанных в [Создание файла PostIC.cmd для выполнения начальной настройки задач](Create-the-PostIC.cmd-File-for-Running-Post-Initial-Configuration-Tasks.md) раздела.  
  
2.  С помощью программы «Блокнот» создайте файл с именем **customizefolders.ps1** C:\Windows\Setup\Scripts папки, и вставьте следующий Windows PowerShell® команды в файл (снять соответствующие строки в зависимости от требуемого поведения).  
  
    ```  
    # Move the Documents folder to D:\ServerFolders  
    #Get-WssFolder -name Documents| Move-WssFolder - NewDrive D:\ -Force  
  
    # Check for last error. If last error is not null, exit with return code 1  
    #If ($error[0] -ne $null) { exit 1}   
  
    # Move all folders to D:\ServerFolders  
    #foreach( $folder in Get-WssFolder )  
    #{  
    #    Move-WssFolder $folder -NewDrive D:\ -Force  
    #}  
  
    # Check for last error. If last error is not null, exit with return code 1  
    #If ($error[0] -ne $null) { exit 1}   
  
    # Create a custom folder named Custom Folder  
    #Add-WssFolder -Name CustomFolder -Path D:\ServerFolders\CustomFolder -Description "Custom Folder"  
  
    # Check for last error. If last error is not null, exit with return code 1  
    #If ($error[0] -ne $null) { exit 1}   
  
    exit 0  
    ```  
  
3.  Добавьте следующую строку в файл PostIC.cmd для выполнения этого сценария.  
  
    ```  
    REM Lower the execution policy  
    "%programfiles%\Windows Server\bin\WssPowershell.exe" "Set-ExecutionPolicy RemoteSigned"  
  
    REM Execute the folder customization script  
    "%programfiles%\Windows Server\bin\WssPowershell.exe" -NoProfile -Noninteractive -command ". %windir%\setup\scripts\customizefolders.ps1;exit $LASTEXITCODE"  
    Set error_level=%ERRORLEVEL%  
  
    REM Restore the execution policy to deafult  
    "%programfiles%\Windows Server\bin\WssPowershell.exe" "Set-ExecutionPolicy Restricted"  
    Set ERRORLEVEL=%error_level%  
    ```  
  
###  <a name="BKMK_Example2"></a>Пример 2: Создание настраиваемой папки и перемещение папок с помощью пакета SDK для решений Windows Server  
 Код, который вы создаете можно скомпилирован как исполняемый файл и затем вызывается из файла PostIC.cmd или вызывать непосредственно из установленных надстройки.  
  
```  
static void Main(string[] args)  
{  
 StorageManager storageManager = new StorageManager();  
 //Connect to the StorageManager  
 storageManager.Connect();  
  
 //Move the Documents folder to D:\ServerFolders  
 Folder targetFolder = storageManager.Folders.First(folder => folder.Name == "Documents");  
  
 MoveFolderRequest moveRequest = targetFolder.GetMoveRequest(@"D:\");  
 moveRequest.MoveFolder();  
  
 //Verify operation was successful, if so print result  
 if (moveRequest.Status == OperationStatus.Succeeded)  
 {  
  Console.WriteLine("Folder {0} now located at {1}", targetFolder.Name, targetFolder.Path);  
 }  
  
 string newFolderName = "New Custom Folder";  
 string newFolderLocation = @"C:\ServerFolders\New Custom Folder";  
  
 //Create add request based with specific name and location  
 CreateFolderRequest request = storageManager.GetCreateFolderRequest(newFolderName, newFolderLocation);  
  
 //Give Guest user read only permission to folder  
 request.PermissionsByName.Add(new NamePermission("Guest", Permission.ReadOnly));  
  
 //Create the new folders  
 request.CreateFolder();  
  
 //Verify operation was successful, if so print result  
 if( request.Status == OperationStatus.Succeeded)  
 {  
  Folder newFolder = storageManager.Folders.First(folder => folder.Path == newFolderLocation);  
  
  Console.WriteLine("Folder {0} created at {1}", newFolder.Name, newFolder.Path);  
 }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)