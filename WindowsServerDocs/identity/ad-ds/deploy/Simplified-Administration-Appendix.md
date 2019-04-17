---
ms.assetid: c911d6c6-98c6-4532-b1db-5724e1ceb96c
title: "Приложение по упрощенному администрированию"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 5de7431d0f3fe9a078432b11a63ce996d3abe447
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="simplified-administration-appendix"></a>Приложение по упрощенному администрированию

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

  
-   [Диалоговое окно серверов (Active Directory) добавления диспетчера сервера](../../ad-ds/deploy/Simplified-Administration-Appendix.md#BKMK_AddServers)  
  
-   [Состояние сервера удаленного диспетчера сервера](../../ad-ds/deploy/Simplified-Administration-Appendix.md#BKMK_ServerMgrStatus)  
  
-   [Загрузка модуля PowerShell в Windows](../../ad-ds/deploy/Simplified-Administration-Appendix.md#BKMK_PSLoadModule)  
  
-   [Выдачи исправления, касающиеся относительных ИДЕНТИФИКАТОРОВ предыдущих операционных системах](../../ad-ds/deploy/Simplified-Administration-Appendix.md#BKMK_Rid)  
  
-   [Изменяет Ntdsutil.exe установки с носителя](../../ad-ds/deploy/Simplified-Administration-Appendix.md#BKMK_IFM)  
  
## <a name="BKMK_AddServers"></a>Диалоговое окно серверов (Active Directory) добавления диспетчера сервера  

**Добавление серверов** диалоговое окно позволяет поиск серверы, Active Directory операционной системы, с помощью подстановочных знаков и расположение. Диалоговое окно также позволяет с помощью DNS-запросы по полное доменное имя или префикс имени. Поиск использовать собственные протоколы DNS и LDAP, развернутые с помощью .NET, не AD Windows PowerShell от Management Gateway AD через SOAP - это означает, что связь с диспетчером серверов контроллеры домена даже можно запустить в Windows Server 2003. Также можно импортировать файл, имена серверов для подготовки целей.  
  
Поиск в Active Directory использует следующие фильтры LDAP:  
  
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
  
## <a name="BKMK_ServerMgrStatus"></a>Состояние сервера удаленного диспетчера сервера  
Диспетчер сервера проверяет специальных возможностей удаленного сервера, с помощью протокола маршрутизации. Все серверы, не отвечает на запросы ARP не указаны, даже если они находятся в пуле.  
  
Если отвечает ARP, затем DCOM и WMI подключения к серверу для получения сведений о состоянии. Если недоступны WMI, RPC и DCOM, диспетчер сервера не можете полностью управлять сервера.  
  
## <a name="BKMK_PSLoadModule"></a>Загрузка модуля PowerShell в Windows  
Windows PowerShell 3.0 реализует загрузка динамического модуля. С помощью **Import-Module** командлета больше обычно не требуется; Вместо этого просто для вызова командлета, alias или function автоматически загружает модуль.  
  
Чтобы увидеть загруженных модулей, используйте **Get-Module** командлета.  
  
```  
Get-Module  
  
```  
  
![Упрощенное администрирование](media/Simplified-Administration-Appendix/ADDS_PSGetModule.gif)  
  
Чтобы просмотреть все установленные модули с их экспортированных функций и командлетов, используйте следующую команду:  
  
```  
Get-Module -ListAvailable  
  
```  
  
Основного варианта использования **import-module** команды, когда требуется доступ к «AD: «виртуальный диск Windows PowerShell и ничто уже загрузивший модуль. Например с помощью следующих команд:  
  
```  
import-module activedirectory  
cd ad:  
dir  
  
```  
  
## <a name="BKMK_Rid"></a>Выдачи исправления, касающиеся относительных ИДЕНТИФИКАТОРОВ предыдущих операционных системах  
В разделе [обновление доступно для обнаружения и предотвращения слишком много использования глобального пула RID контроллера домена под управлением Windows Server 2008 R2](https://support.microsoft.com/kb/2618669).  
  
## <a name="BKMK_IFM"></a>Изменяет Ntdsutil.exe установки с носителя  
Windows Server 2012 добавлены два дополнительных варианта действий в средство командной строки Ntdsutil.exe для **IFM (создать носитель IFM)** меню. Они позволяют создавать IFM хранилищ без первого выполнения автономной дефрагментации экспортированные NTDS. Файл базы данных DIT. Если места на диске не premium, это экономит время, создание IFM.  
  
В следующей таблице описаны две новые пункты меню:  
  
|||  
|-|-|  
|Пункт меню|Объяснение|  
|Создайте полную NoDefrag %s|Создать носитель IFM без дефрагментации для полного контроллера домена AD или экземпляр Облегченного или в папку %s|  
|Создание полной Sysvol NoDefrag %s|Создать носитель IFM с SYSVOL и без дефрагментации для полного контроллера домена AD, в папку %s|  
  
![Упрощенное администрирование](media/Simplified-Administration-Appendix/ADDS_PSIFM.png)  
  
![Упрощенное администрирование](media/Simplified-Administration-Appendix/ADDS_PSIFMComplete.gif)  
  


