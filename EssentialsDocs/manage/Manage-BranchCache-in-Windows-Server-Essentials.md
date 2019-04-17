---
title: "Управление BranchCache в Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6e05aec-d07c-4e0b-94ab-f20279e9ffd1
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 13d1d439eb9eeb60de9779d783e36405aee3ddfc
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="manage-branchcache-in-windows-server-essentials"></a>Управление BranchCache в Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Служба BranchCache может помочь оптимизировать использование Интернета, увеличить производительность сетевых приложений и уменьшить трафик в глобальной сети (WAN), когда Windows Server Essentials server расположен удаленно от офиса или при подключении клиентских компьютеров к локальному серверу использовать облачные ресурсы, такие как библиотеки SharePoint Online.  
  
 Служба BranchCache включена, когда клиентский компьютер запрашивает содержимое с удаленного сервера Windows Server Essentials, содержимое кэшируется в локальном офисе. После этого остальные компьютеры в этом офисе могут получать данные локально, а не загружать содержимое с сервера по глобальной сети. Это может увеличить производительность сетевых приложений и снижает потребление пропускной способности по глобальной сети.  
  
 Является ли сервер Windows Server Essentials локальным или удаленным, BranchCache может уменьшить время отклика для общих папках сервера и веб-содержимого, размещенного на сервере (например, библиотеки SharePoint Online).  
  
 Так как BranchCache не требуется новое оборудование или изменение топологии сети, эта функция предоставляет простой способ оптимизации использования пропускной способности и сокращения времени отклика служб и доступ к ресурсам получен через глобальную сеть.  
  
## <a name="branchcache-scenarios"></a>Сценарии использования BranchCache  
 Существует три основных сценария использования BranchCache с удаленным сервером.  
  
-   Сервер Windows Server Essentials размещается в Microsoft Azure.  
  
-   Сервер Windows Server Essentials размещается в центре обработки данных поставщика услуг сторонних производителей.  
  
-   Сервер Windows Server Essentials — в другом офисе в отдельном физическом расположении.  
  
## <a name="distributed-cache-mode"></a>Режим распределенного кэша  
 В Windows Server Essentials, служба BranchCache работает в *режим распределенного кэша*, один из двух доступных режимов в BranchCache. В режиме распределенного кэша кэш содержимого в филиале распределяется между клиентскими компьютерами. Поскольку нет дополнительное оборудование или изменение топологии не требуются, этот режим больше подходит для небольших офисов, в которых используется удаленный сервер или локальный сервер для доступа к облачным службам, таким как SharePoint Online. При включении BranchCache в Windows Server Essentials реализуется режим распределенного кэша.  
  
> [!NOTE]
>  В крупных филиалах с несколькими подсетями или большим количеством сотрудников, работающих с сетевыми приложениями, может быть целесообразно реализовать BranchCache в *режима размещенного кэша*. В режиме размещенного кэша кэш содержимого хранится на один или несколько серверов размещенного кэша в филиале.
  
## <a name="requirements"></a>Требования к  
 Чтобы использовать BranchCache в Windows Server Essentials, сервер и клиентские компьютеры удовлетворяет следующим требованиям.  
  
-   Сервер должен работать под управлением операционной системы Windows Server Essentials или Windows Server 2012 R2 Standard или операционной системы Windows Server 2012 R2 Datacenter с ролью Windows Server Essentials Experience.  
  
     На сервере Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter BranchCache добавляется при добавлении роли Windows Server Essentials Experience. Чтобы включить BranchCache, необходимо будет выполнить вход на панели мониторинга Windows Server Essentials с правами администратора домена.  
  
-   Клиентские компьютеры должны работать под управлением Windows 7 Корпоративная, Windows 7 Максимальная, Windows 8 Корпоративная или Windows 8.1 Корпоративная операционной системы.  
  
-   В режиме распределенного кэша всех клиентских компьютерах должен быть в одной подсети.  
  
    > [!NOTE]
    >  Если клиентские компьютеры подключены к серверу Windows Server Essentials без присоединения к домену, они исключаются из кэширования по умолчанию. Чтобы включить клиентский компьютер не присоединенные к домену в кэширование, выполните [Enable-BCDistributed](https://technet.microsoft.com/library/hh848398.aspx) командлета Windows PowerShell на клиентском компьютере. Дополнительные сведения см. в разделе [командлеты BranchCache в Windows PowerShell](https://technet.microsoft.com/library/hh848392.aspx).  
 
  
## <a name="turn-branchcache-on"></a>Включить BranchCache  
 Чтобы включить BranchCache в режиме распределенного кэша, нужно просто щелкнуть кнопку на панели мониторинга Windows Server Essentials. Кэширование начинается немедленно и процесс полностью прозрачен.  
  
#### <a name="to-turn-on-branchcache-in-windows-server-essentials"></a>Чтобы включить BranchCache в Windows Server Essentials  
  
1.  Войдите на сервер Windows Server Essentials с вашей учетной записи администратора.  
  
2.  Для мониторинга Windows Server Essentials щелкните **параметры**.  
  
     Откроется мастер настройки параметров.  
  
3.  Нажмите кнопку **BranchCache**.  
  
4.  На **параметры BranchCache** щелкните **включить**.  
  
## <a name="use-windows-powershell-to-turn-branchcache-on-or-off"></a>Чтобы включить BranchCache, или отключить с помощью Windows PowerShell  
 Чтобы проверить состояние BranchCache (включено или отключено) и включить BranchCache, или отключить, можно использовать Windows PowerShell.  
  
#### <a name="to-turn-branchcache-on-or-off-using-windows-powershell"></a>Чтобы включить BranchCache или отключить с помощью Windows PowerShell  
  
1.  На сервере откройте Windows PowerShell с правами администратора. На **запустить** щелкните правой кнопкой мыши **Windows PowerShell**, нажмите кнопку **Запуск от имени администратора**, а затем нажмите кнопку **Да**.  
  
2.  Введите один из перечисленных ниже командлетов в командной строке.  
  
    -   Чтобы проверить состояние BranchCache (включено или отключено), введите:  
  
        ```powershell  
        Get-WSSBranchCacheStatus  
        ```  
  
    -   Чтобы включить BranchCache, введите:  
  
        ```powershell  
        Enable-WSSBranchCache  
        ```  
  
    -   Чтобы отключить BranchCache, введите:  
  
        ```powershell  
        Disable-WSSBranchCache  
        ```  
  
## <a name="see-also"></a>См. также:  
    
-   [Обзор BranchCache](https://technet.microsoft.com/library/hh831696.aspx)  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)
