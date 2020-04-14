---
title: Создание простого настроенного образа
description: Описание использования Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: 29f9a09f-e4e8-476d-ada1-ab9202a670d7
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 1c3c47a9cab8e08768cef265ff823d383eda4a74
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80818357"
---
# <a name="create-a-simple-customized-image"></a>Создание простого настроенного образа

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Приведенную ниже процедуру можно использовать для создания простого настраиваемого образа.  
  
#### <a name="to-create-the-image"></a>Создание образа  
  
1.  После установки сервера на первой странице раздела "Первоначальная настройка" нажмите комбинацию клавиш Shift+F10, чтобы открылось окно cmd.  
  
2.  Создайте файл SkipIC.txt в корне системного диска.  
  
3.  Перезапустите сервер.  
  
4.  Запустите сервер с помощью загрузочного USB-устройства флэш-памяти на DVD-диска, содержащего файл unattend.xml. Дополнительные сведения о создании загрузочного USB-устройства флэш-памяти см. в статье [Создание загрузочного USB-устройства флэш-памяти](Create-a-Bootable-USB-Flash-Drive.md).  
  
5.  Добавление фирменной символики на панель администрирования. Дополнительные сведения о добавлении фирменной символики см. в статье [Добавление фирменной символики на панель администрирования, веб-сайт удаленного доступа и панель запуска](Add-Branding-to-the-Dashboard--Remote-Web-Access--and-Launchpad.md).  
  
6.  Создайте файл OOBE.xml для отображения пользовательской информации, такой как название компании, эмблема и лицензионное соглашение. Дополнительные сведения о файле OOBE.xml см. в разделе [Create the Oobe.xml File Including Logo and EULA](Create-the-Oobe.xml-File-Including-Logo-and-EULA.md).  
  
7.  Измените имя сервера по умолчанию, если это не определено в файле unattend.xml.  
  
8.  В качестве имени сервера используется случайно выбранная строка. Измените имя сервера на другую строку (например, ContosoServer) и уведомите своего клиента о новом имени сервера.  
  
9. Подготовьте образ для развертывания как описано в статье [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md).  
  
## <a name="see-also"></a>См. также  
 [Начало работы с Windows Server ESSENTIALS ADK](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и Настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа к развертыванию](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)