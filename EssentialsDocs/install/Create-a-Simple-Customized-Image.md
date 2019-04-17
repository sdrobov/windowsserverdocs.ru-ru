---
title: "Создание простого настроенного образа"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 29f9a09f-e4e8-476d-ada1-ab9202a670d7
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: e18ff5ded94127449072d28d00b98e17dbe63c3a
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="create-a-simple-customized-image"></a>Создание простого настроенного образа

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Можно использовать следующую процедуру для создания простого настраиваемого образа:  
  
#### <a name="to-create-the-image"></a>Для создания образа  
  
1.  После установки сервера на первой странице первоначальную настройку, нажмите клавиши Shift + F10, чтобы открылось окно cmd..  
  
2.  Создайте файл SkipIC.txt в корне системного диска.  
  
3.  Перезапустите сервер.  
  
4.  Запустите сервер с помощью USB-накопитель флэш-памяти или DVD-диска, содержащего файл unattend.xml. Сведения о создании загрузочного USB-накопителя см. в разделе [создать загрузочный флэш-накопитель USB](Create-a-Bootable-USB-Flash-Drive.md).  
  
5.  Добавление фирменной символики на панель мониторинга. Дополнительные сведения о добавлении фирменной символики см. в разделе [Добавление фирменной символики на панели мониторинга, удаленного веб-доступа и запуска](Add-Branding-to-the-Dashboard--Remote-Web-Access--and-Launchpad.md).  
  
6.  Создайте файл OOBE.xml для отображения пользовательской информации, такой как название компании, эмблема и лицензионное соглашение. Дополнительные сведения о файле OOBE.xml см. в разделе [Создание файла Oobe.xml, включая эмблему и лицензионное соглашение](Create-the-Oobe.xml-File-Including-Logo-and-EULA.md).  
  
7.  Измените имя сервера по умолчанию, если не определено в unattend.xml.  
  
8.  По умолчанию имя сервера будет случайные строки. Измените имя сервера на другую строку (например, ContosoServer) и уведомите своего клиента о новом имени сервера.  
  
9. Подготовка образа для развертывания, как описано в [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md).  
  
## <a name="see-also"></a>См. также:  
 [Начало работы с ADK Windows Server Essentials](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)