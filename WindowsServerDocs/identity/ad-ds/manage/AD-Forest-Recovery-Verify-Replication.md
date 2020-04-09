---
title: Восстановление леса Active Directory — проверка репликации
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: 302e522a-fb40-43bc-bc63-83dcc87ebde5
ms.technology: identity-adds
ms.openlocfilehash: af0946674d9185651c7b22a822dcc3a2dd5a1c5d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80823397"
---
# <a name="resources-to-verify-replication-is-working"></a>Ресурсы для проверки работы репликации 

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

После восстановления или повторной установки всех контроллеров домена можно убедиться, что AD DS и SYSVOL восстановлены и правильно реплицируются с помощью **repadmin/реплсум**, работающей на любой версии Windows Server.  
  
> [!TIP]
> Можно также загрузить и запустить [средство состояние репликации Active Directory](https://www.microsoft.com/download/details.aspx?id=30005) (адреплстатус), бесплатное средство, отслеживающее состояние репликации контроллеров домена и сообщающих об ошибках. Для Адреплстатус требуется .NET Framework 4, который будет установлен, если он еще не указан.  

Проверьте репликация DFS log в Просмотр событий для события с ИДЕНТИФИКАТОРом 4602 (или события службы репликации файлов 13516), которое указывает, что SYSVOL инициализирован.  

Если первый восстановленный контроллер домена регистрирует событие с кодом 4614 ("контроллер домена ожидает выполнения начальной репликации. Реплицированная папка останется в состоянии начальной синхронизации до тех пор, пока она не будет реплицирована с партнером "") в журнал репликация DFS, а событие с ИДЕНТИФИКАТОРом 4602 не отображается, и необходимо выполнить следующие действия по восстановлению SYSVOL, если он реплицируется с помощью DFSR:  

1. Когда событие DFSR 4612 появляется на первом восстановленном контроллере домена, выполните принудительное восстановление вручную, как описано в [2218556: как принудительно выполнить полномочное и неполномочное синхронизацию для реплицированного SYSVOL (например, "D4/D2" для FRS)](https://support.microsoft.com/kb/2218556) (https://support.microsoft.com/kb/2218556).  
2. Установите для **флага сисволреади** значение 1 вручную, как описано в [947022. общий ресурс NETLOGON отсутствует после установки домен Active Directory Services на новом полном или доступном только для чтения контроллере домена на базе Windows Server 2008](https://support.microsoft.com/kb/947022).  

Можно также создать диагностический отчет репликация DFS. Дополнительные сведения см. [в разделе Создание диагностического отчета для репликация DFS](https://technet.microsoft.com/library/cc754227.aspx) и пошагового [руководств по DFS для Windows Server 2008](https://technet.microsoft.com/library/cc732863\(WS.10\).aspx). Если сервер работает под Windows Server 2008 R2, можно использовать [параметр командной строки Dfsrdiag. exe ReplicationState](https://blogs.technet.com/b/filecab/archive/2009/05/28/dfsrdiag-exe-replicationstate-what-s-dfsr-up-to.aspx).  

Можно также запустить тест репликации с помощью программы Dcdiag. exe, чтобы проверить наличие ошибок репликации. Дополнительные сведения см. в статье базы знаний [249256](https://support.microsoft.com/kb/249256).

## <a name="next-steps"></a>Следующие шаги

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
