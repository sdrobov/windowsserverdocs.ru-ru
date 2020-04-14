---
title: Добавление информации о зарегистрированном партнере, заключившем партнерское соглашение об использовании интернет-служб Майкрософт
description: Описание использования Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: 9bd191d6-ecc5-4230-a88e-f3fc281cb956
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 7a297ed077f4c1457bd1e59fc0ea22feedd5de0d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80817589"
---
# <a name="add-microsoft-online-service-partner-agreement-partner-of-record-information"></a>Добавление информации о зарегистрированном партнере, заключившем партнерское соглашение об использовании интернет-служб Майкрософт

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

##  <a name="BKMK_3rdLevelDomanNames"></a>   
 Если вы являетесь партнером Microsoft Online Service Partner Agreement (МОСПА) для Office 365, чтобы обеспечить правильную компенсацию при порождении запроса на подписку из Windows Server Essentials с помощью модуля интеграции Office 365, необходимо создать раздел реестра, содержащий идентификатор партнера по записи (пор ID). Указанная ниже информация считывается и передается поставщику услуг через URL-адреса регистрации Office 365.  
  
-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO  
  
-   Тип = строковый параметр  
  
-   Имя раздела = Partner  
  
-   Значение = xxxxx, где xxxxx - POR ID партнера  
  
#### <a name="to-add-the-por-id-key-to-the-registry"></a>Добавление раздела POR ID в реестр  
  
1.  На компьютере-образце нажмите кнопку **Пуск**, введите команду **regedit** и нажмите клавишу ВВОД.  
  
2.  В левой области последовательно разверните узлы **HKEY_LOCAL_MACHINE**, **SOFTWARE**, **Microsoft** и **Windows Server**.  
  
3.  Щелкните правой кнопкой мыши узел **Windows Server**, выберите команду **Создать** и щелкните пункт **Раздел**.  
  
4.  В качестве имени раздела введите **MSO**.  
  
5.  Щелкните правой кнопкой мыши созданный раздел и выберите пункт **Строковый параметр**.  
  
6.  В качестве имени строки введите **Partner** и нажмите клавишу ВВОД.  
  
7.  Щелкните правой кнопкой мыши строку **Partner** в правой области и выберите команду **Изменить**.  
  
8.  Введите идентификатор POR ID в текстовое поле **Значение** и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  

 [Создание и Настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа к развертыванию](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Создание и Настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа к развертыванию](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

