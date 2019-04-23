---
title: Управление BranchCache в Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59828805"
---
# <a name="manage-branchcache-in-windows-server-essentials"></a>Управление BranchCache в Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

BranchCache может помочь оптимизировать использование Интернета, повысить производительность сетевых приложений и уменьшить трафик в глобальной сети (WAN), если Windows Server Essentials расположен удаленно от офиса или клиентские компьютеры подключение к локальному серверу использования облачных ресурсов например библиотек SharePoint Online.  
  
 С поддержкой BranchCache, когда клиентский компьютер запрашивает содержимое с удаленного сервера Windows Server Essentials, содержимое кэшируется в локальном офисе. После этого остальные компьютеры в этом офисе могут получать данные локально, а не загружать их с сервера по глобальной сети. Это может увеличить производительность сетевых приложений и снизить нагрузку на глобальную сеть.  
  
 Ограничен ли сервер Windows Server Essentials локальным или удаленным, BranchCache может уменьшить время отклика для общих папках сервера и веб-содержимого, размещенного на сервере (например, библиотеки SharePoint Online).  
  
 Поскольку для развертывания BranchCache не нужно дополнительное оборудование или изменение топологии сети, эта служба представляет собой простое решение для оптимизации использования пропускной способности и сокращения времени отклика служб и приложений, доступ к которым осуществляется по глобальной сети.  
  
## <a name="branchcache-scenarios"></a>Сценарии использования BranchCache  
 Существует три основных сценария использования BranchCache с удаленным сервером.  
  
-   Сервер Windows Server Essentials, размещенная в Microsoft Azure.  
  
-   В центре обработки данных служба стороннего поставщика размещения сервера Windows Server Essentials.  
  
-   Windows Server Essentials сервер находится в другом офисе в другом физическом расположении.  
  
## <a name="distributed-cache-mode"></a>Режим распределенного кэша  
 В Windows Server Essentials, BranchCache реализован в *режим распределенного кэша*, один из двух доступных режимов в BranchCache. В режиме распределенного кэша кэш содержимого в филиале распределяется между клиентскими компьютерами. Поскольку в этом случае дополнительное оборудование и изменение топологии не требуются, этот режим больше подходит для небольших офисов, где для доступа к облачным службам, таким как SharePoint Online, используется удаленный сервер или локальный сервер. При включении BranchCache в Windows Server Essentials, реализуется режим распределенного кэша.  
  
> [!NOTE]
>  В крупных филиалах с несколькими подсетями или большим количеством сотрудников, работающих с сетевыми приложениями, может быть целесообразно реализовать BranchCache в *режиме размещенного кэша*. В режиме размещенного кэша кэш содержимого размещается в филиале на одном или нескольких серверах размещенного кэша.
  
## <a name="requirements"></a>Требования  
 Чтобы использовать BranchCache в Windows Server Essentials, сервер и клиентские компьютеры должны соответствовать следующим требованиям:  
  
-   На сервере должна выполняться ОС Windows Server Essentials или Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter операционной системы с ролью Windows Server Essentials Experience.  
  
     На сервере Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter BranchCache добавляется при добавлении роли Windows Server Essentials Experience. Чтобы включить BranchCache, необходимо войти в панель мониторинга Windows Server Essentials с правами администратора домена.  
  
-   Клиентские компьютеры должны работать под управлением Windows 7 Корпоративная, Windows 7 Максимальная, Windows 8 Корпоративная или Windows 8.1 Enterprise операционной системы.  
  
-   В режиме распределенного кэша все клиентские компьютеры должны находиться в одной подсети.  
  
    > [!NOTE]
    >  Если клиентские компьютеры подключены к серверу Windows Server Essentials без присоединения к домену, они исключаются из кэширования по умолчанию. Чтобы включить в кэширование клиентский компьютер, который не присоединен к домену, выполните командлет [Enable-BCDistributed](https://technet.microsoft.com/library/hh848398.aspx) Windows PowerShell на этом компьютере. Дополнительные сведения см. в разделе [Командлеты BranchCache в Windows PowerShell](https://technet.microsoft.com/library/hh848392.aspx).  
 
  
## <a name="turn-branchcache-on"></a>Включение BranchCache  
 Чтобы включить BranchCache в режиме распределенного кэша, просто щелкните кнопку на панели мониторинга Windows Server Essentials. Кэширование начинается немедленно и процесс полностью прозрачен.  
  
#### <a name="to-turn-on-branchcache-in-windows-server-essentials"></a>Включение BranchCache в Windows Server Essentials  
  
1.  Войдите на сервере Windows Server Essentials с помощью учетной записи администратора.  
  
2.  На мониторинга Windows Server Essentials щелкните **параметры**.  
  
     Откроется мастер настройки параметров.  
  
3.  Щелкните **BranchCache**.  
  
4.  На странице **Параметры BranchCache** нажмите кнопку **Включить**.  
  
## <a name="use-windows-powershell-to-turn-branchcache-on-or-off"></a>Включение и отключение BranchCache с помощью Windows PowerShell  
 С помощью Windows PowerShell можно проверять состояние BranchCache (включено или отключено) и включать или отключать BranchCache.  
  
#### <a name="to-turn-branchcache-on-or-off-using-windows-powershell"></a>Включение и отключение BranchCache с помощью Windows PowerShell  
  
1.  На сервере откройте Windows PowerShell от имени администратора. На **начальной** странице щелкните правой кнопкой мыши **Windows PowerShell**, а затем выберите **Запуск от имени администратора** и нажмите кнопку **Да**.  
  
2.  В командной строке введите один из следующих командлетов.  
  
    -   Чтобы проверить состояние BranchCache (служба включена или отключена), введите:  
  
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
  
## <a name="see-also"></a>См. также  
    
-   [Обзор BranchCache](https://technet.microsoft.com/library/hh831696.aspx)  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)
