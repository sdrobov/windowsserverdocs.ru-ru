---
title: "Создание файла PostIC.cmd для выполнения задач после начальной настройки"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99e258bc-0695-48c9-b694-a7f3cbe2a2d0
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: f5042204cd189e3101f5e0126fd98e786a49032d
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="create-the-posticcmd-file-for-running-post-initial-configuration-tasks"></a>Создание файла PostIC.cmd для выполнения задач после начальной настройки

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Можно добавить после начальной настройки, напишите собственный код, а затем вызвать этот код из файла сценария с именем PostIC.cmd. При использовании файла PostIC.cmd, необходимо соблюдать следующие рекомендации:  
  
-   Код настройки должны запускаться в автоматическом режиме (не может отобразить пользовательский интерфейс).  
  
-   Код настройки не может инициировать перезагрузки сервера. В качестве последней задачи начальной настройки будет перезапустить сервер.  
  
-   Код настройки необходимо выполнить в течение трех минут или меньше.  
  
 Определите файл PostIC.cmd, чтобы возвращать значение 0, если код выполняется успешно. При возвращении другого значения операционной системы ищет файл с именем [SetupFailure.cmd](Create-the-PostIC.cmd-File-for-Running-Post-Initial-Configuration-Tasks.md#BKMK_SetupFailure), который содержит кода, который должен выполняться, если не удается выполнить код в файле PostIC.cmd. Файл PostIC.cmd и SetupFailure.cmd файл должен быть размещена C:\Windows\Setup\Scripts.  
  
#### <a name="to-define-post-initial-configuration-customizations"></a>Чтобы определить дополнительные параметры после начальной настройки  
  
1.  Напишете код, который вызывается из сценария PostIC.cmd.  
  
2.  С помощью блокнота, создайте файл с именем PostIC.cmd и добавьте вызов код, который вы создали в шаге 1. Убедитесь, что ваш код возвращает значение успеха.  
  
3.  Сохраните PostIC.cmd в C:\Windows\Setup\Scripts.  
  
4.  (Необязательно) Создайте файл SetupFailure.cmd, который возвращает PostIC.cmd, отличное от 0, которая выполняет код.  
  
###  <a name="BKMK_SetupFailure"></a>SetupFailure.cmd  
 Уведомления о проблем в ходе начальной настройки можно предоставить с помощью SetupFailure.cmd. Файл SetupFailure.cmd содержит код, который требуется выполнить при возникновении проблем. Файл SetupFailure.cmd помещается в C:\Windows\Setup\Scripts и выполняется при возникновении либо проблемы с задачей установки или при файла PostIC.cmd возвращает значение, отличное от 0.  
  
##### <a name="to-define-notifications"></a>Для определения уведомления  
  
1.  Напишете код, который вызывается из сценария SetupFailure.cmd.  
  
2.  С помощью блокнота, создайте файл с именем SetupFailure.cmd и добавьте вызов код, который вы создали в шаге 1. Убедитесь, что ваш код возвращает значение успеха.  
  
3.  Сохраните SetupFailure.cmd в C:\Windows\Setup\Scripts.  
  
## <a name="see-also"></a>См. также:  
 [Начало работы с ADK Windows Server Essentials](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)