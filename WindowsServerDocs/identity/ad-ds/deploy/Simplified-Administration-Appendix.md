---
ms.assetid: c911d6c6-98c6-4532-b1db-5724e1ceb96c
title: Приложение по упрощенному администрированию
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 36cdacec27e64586c359146b858a9d68750e5026
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858265"
---
# <a name="simplified-administration-appendix"></a>Приложение по упрощенному администрированию

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

  
-   [Диспетчер серверов: Добавление серверов диалоговое окно (Active Directory)](../../ad-ds/deploy/Simplified-Administration-Appendix.md#BKMK_AddServers)  
  
-   [Состояние сервера удаленного диспетчера серверов](../../ad-ds/deploy/Simplified-Administration-Appendix.md#BKMK_ServerMgrStatus)  
  
-   [Загрузка модуля PowerShell Windows](../../ad-ds/deploy/Simplified-Administration-Appendix.md#BKMK_PSLoadModule)  
  
-   [RID выдачи исправлений для предыдущих операционных систем](../../ad-ds/deploy/Simplified-Administration-Appendix.md#BKMK_Rid)  
  
-   [Ntdsutil.exe Install from Media Changes](../../ad-ds/deploy/Simplified-Administration-Appendix.md#BKMK_IFM)  
  
## <a name="BKMK_AddServers"></a>Диспетчер серверов: Добавление серверов диалоговое окно (Active Directory)  

**Добавление серверов** диалоговое окно позволяет поиск по Active Directory для серверов, операционной системой, с использованием подстановочных знаков и по расположению. Диалоговое окно также позволяет использовать запросы DNS, полное доменное имя или имя префикса. Поиск использовать собственный DNS- и LDAP протоколы, реализовать с помощью .NET, не AD Windows PowerShell для работы шлюза управления AD по протоколу SOAP - это означает, что контроллеры домена, связаться с диспетчером серверов можно даже запускать Windows Server 2003. Также можно импортировать файл с имена серверов для целей подготовки.  
  
Поиск Active Directory использует следующие фильтры LDAP:  
  
```  
(&(ObjectCategory=computer)  
  
(&(ObjectCategory=computer)(cn=dc*)(OperatingSystemVersion=6.2*))  
  
(&(ObjectCategory=computer)(OperatingSystemVersion=6.1*))  
  
(&(ObjectCategory=computer)(OperatingSystemVersion=6.0*))  
  
(&(ObjectCategory=computer)(|(OperatingSystemVersion=5.2*)(OperatingSystemVersion=5.1*)))  
  
```  
  
Поиск Active Directory возвращает следующие атрибуты:  
  
```  
( dnsHostName )( operatingSystem )( cn )  
  
```  
  
## <a name="BKMK_ServerMgrStatus"></a>Состояние сервера удаленного диспетчера серверов  
Диспетчер сервера проверяет доступность удаленного сервера, с помощью протокола маршрутизации адрес. Все серверы, не отвечает на запросы ARP не указываются, даже если они находятся в пуле.  
  
Если отвечает на запросы ARP, затем WMI и DCOM подключения к серверу для возвращения сведений о состоянии. Если недоступны RPC, DCOM и WMI, диспетчер сервера не может управлять не полностью сервера.  
  
## <a name="BKMK_PSLoadModule"></a>Загрузка модуля PowerShell Windows  
Windows PowerShell 3.0 реализует динамической загрузки модуля. С помощью **Import-Module** командлета больше обычно не требуется; вместо этого просто вызов командлета, псевдоним или функция автоматически загружает модуль.  
  
Чтобы просмотреть загруженные модули, используйте **Get-Module** командлета.  
  
```  
Get-Module  
  
```  
  
![Упрощенное администрирование](media/Simplified-Administration-Appendix/ADDS_PSGetModule.gif)  
  
Чтобы просмотреть все установленные модули с их экспортированных функций и командлетов, используйте следующую команду:  
  
```  
Get-Module -ListAvailable  
  
```  
  
Основного варианта использования **import-module** команды, которая когда вам нужен доступ к «AD:» Виртуальный диск Windows PowerShell и ничего более уже загружен модуль. Например с помощью следующих команд:  
  
```  
import-module activedirectory  
cd ad:  
dir  
  
```  
  
## <a name="BKMK_Rid"></a>RID выдачи исправлений для предыдущих операционных систем  
См. в разделе [доступно обновление для обнаружения и предотвратить чрезмерное потребление глобального пула RID на контроллере домена под управлением Windows Server 2008 R2](https://support.microsoft.com/kb/2618669).  
  
## <a name="BKMK_IFM"></a>Ntdsutil.exe Install from Media Changes  
Windows Server 2012 добавляет два дополнительных параметра командной строки средства Ntdsutil.exe для **IFM (создать носитель IFM)** меню. Они позволяют создавать IFM хранилища, выполняя автономную дефрагментацию экспортированного NTDS. Файл базы данных DIT. Если места на диске не категории "премиум", это экономит время, создание IFM.  
  
В следующей таблице описаны две новые элементы меню:  
  
|||  
|-|-|  
|Пункт меню|Объяснение|  
|Создание полной NoDefrag %s|Создать носитель IFM без дефрагментации для полного контроллера домена AD или AD/LDS экземпляра в папку %s|  
|Создание полной Sysvol NoDefrag %s|Создать носитель IFM с SYSVOL и без дефрагментации для полного контроллера домена AD, в папку %s|  
  
![Упрощенное администрирование](media/Simplified-Administration-Appendix/ADDS_PSIFM.png)  
  
![Упрощенное администрирование](media/Simplified-Administration-Appendix/ADDS_PSIFMComplete.gif)  
  


