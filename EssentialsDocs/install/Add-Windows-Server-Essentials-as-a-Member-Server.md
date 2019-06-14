---
title: Добавление Windows Server Essentials в качестве рядового сервера
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d09dd82f-f7d2-47ce-862d-fd9869f2021c
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 502e54cf719895dd11030cf163159f6cdda47164
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433728"
---
# <a name="add-windows-server-essentials-as-a-member-server"></a>Добавление Windows Server Essentials в качестве рядового сервера

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Этот раздел относится к серверу под управлением Windows Server 2012 R2 Standard, Windows Server 2012 R2 Datacenter или Windows Server 2016 с установленной ролью Windows Server Essentials Experience. В оставшейся части этого документа роль Windows Server Essentials Experience будет называться Windows Server Essentials.  
  
> [!NOTE]
>   Windows Server Essentials можно развернуть только в качестве контроллера домена. В этом документе Windows Server Essentials не включает Windows Server Essentials.  
  
 Windows Server Essentials необязательно быть основным сервером в домене Windows. Вы можете добавить Windows Server Essentials в качестве рядового сервера в существующую среду домена Active Directory и использовать все преимущества защиты данных, безопасного удаленного доступа и интеграции с облачными службами, которые он предоставляет. Кроме того, Windows Server Essentials можно развернуть в существующей среде Active Directory не только как контроллер домена. Это позволяет расширить хранилище или использовать филиал для локального хранения данных и администрирования.  
  
 Windows Server Essentials можно добавить одним из следующих способов.  
  
-   Добавьте Windows Server Essentials в филиал своего офиса и присоедините его к контроллеру домена, расположенному в главном офисе с помощью стандартных средств. Вы можете включить функцию BranchCache для использования оптимальной пропускной способности данного рядового сервера.  
  
-   Добавьте Windows Server Essentials в качестве рядового сервера в сети Windows Server Essentials, чтобы расширить хранилище сети с помощью добавления дополнительных серверных папок на ваш рядовой сервер.  
  
-   Добавьте Windows Server Essentials в качестве рядового сервера в локальном офисе, если сервера-источника под управлением Windows Server Essentials размещено в Microsoft Azure или у стороннего поставщика услуг размещения. Использование Windows Server Essentials в качестве рядового сервера в локальном офисе позволяет оптимизировать пропускную способность.  
  
## <a name="adding-windows-server-essentials-as-a-member-server"></a>Добавление Windows Server Essentials в качестве рядового сервера  
 Чтобы добавить Windows Server Essentials в качестве рядового сервера для сервера-источника под управлением Windows Server 2012 R2 или Windows Server Essentials в существующей среде Active Directory, необходимо выполнить следующие действия:  
  
1.  Присоедините сервер под управлением Windows Server Essentials к рабочей группе.  
  
2.  Присоедините сервер под управлением Windows Server Essentials к домену основного сервера Windows Server Essentials.  
  
3.  Настройка Windows Server Essentials Experience в диспетчере сервера.  
  
#### <a name="to-join-windows-server-essentials-to-a-workgroup-or-domain"></a>Присоединение Windows Server Essentials к рабочей группе или домену  
  
1. После завершения установки Windows Server Essentials на втором сервере закройте мастер настройки Windows Server Essentials.  
  
2. В поле **Поиск** введите **System Settings**и в результатах поиска выберите **Просмотр расширенных параметров системы**.  
  
3. В окне **Свойства системы** перейдите на вкладку **Имя компьютера**.  
  
4. В окне **Имя компьютера** в разделе **Домен** нажмите кнопку **Изменить**.  
  
5. В **изменение имени компьютера или домена**в **член** выберите, если вы хотите присоединить сервер под управлением Windows Server Essentials для **рабочей группы** или **Домена**.  
  
   -   Чтобы добавить сервер к рабочей группе, введите команду **workgroup**, а затем нажмите кнопку **ОК**.  
  
   -   Чтобы присоединить этот сервер к существующему домену Active Directory, введите имя домена и нажмите кнопку **ОК**.  
  
6. Чтобы изменения вступили в силу, перезагрузите сервер.  
  
   После присоединения сервера к домену основного сервера s, вы можете настроить Windows Server Essentials, запустив мастер настройки Windows Server Essentials из диспетчера сервера.  
  
#### <a name="to-configure-windows-server-essentials-experience-on-a-member-server"></a>Настройка Windows Server Essentials Experience на рядовом сервере  
  
1.  (Необязательно) При необходимости измените имя сервера.  
  
    > [!IMPORTANT]
    >  Не удается изменить имя сервера, после настройки Windows Server Essentials Experience.  
  
2.  Войдите в сервер с помощью учетной записи администратора домена.  
  
3.  Откройте диспетчер сервера.  
  
4.  В области уведомлений в **диспетчере сервера** установите флажок, а затем выберите **Настройка Windows Server Essentials**.  
  
5.  Выберите настройку сервера в качестве рядового сервера и нажмите кнопку **Далее**.  
  
6.  Щелкните **Настройка**, чтобы приступить к настройке. Процесс настройки занимает около 10 минут.  
  
7.  На рабочем столе щелкните значок панели мониторинга для запуска панели мониторинга. На домашней странице завершите задачи **Приступая к работе** , перечисленные на вкладке **Установка** .  
  
## <a name="see-also"></a>См. также  
  

-   [Установка Windows Server Essentials](Install-Windows-Server-Essentials.md)

-   [Установка Windows Server Essentials](../install/Install-Windows-Server-Essentials.md)

