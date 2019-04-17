---
title: "Добавление информации зарегистрированного партнера соглашение об партнеров веб-службы Майкрософт"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9bd191d6-ecc5-4230-a88e-f3fc281cb956
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 39ce43228cd7392bcc86de4a410c52676ce15047
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="add-microsoft-online-service-partner-agreement-partner-of-record-information"></a>Добавление информации зарегистрированного партнера соглашение об партнеров веб-службы Майкрософт

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

##  <a name="BKMK_3rdLevelDomanNames"></a>   
 Если вы являетесь партнером Microsoft Online соглашения Service (MOSPA) для Office 365, чтобы убедиться, что вы получение надлежащей компенсации при поступлении запроса от Windows Server Essentials через модуль интеграции Office 365, необходимо создать раздел реестра, содержащий ваш идентификатор зарегистрированного партнера (POR ID). Следующие сведения прочитать и передается поставщику услуг по URL-адресам подписки Office 365.  
  
-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO  
  
-   Тип = строковое значение  
  
-   Имя ключа = партнеров  
  
-   Значение = xxxxx, где xxxxx — идентификатор POR  
  
#### <a name="to-add-the-por-id-key-to-the-registry"></a>Чтобы добавить раздел POR ID в реестр  
  
1.  На компьютере-образце нажмите кнопку **запустить**, тип **regedit**, и нажмите клавишу ВВОД.  
  
2.  В левой области разверните **HKEY_LOCAL_MACHINE**, разверните **программного обеспечения**, разверните **Microsoft**и затем разверните **Windows Server**.  
  
3.  Щелкните правой кнопкой мыши **Windows Server**, наведите курсор на **New**, а затем нажмите кнопку **ключ**.  
  
4.  Тип **MSO** для имени ключа.  
  
5.  Щелкните правой кнопкой мыши только что создан, а затем нажмите кнопку **строковое значение**.  
  
6.  Тип **партнеров** имя строки, а затем нажмите клавишу ВВОД.  
  
7.  Щелкните правой кнопкой мыши новый **партнеров** строка в правой области и нажмите кнопку **изменить**.  
  
8.  Введите свой идентификатор POR в **значение** текстовое поле, а затем нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  

 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

