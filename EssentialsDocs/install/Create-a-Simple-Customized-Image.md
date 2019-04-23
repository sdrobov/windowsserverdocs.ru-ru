---
title: Создание простого настроенного образа
description: Описывает способ использования Windows Server Essentials
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59884615"
---
# <a name="create-a-simple-customized-image"></a>Создание простого настроенного образа

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Приведенную ниже процедуру можно использовать для создания простого настраиваемого образа.  
  
#### <a name="to-create-the-image"></a>Создание образа  
  
1.  После установки сервера на первой странице раздела "Первоначальная настройка" нажмите комбинацию клавиш Shift+F10, чтобы открылось окно cmd.  
  
2.  Создайте файл SkipIC.txt в корне системного диска.  
  
3.  Перезагрузите сервер.  
  
4.  Запустите сервер с помощью загрузочного USB-устройства флэш-памяти на DVD-диска, содержащего файл unattend.xml. Дополнительные сведения о создании загрузочного USB-накопителя см. в статье [Create a Bootable USB Flash Drive](Create-a-Bootable-USB-Flash-Drive.md).  
  
5.  Добавление фирменной символики на панель администрирования. Дополнительные сведения о добавлении доменов см. в разделе [Add Branding to the Dashboard, Remote Web Access, and Launchpad](Add-Branding-to-the-Dashboard--Remote-Web-Access--and-Launchpad.md).  
  
6.  Создайте файл OOBE.xml для отображения пользовательской информации, такой как название компании, эмблема и лицензионное соглашение. Дополнительные сведения о файле OOBE.xml см. в разделе [Create the Oobe.xml File Including Logo and EULA](Create-the-Oobe.xml-File-Including-Logo-and-EULA.md).  
  
7.  Измените имя сервера по умолчанию, если это не определено в файле unattend.xml.  
  
8.  В качестве имени сервера используется случайно выбранная строка. Измените имя сервера на другую строку (например, ContosoServer) и уведомите своего клиента о новом имени сервера.  
  
9. Подготовьте образ для развертывания, как описано в статье [Preparing the Image for Deployment](Preparing-the-Image-for-Deployment.md).  
  
## <a name="see-also"></a>См. также  
 [Начало работы с ADK Windows Server Essentials](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)