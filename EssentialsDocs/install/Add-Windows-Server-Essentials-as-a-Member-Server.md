---
title: "Добавьте Windows Server Essentials в качестве рядового сервера"
description: "Описывается, как использовать Windows Server Essentials"
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
ms.openlocfilehash: 8fb73f8186d3984c9e93f7a6e39cb72a54db1e58
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="add-windows-server-essentials-as-a-member-server"></a>Добавьте Windows Server Essentials в качестве рядового сервера

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Этот раздел относится к серверу под управлением Windows Server 2012 R2 Standard, Windows Server 2012 R2 Datacenter или Windows Server 2016 с установленной ролью Windows Server Essentials Experience. В оставшейся части этого документа роль Windows Server Essentials Experience будет называться Windows Server Essentials.  
  
> [!NOTE]
>   Windows Server Essentials можно развернуть только как контроллер домена. В этом документе Windows Server Essentials не включает Windows Server Essentials.  
  
 Windows Server Essentials необязательно быть основным сервером в домене Windows. Можно добавить Windows Server Essentials в качестве рядового сервера в существующую среду домена Active Directory и использовать преимущества защиты данных, безопасного удаленного доступа и интеграции с облачными службами, он предоставляет. Кроме того Windows Server Essentials можно развернуть в существующей среде Active Directory без необходимости быть контроллером домена. Это позволяет расширить хранилище или использовать филиал для локального хранения данных и администрирования.  
  
 Windows Server Essentials можно добавить в следующих случаях:  
  
-   Добавьте Windows Server Essentials в филиал своего офиса и присоедините его к контроллеру домена, расположенному в главном офисе в отдельном расположении с помощью стандартных средств. Можно включить функции BranchCache для использования оптимальной пропускной способности данного рядового сервера.  
  
-   Добавьте Windows Server Essentials в качестве рядового сервера в сети Windows Server Essentials, чтобы расширить хранилище сети с помощью добавления дополнительных серверных папок на ваш рядовой сервер.  
  
-   Добавьте Windows Server Essentials в качестве рядового сервера в локальном офисе, если ваш основной сервер под управлением Windows Server Essentials размещается в Microsoft Azure или у стороннего поставщика услуг размещения. Использование Windows Server Essentials в качестве рядового сервера в вашем локальном офисе позволяет оптимизировать использование пропускной способности.  
  
## <a name="adding-windows-server-essentials-as-a-member-server"></a>Добавление Windows Server Essentials в качестве рядового сервера  
 Чтобы добавить Windows Server Essentials в качестве рядового сервера к основному серверу под управлением Windows Server 2012 R2 или Windows Server Essentials в существующей среде Active Directory, необходимо выполнить следующие действия:  
  
1.  Присоедините сервер под управлением Windows Server Essentials к рабочей группе.  
  
2.  Присоедините сервер под управлением Windows Server Essentials к домену основного сервера Windows Server Essentials.  
  
3.  Настройка Windows Server Essentials Experience с помощью диспетчера сервера.  
  
#### <a name="to-join-windows-server-essentials-to-a-workgroup-or-domain"></a>Присоединение к рабочей группе или домене Windows Server Essentials  
  
1.  После завершения установки Windows Server Essentials на втором сервере, закройте мастер настройки Windows Server Essentials.  
  
2.  В **поиска** введите **параметры системы**и в результатах поиска щелкните **Просмотр расширенных параметров системы**.  
  
3.  В **свойства системы**, нажмите кнопку **имя компьютера** вкладку.  
  
4.  В **имя компьютера**в **домена** щелкните **изменение**.  
  
5.  В **изменение имени компьютера или домена**в **члена** выберите, если вы хотите присоединить сервер под управлением Windows Server Essentials на **рабочей группы** или **домена**.  
  
    -   Чтобы добавить сервер к рабочей группе, введите **рабочей группы**, а затем нажмите кнопку **ОК**.  
  
    -   Чтобы присоединить этот сервер к существующему домену Active Directory, введите имя домена и нажмите кнопку **ОК**.  
  
6.  Перезапустите сервер, чтобы применить изменения.  
  
 После присоединения сервера к домену основного сервера s, можно продолжить настройку Windows Server Essentials, запустив мастер настройки Windows Server Essentials из диспетчера сервера.  
  
#### <a name="to-configure-windows-server-essentials-experience-on-a-member-server"></a>Чтобы настроить Windows Server Essentials Experience на рядовом сервере  
  
1.  (Необязательно) При необходимости измените имя сервера.  
  
    > [!IMPORTANT]
    >  После настройки Windows Server Essentials Experience не может изменить имя сервера.  
  
2.  Войдите на сервер с помощью учетной записи администратора домена.  
  
3.  Откройте диспетчер сервера.  
  
4.  В области уведомлений в **диспетчера сервера**, установите соответствующий флажок и нажмите кнопку **Настройка Windows Server Essentials**.  
  
5.  Выберите настройку сервера в качестве рядового сервера и нажмите кнопку **Далее**.  
  
6.  Нажмите кнопку **Настройка** Чтобы приступить к настройке. Процесс настройки занимает около 10 минут.  
  
7.  На рабочем столе щелкните значок панели мониторинга для запуска панели мониторинга. На домашней странице завершите **Приступая к работе** задачи, которые указаны на **установки** вкладку.  
  
## <a name="see-also"></a>См. также:  
  

-   [Установка Windows Server Essentials](Install-Windows-Server-Essentials.md)

-   [Установка Windows Server Essentials](../install/Install-Windows-Server-Essentials.md)

