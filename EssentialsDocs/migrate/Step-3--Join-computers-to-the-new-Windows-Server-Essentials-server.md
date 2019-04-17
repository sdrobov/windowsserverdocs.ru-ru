---
title: "Шаг 3: Присоединение компьютеров к новому серверу Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a0e07d1a-8409-429b-87d7-0f4a7e14d668
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: f71ac280e2de0b7d945f2d979fe52d173f7c3323
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="step-3-join-computers-to-the-new-windows-server-essentials-server"></a>Шаг 3: Присоединение компьютеров к новому серверу Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Следующим шагом в процессе миграции является подключение клиентских компьютеров к новому серверу с ОС Windows Server Essentials.  
  
> [!NOTE]
>  Для компьютеров, работающих под управлением Windows XP или операционных систем Windows Vista этот шаг можно пропустить. Программное обеспечение Windows Server Connector не поддерживает компьютеры под управлением Windows XP или Windows Vista.  
  
 Прежде чем присоединить клиентский компьютер к новому серверу Windows Server Essentials, необходимо отключить его от исходного сервера путем удаления программного обеспечения Windows Server Connector на клиентском компьютере.  
  
### <a name="to-uninstall-windows-server-connector-on-a-client-computer"></a>Удаление Windows Server Connector на клиентском компьютере  
  
1.  На клиентском компьютере откройте панель управления, а затем откройте **программы и компоненты**.  
  
2.  В списке программ щелкните правой кнопкой мыши приложение Connector, на котором выполняется на компьютере.  
  
    > [!NOTE]
    >  Приложения Connector может применяться **Windows Small Business Server 2011 Essentials Connector**, или **Windows Server Essentials Connector**в зависимости от версии Windows Server Essentials, был подключен клиентский компьютер.  
  
3.  Нажмите кнопку **удаление**.  
  
### <a name="to-reconnect-a-client-computer-to-the-server"></a>Для повторного подключения клиентского компьютера к серверу  
  
1.  Войдите в компьютер, который вы хотите подключиться к серверу.  
  
    > [!NOTE]
    >  Если на компьютере настроено несколько учетных записей пользователей, войдите с помощью учетной записи пользователя, чьи документы, изображения и личные настройки которой требуется сохранить после подключения компьютера к серверу.  
  
2.  Откройте веб-браузер, например Internet Explorer.  
  
3.  В адресной строке введите **http://<servername\>/Connect**, и нажмите клавишу ВВОД.  
  
4.  Следуйте инструкциям на экране, чтобы присоединить клиентский компьютер к новому серверу Windows Server Essentials.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Вы присоединили клиентских компьютеров к новому серверу с ОС Windows Server Essentials. Теперь перейдите к [шаг 4: перенос параметров и данных на целевой сервер для миграции Windows Server Essentials](Step-4--Move-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  
  

Для просмотра всех шагов см [переход на Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).

