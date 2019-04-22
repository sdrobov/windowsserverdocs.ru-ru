---
title: Шаг 2. Установка Windows Server Essentials в качестве нового репликата контроллера домена
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c7ccfc34-63fd-436b-a1cd-e05810f60bfe
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 757012b7d1a57a001e3b55cdc0604b63852a3d3c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59816465"
---
# <a name="step-2-install-windows-server-essentials-as-a-new-replica-domain-controller"></a>Шаг 2. Установка Windows Server Essentials в качестве нового репликата контроллера домена

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

В этом разделе описывается установка Windows Server Essentials и Windows Server 2012 R2 Standard (с включенной ролью Windows Server Essentials Experience) в качестве контроллера домена.  
  
 Для среды максимум с 25 пользователями и 50 устройств можно выполнить действия, описанные в этом руководстве для миграции Windows Server Essentials из предыдущих версий Windows SBS. Для среды до 100 пользователей и 200 устройств можно выполнить то же руководство для миграции на выпуски Standard и Datacenter, Windows Server 2012 R2 с установленной ролью Windows Server Essentials Experience. В этом документе рассматриваются оба сценария.  
  
> [!IMPORTANT]
>  Если выполняется миграция на Windows Server Essentials, следующее сообщение об ошибке добавляется в журнал событий каждый день в течение 21-дневного льготного периода, пока вы не удалите исходный сервер из сети. По истечении 21-дневного льготного периода работа исходного сервера завершается. <br> **Проверка роли FSMO обнаружила в вашей среде, не соответствует требованиям политики лицензирования условие. Сервер управления должен выполнять роли Active Directory первичного контроллера домена и хозяина именования доменов. Перенесите роли Active Directory на сервер управления. Этот сервер будет автоматически завершена, если проблема не будет устранена в течение 21 дня с момента первого обнаружения этого условия**.   
  
#### <a name="install-windows-server-essentials-or-windows-server-2012-r2-standard-on-the-destination-server"></a>Установка Windows Server Essentials или Windows Server 2012 R2 Standard на целевом сервере  
  
1.  Установка Windows Server Essentials или Windows Server 2012 R2 Standard с включенной, следуя инструкциям в ролью Windows Server Essentials Experience [Установка и настройка Windows Server Essentials](../install/Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).  
  
    > [!NOTE]
    >  Если будет запущен мастер настройки Windows Server Essentials, отмените его.  
  
2.  Перенесите роли FSMO с исходного сервера.  
  
    > [!NOTE]
    >  Если Windows Server Essentials является единственным контроллером домена в домене, то роль FSMO автоматически перемещается на сервер под управлением Windows Server Essentials при понижении уровня исходного сервера.  
  
3.  Откройте диспетчер серверов и запустите мастер добавления ролей и компонентов.  
  
4.  Если роль Windows Server Essentials Experience не установлена, добавьте ее.  
  
5.  После установки роли Windows Server Essentials Experience в области уведомлений появляется задача "Настройка Windows Server Essentials". Для запуска мастера настройки Windows Server Essentials щелкните эту задачу.  
  
6.  Следуйте инструкциям для завершения процесса настройки Windows Server Essentials. Перед запуском мастера выполните следующие действия.  
  
    -   При необходимости, измените имя сервера, так как после завершения работы мастера настройки Essentials Windows Server изменить имя будет невозможно.  
  
    -   Проверьте правильность времени и параметров сервера.  
  
7.  Проверьте установку следующим образом:  
  
    1.  Откройте панель мониторинга.  
  
    2.  Перейдите на вкладку **Пользователи** и убедитесь, что учетные записи пользователей указаны в Active Directory.  
  
### <a name="transfer-the-operations-master-roles"></a>Перенос ролей хозяина операций  
 Роли хозяев операций (также известные хозяином или FSMO) передаются с исходного сервера на конечный сервер в течение 21 дня после установки Windows Server Essentials на конечном сервере.  
  
##### <a name="to-transfer-the-operations-master-roles"></a>Перенос ролей хозяина операций  
  
1.  На целевом сервере откройте окно командной строки от имени администратора. См. раздел [Открытие окна командной строки от имени администратора](https://technet.microsoft.com/library/cc947813\(v=WS.10\).aspx).  
  
2.  В командной строке введите **NETDOM QUERY FSMO**и нажмите клавишу "ВВОД".  
  
3.  В командной строке введите **ntdsutil**и нажмите клавишу "ВВОД".  
  
4.  В командной строке  **ntdsutil** введите следующие команды:  
  
    1.  Введите **activate instance NTDS**и нажмите клавишу ВВОД.  
  
    2.  Введите **roles**и нажмите клавишу "ВВОД".  
  
    3.  Введите **connections** и нажмите клавишу "ВВОД".  
  
    4.  Тип **соединиться с сервером** *< ServerName\>*  (где *< ServerName\>*  имя конечного сервера), и нажмите клавишу ВВОД.  
  
    5.  В окне командной строки введите **q**и нажмите клавишу "ВВОД".  
  
        1.  Введите **transfer PDC**, нажмите клавишу ВВОД и щелкните **Да** в диалоговом окне **Подтверждение передачи роли**.  
  
        2.  Введите **transfer infrastructure master**, нажмите клавишу "ВВОД" и щелкните **Да** в диалоговом окне **Подтверждение передачи роли**.  
  
        3.  Введите **transfer naming master**, нажмите клавишу "ВВОД" и щелкните **Да** в диалоговом окне **Подтверждение передачи роли**.  
  
        4.  Введите **transfer RID master**, нажмите клавишу "ВВОД" и щелкните **Да** в диалоговом окне **Подтверждение передачи роли**.  
  
        5.  Введите **transfer schema master**, нажмите клавишу "ВВОД" и щелкните **Да** в диалоговом окне **Подтверждение передачи роли** .  
  
    6.  Введите **q**и нажимайте клавишу ВВОД до тех пор, пока не вернетесь в командную строку.  
  
> [!NOTE]
>  На любом сервере в сети вы можете убедиться, что роли хозяина операций были перенесены на кольцевой сервер. Откройте окно командной строки от имени администратора (дополнительные сведения см. в разделе [Открыть окно командной строки от имени администратора](https://technet.microsoft.com/library/cc947813\(v=WS.10\).aspx)). Введите **netdom query fsmo**и нажмите клавишу "ВВОД".  
  
## <a name="next-steps"></a>Следующие шаги  
 Вы установили Windows Server Essentials в качестве нового репликата контроллера домена. Теперь перейдите к [Step 3: Присоединение компьютеров к новому серверу Windows Server Essentials](Step-3--Join-computers-to-the-new-Windows-Server-Essentials-server.md).  
  
Чтобы просмотреть все действия, см. в разделе [миграции на Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).

