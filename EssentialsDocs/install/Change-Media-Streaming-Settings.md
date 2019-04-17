---
title: "Изменение параметров потоковой передачи мультимедиа"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dec690d2-f80c-4b09-99d6-3bba41331972
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: d34d60e792fcda4d71a4509fe3d1b95fc6e74d0e
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="change-media-streaming-settings"></a>Изменение параметров потоковой передачи мультимедиа

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Для изменения параметров потоковой передачи мультимедиа предусмотрено несколько вариантов. Доступны следующие параметры:  
  
-   [Скрыть удаленной потоковой передачи надстройки мультимедиа](Change-Media-Streaming-Settings.md#BKMK_DisableRemote)  
  
-   [Задайте имя библиотеки мультимедиа](Change-Media-Streaming-Settings.md#BKMK_LibraryName)  
  
-   [Задайте качество потокового видео](Change-Media-Streaming-Settings.md#BKMK_StreamingQuality)  
  
-   [Чтобы включить или отключить потоковую передачу мультимедиа](Change-Media-Streaming-Settings.md#BKMK_Program)  
  
##  <a name="BKMK_DisableRemote"></a>Скрыть удаленной потоковой передачи надстройки мультимедиа  
 Можно скрыть удаленная потоковая надстройки путем добавления записи в реестре.  
  
#### <a name="to-hide-the-remote-media-streaming-add-in"></a>Чтобы скрыть удаленной потоковой передачи надстройки мультимедиа  
  
1.  На сервере, переместите указатель мыши в правый верхний угол экрана, а затем нажмите кнопку **поиска**.  
  
2.  В **поиска** введите **regedit**, а затем нажмите кнопку **Regedit** приложения.  
  
3.  В левой области разверните вплоть до следующей записи реестра:  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\RemoteAccess\DisabledAddIns**  
  
4.  Щелкните правой кнопкой мыши **DisabledAddIns**, наведите курсор на **New**, а затем нажмите кнопку **значение DWORD**.  
  
5.  Новое значение, введите **497796c6-9cc7-43be-aa26-4e6b5695370d**, который — идентификатор для удаленной потоковой передачи надстройки мультимедиа и нажмите клавишу **ввод**.  
  
6.  Щелкните правой кнопкой мыши значение, а затем нажмите кнопку **изменить**.  
  
7.  Тип **1** значение, а затем нажмите кнопку **ОК**.  
  
##  <a name="BKMK_LibraryName"></a>Задайте имя библиотеки мультимедиа  
 Для присвоения имени библиотеке мультимедиа, можно использовать класс в пакет SDK для решений Windows Server. Чтобы задать имя библиотеки мультимедиа, можно использовать **SetMediaLibraryName** метод **MediaStreamingManager** класса **Microsoft.WindowsServerSolutions.MediaStreaming** пространства имен. Приведенный ниже показано, как задать имя библиотеки мультимедиа:  
  
```c#  
  
MediaStreamingManager mediaStreamingManager = new MediaStreamingManager();  
string mediaLibraryName = Guid.NewGuid().ToString("B");   
mediaStreamingManager.SetMediaLibraryName(mediaLibraryName);  
  
```  
  
 Дополнительные сведения см. в разделе [пакет SDK для решений Windows Server](https://go.microsoft.com/fwlink/?LinkID=248648).  
  
##  <a name="BKMK_StreamingQuality"></a>Задайте качество потокового видео  
 Путем получения оценки ЦП средства WinSAT и создания и установки XML-файл, содержащий сведения об оценке WinSAT качество потоковой передачи видео задается. Если XML-файл, содержащий сведения об оценке WinSAT устанавливается раньше выполнения начальной настройки, пользовательский интерфейс для задания качества видео не будут отображаться для клиента. Дополнительные сведения см. в разделе [Установка на сервере системы оценки WinSAT](Set-the-WinSAT-Score-on-the-Server.md).  
  
##  <a name="BKMK_Program"></a>Чтобы включить или отключить потоковую передачу мультимедиа  
 Для программного включения или отключения потоковой передачи мультимедиа, можно использовать класс в пакет SDK для решений Windows Server. Чтобы включить или отключить потоковую передачу мультимедиа, можно использовать **SetMediaStreamingEnabled** метод **MediaStreamingManager** класса **Microsoft.WindowsServerSolutions.MediaStreaming** пространства имен. В следующем примере кода показано, как Включение потоковой передачи мультимедиа:  
  
```c#  
  
MediaStreamingManager mediaStreamingManager = new MediaStreamingManager();  
mediaStreamingManager.SetMediaStreamingEnabled(true);  
  
```  
  
 В следующем примере кода показано, как отключить потоковой передачи мультимедиа:  
  
```c#  
  
MediaStreamingManager mediaStreamingManager = new MediaStreamingManager();  
mediaStreamingManager.SetMediaStreamingEnabled(false);  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)