---
title: "AD леса восстановление — проверьте репликации"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/07/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 302e522a-fb40-43bc-bc63-83dcc87ebde5
ms.technology: identity-adfs
ms.openlocfilehash: d85336a10e808755677a99777af8ecf5c07b05ab
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="resources-to-verify-replication-is-working"></a>Ресурсы, чтобы убедиться, что репликация работает 

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2
 
 После восстановления или повторно установить все контроллеры домена, можно проверить, Доменных службах Active Directory и SYSVOL, восстановленные и репликацию правильно с помощью **repadmin/REPLSUM**, который выполняется в любой версии Windows Server.  
  
> [!TIP]
>  Можно также загрузить и запустить [средства состояние репликации Active Directory](https://www.microsoft.com/download/details.aspx?id=30005) (ADReplStatus), бесплатного средства, которое отслеживает состояние репликации контроллеров домена и сообщает об ошибках. ADReplStatus требуется .NET Framework 4, который будет устанавливаться, если это еще не сделано.  
  
 Проверьте журнал репликации DFS в средстве просмотра событий для 4602 идентификатор события (или ИД событий службы репликации файлов 13516) показывает, что SYSVOL был инициализирован.  
  
 Если восстановить первый контроллер домена регистрирует 4614 идентификатор события («контроллер домена готова к начальной репликации. Реплицированная папка останется в состоянии начальной синхронизации до выполнения репликации со своим партнером») в журнале репликации DFS, затем код события 4602 не отображается и необходимо выполнить перечисленные ниже действия вручную восстановлению реплицируется с DFSR SYSVOL:  
  
1.  При появлении DFSR событие 4612 на первого восстановленного контроллера домена выполнить вручную принудительного восстановления, которая описана в [2218556: как принудительное выполнение заслуживающей и не заслуживающей доверия синхронизации для SYSVOL, реплицированного DFSR (как «D4/D2» для FRS)](https://support.microsoft.com/kb/2218556) (https://support.microsoft.com/kb/2218556).  
  
2.  Задайте **флаг SysvolReady** 1 вручную, как описано в [947022 ресурсу NETLOGON не указан, после установки доменных служб Active Directory для нового контроллера домена под управлением Windows Server 2008 full "или" только для чтения](https://support.microsoft.com/kb/947022).  
  
 Можно также создать диагностический отчет по репликации DFS. Дополнительные сведения см. в разделе [Создание диагностического отчета для репликации DFS](https://technet.microsoft.com/library/cc754227.aspx) и [DFS Step-by-Step руководстве по Windows Server 2008](https://technet.microsoft.com/library/cc732863\(WS.10\).aspx). Если сервер работает под управлением Windows Server 2008 R2, можно использовать [параметр командной строки dfsrdiag.exe ReplicationState](http://blogs.technet.com/b/filecab/archive/2009/05/28/dfsrdiag-exe-replicationstate-what-s-dfsr-up-to.aspx).  
  
 Можно также выполнить тест репликации с помощью dcdiag.exe для проверки ошибок репликации. Дополнительные сведения см. в статье базы знаний [статья 249256](https://support.microsoft.com/kb/249256).

## <a name="next-steps"></a>Дальнейшие действия

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
