---
title: "Замена Office 365 интеграции модуля попробуйте купить Endpoint URL-адресов для поддержки соглашения торгового посредника интерактивных служб Майкрософт"
description: "Описывается, как использовать Windows Server Essentials"
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
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="replace-o365-integration-module-buy-try-endpoint-url-in-support-of-microsoft-online-service-reseller-agreement"></a>Замена Office 365 интеграции модуля попробуйте купить Endpoint URL-адресов для поддержки соглашения торгового посредника интерактивных служб Майкрософт

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

##  <a name="BKMK_O365"></a>   
 Если используется Microsoft Online службы торгового посредника соглашения (mosra), для обеспечения обработки транзакций по регистрации пользователей через ваш портал, необходимо будет заменить URL-адреса конечной точки, используемые модулем интеграции Windows Server Essentials Office 365.  
  
 Модуль интеграции использует следующие четыре endpoint URL-адреса:  
  
1.  Конечная точка покупки подписки Office 365 Enterprise.  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\  
  
    -   Тип = REG SZ  
  
    -   Имя ключа = MOSRASTDBUY  
  
    -   Значение = *xxxxx*, где xxxxx — URL-адрес вашего предприятия покупки подписки. Например, значение = http://syndicatepartner.office365.com/enterprisebuy.html  
  
2.  Office 365 корпоративный конечная точка пробной подписки.  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\  
  
    -   Тип = REG SZ  
  
    -   Имя ключа = MOSRASTDTRY  
  
    -   Значение = *xxxxx*, где xxxxx — URL-адрес вашего предприятия покупки подписки. Например, значение = http://syndicatepartner.office365.com/enterprisetry.html  
  
3.  Конечная точка покупки подписки Office 365 малого бизнеса расширенный.  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\  
  
    -   Тип = REG SZ  
  
    -   Имя ключа = MOSRALITEBUY  
  
    -   Значение = *xxxxx*, где xxxxx — URL-адрес вашего предприятия покупки подписки. Например, значение = http://syndicatepartner.office365.com/smallbizbuy.html  
  
4.  Office 365 малого бизнеса расширенный конечная точка пробной подписки.  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO\  
  
    -   Тип = REG SZ  
  
    -   Имя ключа = MOSRALITETRY  
  
    -   Значение = *xxxxx*, где xxxxx — URL-адрес вашего предприятия покупки подписки. Например, значение = http://syndicatepartner.office365.com/smallbiztry.html  
  
#### <a name="to-add-an-endpoint-url-key-to-the-registry"></a>Чтобы добавить ключ URL-адрес конечной точки в реестр  
  
1.  На компьютере-образце нажмите кнопку **запустить**, тип **regedit**, и нажмите клавишу ВВОД.  
  
2.  В левой области разверните **HKEY_LOCAL_MACHINE**, разверните **программного обеспечения**, разверните **Microsoft**, разверните **Windows Server**и затем разверните **MSO**.  
  
3.  Если раздел MSO не существует, щелкните правой кнопкой мыши **Windows Server**, наведите курсор на **New**, нажмите кнопку **ключ**и затем введите **MSO** для имени ключа.  
  
4.  Щелкните правой кнопкой мыши раздел MSO, а затем нажмите кнопку **строковое значение**. Введите одно из следующих имен строку конечной точки для имя строки:  
  
    -   MOSRASTDBUY  
  
    -   MOSRASTDTRY  
  
    -   MOSRALITEBUY  
  
    -   MOSRALITETRY  
  
5.  Щелкните правой кнопкой мыши новую строку в области справа, а затем нажмите кнопку **изменить**.  
  
6.  Введите новый URL-адрес конечной точки в **значение** текстовое поле, а затем нажмите кнопку **ОК**.  
  
7.  Повторите шаги 4 – 6 для каждого имени строки, перечисленные в шаге 4.  
  
## <a name="see-also"></a>См. также:  

 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)[Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

