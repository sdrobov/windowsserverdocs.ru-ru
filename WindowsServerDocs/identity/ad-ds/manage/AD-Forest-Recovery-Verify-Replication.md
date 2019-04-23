---
title: AD леса восстановления - проверьте репликацию
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 302e522a-fb40-43bc-bc63-83dcc87ebde5
ms.technology: identity-adds
ms.openlocfilehash: fb05586f281460dc2c7a1afea4c0423493e3fc46
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59878315"
---
# <a name="resources-to-verify-replication-is-working"></a>Ресурсы для проверки работоспособности репликации 

>Область применения. Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

После восстановления или повторной установке всех контроллеров домена, чтобы узнать, AD DS и SYSVOL надлежащую восстановленные и реплицируется с помощью **repadmin/REPLSUM**, который запускает на любой версии Windows Server.  
  
> [!TIP]
> Можно также загрузить и запустить [средства состояния репликации Active Directory](https://www.microsoft.com/download/details.aspx?id=30005) (ADReplStatus), бесплатное средство, которое отслеживает состояние репликации контроллеров домена и сообщает об ошибках. ADReplStatus требуется .NET Framework 4, которая будет установлена в том случае, если он еще не.  

В средстве просмотра событий для 4602 идентификатор события (или идентификатор события служба репликации файлов 13516), указывающий, что SYSVOL был инициализирован в журнале репликации DFS.  

Если восстановить первый контроллер домена регистрирует 4614 идентификатор события («контроллер домена ожидает выполнения первоначальной репликации. Реплицированная папка останется в состоянии начальной синхронизации до выполнения репликации со своим партнером») в журнале репликации DFS, 4602 идентификатор события выглядит и необходимо выполнить следующие действия вручную, чтобы восстановить SYSVOL, если они реплицируются по DFSR:  

1. Когда появится 4612 событие DFSR первый восстановленного контроллера домена выполните принудительное восстановление вручную, как описано в [2218556: Принудительное выполнения заслуживающей и не заслуживающей доверия синхронизации для папки SYSVOL с репликацией DFSR (как «D4/D2» для FRS)](https://support.microsoft.com/kb/2218556) (https://support.microsoft.com/kb/2218556).  
2. Задайте **флаг SysvolReady** 1 вручную, как описано в разделе [947022 общую папку NETLOGON отсутствует после установки доменных служб Active Directory на контроллере домена под управлением Windows Server 2008 полные или только для чтения ](https://support.microsoft.com/kb/947022).  

Можно также создать диагностический отчет репликации DFS. Дополнительные сведения см. в разделе [создать диагностический отчет для репликации DFS](https://technet.microsoft.com/library/cc754227.aspx) и [DFS Пошаговое руководство для Windows Server 2008](https://technet.microsoft.com/library/cc732863\(WS.10\).aspx). Если сервер работает под управлением Windows Server 2008 R2, можно использовать [параметр командной строки dfsrdiag.exe ReplicationState](http://blogs.technet.com/b/filecab/archive/2009/05/28/dfsrdiag-exe-replicationstate-what-s-dfsr-up-to.aspx).  

Также вы можете тестирования репликации, используя dcdiag.exe на наличие ошибок репликации. Дополнительные сведения см. в статье базы знаний [статьи 249256](https://support.microsoft.com/kb/249256).

## <a name="next-steps"></a>Следующие шаги

- [Руководство по восстановлению из леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD - процедуры](AD-Forest-Recovery-Procedures.md)
