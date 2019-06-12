---
title: Шаг 6 Проверка подключения DirectAccess из подсети Homenet
description: Этот раздел входит руководство по лаборатории тестирования — продемонстрировать DirectAccess с проверкой подлинности OTP и RSA SecurID для Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9b77cfd-8dd4-476b-a118-f3d6bf59e7b1
ms.author: pashort
author: shortpatti
ms.openlocfilehash: fe3014b8b37fab35532f3ecf833188fda9e8b744
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66446639"
---
# <a name="step-6-test-directaccess-connectivity-from-the-homenet-subnet"></a>Шаг 6 Проверка подключения DirectAccess из подсети Homenet

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Развертывания DirectAccess одноразовых паролей (OTP) уже выполнено, и вы сможете проверить возможность подключения из подсети Homenet.  
  
### <a name="to-test-otp-functionality-from-the-homenet-subnet-on-client1"></a>Чтобы проверить функцию OTP из подсети Homenet на CLIENT1  
  
1. На компьютере CLIENT1, убедитесь, что вы вошли как **User1**.  
  
2. На **запустить** введите**powershell.exe**, щелкните правой кнопкой мыши **powershell**, нажмите кнопку **Дополнительно**, а затем нажмите кнопку **запуска от имени администратора**. Если появится диалоговое окно **контроля учетных записей**, подтвердите, что отображаемое в нем действие именно то, которое требуется, и нажмите кнопку **Да**.  
  
3. В окне Windows PowerShell введите **gpupdate/force**, и нажмите клавишу ВВОД.  
  
4. Отключите CLIENT1 от подсети Corpnet и подключить его к подсети Homenet.  
  
5. На компьютере CLIENT1 откройте Internet Explorer и в адресной строке введите **https://app1.corp.contoso.com/** и нажмите клавишу ВВОД. Нажмите клавишу F5.  
  
   Не следует открывать сайт.  
  
6. На **запустить** введите**RSA**и нажмите кнопку **токена RSA SecurID**.  
  
7. Подождите, пока токен RSA SecurID изменяет одноразовый пароль и нажмите кнопку **копирования**.  
  
8. В области уведомлений щелкните значок **Сетевые подключения** , чтобы получить доступ к диспетчеру мультимедиа DA.  
  
9. Нажмите кнопку **подключения DirectAccess Contoso**и нажмите кнопку **Продолжить**.  
  
10. Нажмите элемент управления + Alt + Delete и выберите **одноразовых паролей (OTP)** плитку.  
  
11. Вставьте скопированные ранее цифра восемь последовательно и нажмите кнопку **ОК**. Дождитесь завершения операции проверки подлинности. Подключение к рабочему месту DirectAccess состояние теперь будет **подключено**.  
  
12. В Internet Explorer, в адресной строке введите **https://app1.corp.contoso.com/** и нажмите клавишу ВВОД. Нажмите клавишу F5. Появится веб-сайт IIS на APP1 по умолчанию.  
  
13. В адресной строке Internet Explorer введите **https://app2.corp.contoso.com/** и нажмите клавишу ВВОД. Нажмите клавишу F5. Вы увидите веб-сайт по умолчанию IIS на APP2.  
  
14. На **запустить** введите<strong>\\\app1\files</strong>, и нажмите клавишу ВВОД.  
  
15. В **файлы** окно общей папки, дважды щелкните **Example.txt** файл. Вы увидите содержимое этого файла.  
  
16. На **запустить** введите<strong>\\\app2\files</strong>, и нажмите клавишу ВВОД.  
  
17. В **файлы** окно общей папки, дважды щелкните **текстовый документ.txt** файл. Вы увидите содержимое файла текстовый документ.txt.  
  


