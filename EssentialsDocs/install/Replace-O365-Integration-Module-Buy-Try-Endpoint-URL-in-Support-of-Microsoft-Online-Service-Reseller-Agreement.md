---
title: Замена URL-адресов конечных точек при покупке или ознакомлении для модуля интеграции O365 в рамках поддержки по соглашению с торговым посредником интернет-служб Майкрософт
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9860a6b9-baea-4bf0-9a9f-6f1a288f996e
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: b690cedd2f692cc6d11af6e05dd0cd4b4ea5a1d6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59833105"
---
# <a name="replace-o365-integration-module-buy-try-endpoint-url-in-support-of-microsoft-online-service-reseller-agreement"></a>Замена URL-адресов конечных точек при покупке или ознакомлении для модуля интеграции O365 в рамках поддержки по соглашению с торговым посредником интернет-служб Майкрософт

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

##  <a name="BKMK_O365"></a>   
 Если вы являетесь партнером Microsoft Online Service торгового посредника соглашения (MOSRA), чтобы убедиться, что на вашем портале обрабатываются транзакций по регистрации пользователей необходимо будет заменить URL-адреса конечной точки, используемые модулем интеграции Windows Server Essentials с Office 365.  
  
 Модуль интеграции использует следующие четыре URL-адреса конечных точек.  
  
1.  Конечная точка покупки подписки Office 365 Enterprise.  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\  
  
    -   Тип = REG-SZ  
  
    -   Имя раздела = MOSRASTDBUY  
  
    -   Значение = *xxxxx*, где xxxxx - URL-адрес покупки подписки Enterprise. Например, значение = http://syndicatepartner.office365.com/enterprisebuy.html  
  
2.  Конечная точка ознакомительной подписки Office 365 Enterprise.  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\  
  
    -   Тип = REG-SZ  
  
    -   Имя раздела = MOSRASTDTRY  
  
    -   Значение = *xxxxx*, где xxxxx - URL-адрес покупки подписки Enterprise. Например, значение = http://syndicatepartner.office365.com/enterprisetry.html  
  
3.  Конечная точка покупки подписки Office 365 Small Business Premium.  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\  
  
    -   Тип = REG-SZ  
  
    -   Имя раздела = MOSRALITEBUY  
  
    -   Значение = *xxxxx*, где xxxxx - URL-адрес покупки подписки Enterprise. Например, значение = http://syndicatepartner.office365.com/smallbizbuy.html  
  
4.  Office 365 Small Business Premium конечная точка ознакомительной подписки.  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\  
  
    -   Тип = REG-SZ  
  
    -   Имя раздела = MOSRALITETRY  
  
    -   Значение = *xxxxx*, где xxxxx - URL-адрес покупки подписки Enterprise. Например, значение = http://syndicatepartner.office365.com/smallbiztry.html  
  
#### <a name="to-add-an-endpoint-url-key-to-the-registry"></a>Добавление раздела реестра со значением URL-адреса конечной точки  
  
1.  На компьютере-образце нажмите кнопку **Пуск**, введите команду **regedit** и нажмите клавишу ВВОД.  
  
2.  В левой области разверните разделы **HKEY_LOCAL_MACHINE**, **SOFTWARE**, **Microsoft**, **Windows Server** и **MSO**.  
  
3.  Если раздел MSO не существует, щелкните правой кнопкой мыши **Windows Server**, выберите пункт **Создать**, щелкните **Раздел**, а затем введите **MSO** в качестве имени раздела.  
  
4.  Щелкните правой кнопкой мыши раздел MSO и выберите пункт **Строковый параметр**. Введите одно из приведенных ниже имен конечной точки в качестве имени строки.  
  
    -   MOSRASTDBUY  
  
    -   MOSRASTDTRY  
  
    -   MOSRALITEBUY  
  
    -   MOSRALITETRY  
  
5.  Щелкните правой кнопкой мыши новую строку в правой области и выберите команду **Изменить**.  
  
6.  Введите URL-адрес конечной точки в текстовое поле **Значение** и нажмите кнопку **OK**.  
  
7.  Повторите шаги 4-6 для каждого имени строки из указанных в шаге 4.  
  
## <a name="see-also"></a>См. также  

 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md) [Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

