---
title: Шаг 3. Присоединение компьютеров к новому серверу Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59861875"
---
# <a name="step-3-join-computers-to-the-new-windows-server-essentials-server"></a>Шаг 3. Присоединение компьютеров к новому серверу Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Следующий шаг в процессе миграции является подключение клиентских компьютеров к новому серверу под управлением Windows Server Essentials.  
  
> [!NOTE]
>  Для компьютеров с ОС Windows XP или Windows Vista этот шаг можно пропустить. Программное обеспечение Windows Server Connector не поддерживает компьютеры, на которых выполняется ОС Windows XP или Windows Vista.  
  
 Прежде чем можно присоединить клиентский компьютер к новому серверу Windows Server Essentials, необходимо отключить его от исходного сервера путем удаления программного обеспечения Windows Server Connector на клиентском компьютере.  
  
### <a name="to-uninstall-windows-server-connector-on-a-client-computer"></a>Удаление Windows Server Connector на клиентском компьютере  
  
1.  На клиентском компьютере откройте панель управления, а затем **Программы и компоненты**.  
  
2.  В списке программ щелкните правой кнопкой мыши приложение Connector, выполняемое на вашем компьютере.  
  
    > [!NOTE]
    >  Приложения Connector может применяться **Windows Small Business Server 2011 Essentials Connector**, или **Windows Server Essentials Connector**, в зависимости от версии Windows Server Essentials был подключен клиентский компьютер.  
  
3.  Нажмите кнопку **Удалить**.  
  
### <a name="to-reconnect-a-client-computer-to-the-server"></a>Повторное подключение клиентского компьютера к серверу  
  
1.  Войдите на компьютер, который требуется подключить к серверу.  
  
    > [!NOTE]
    >  Если на компьютере настроено несколько учетных записей пользователей, войдите в систему с той учетной записью, документы, изображения и личные настройки которой требуется сохранить после подключения этого компьютера к серверу.  
  
2.  Откройте браузер, например Internet Explorer.  
  
3.  В адресной строке введите **http://<servername\>/Connect**, и нажмите клавишу ВВОД.  
  
4.  Следуйте указаниям на экране, чтобы присоединить клиентский компьютер к новому серверу Windows Server Essentials.  
  
## <a name="next-steps"></a>Следующие шаги  
 Вы присоединили клиентских компьютеров к новому серверу с ОС Windows Server Essentials. Теперь перейдите к [Step 4: Перенос параметров и данных на целевой сервер для миграции Windows Server Essentials](Step-4--Move-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  
  

Чтобы просмотреть все действия, см. в разделе [миграции на Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).

