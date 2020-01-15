---
title: Перенос репликации SYSVOL в репликацию DFS
ms.date: 07/02/2012
ms.prod: windows-server
ms.technology: storage
author: JasonGerend
manager: elizapo
ms.author: jgerend
ms.openlocfilehash: d8d9d47ff8f14ce316d2352729247ab2dcf4acbc
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75949703"
---
# <a name="migrate-sysvol-replication-to-dfs-replication"></a>Перенос репликации SYSVOL в репликацию DFS


Обновлено: 25 августа 2010 г.

Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Контроллеры домена используют специальную общую папку с именем SYSVOL для репликации сценариев входа в систему и групповая политика файлов объектов на другие контроллеры домена. Windows 2000 Server и Windows Server 2003 используют службу репликации файлов (FRS) для репликации SYSVOL, в то время как Windows Server 2008 использует более новую службу репликация DFS в доменах, использующих режим работы домена Windows Server 2008, и FRS для доменов, которые выполнение более старых режимов работы домена.

Чтобы использовать репликация DFS для репликации папки SYSVOL, можно либо создать новый домен, использующий режим работы домена Windows Server 2008, либо выполнить процедуру, описанную в этом документе, чтобы обновить существующий домен и перенести репликацию в. репликация DFS.

В этом документе предполагается, что у вас есть базовые знания домен Active Directory служб (AD DS), FRS и репликации распределенная файловая система (репликация DFS). Дополнительные сведения см. в статьях [Обзор служб домен Active Directory](https://go.microsoft.com/fwlink/?linkid=147787), [Обзор FRS](https://go.microsoft.com/fwlink/?linkid=121763)или [Обзор репликация DFS](https://go.microsoft.com/fwlink/?linkid=121762)


> [!NOTE]
> Чтобы скачать печатную версию этого учебника, перейдите к статье <a href="https://go.microsoft.com/fwlink/?linkid=150375">руководство по миграции репликации SYSVOL: FRS — репликация DFS</a> (https://go.microsoft.com/fwlink/?LinkId=150375)
<br>


## <a name="in-this-guide"></a>В этом руководстве

[Общие сведения о миграции SYSVOL](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd640170(v=ws.10))

  - [Состояния миграции SYSVOL](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd641052(v=ws.10))  
      
  - [Общие сведения о процедуре миграции SYSVOL](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639809(v=ws.10))  
      

[Процедура миграции SYSVOL](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639860(v=ws.10))

  - [Переход в подготовленное состояние](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd641193(v=ws.10))  
      
  - [Миграция в перенаправленное состояние](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd641340(v=ws.10))  
      
  - [Переход к исключенному состоянию](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd640254(v=ws.10))  
      

[Устранение неполадок миграции SYSVOL](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd640395(v=ws.10))

  - [Устранение неполадок, связанных с миграцией SYSVOL](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639976(v=ws.10))  
      
  - [Откат миграции SYSVOL в предыдущее стабильное состояние](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd640509(v=ws.10))  
      

[Справочные сведения о миграции SYSVOL](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd640293(v=ws.10))

  - [Поддерживаемые сценарии миграции SYSVOL](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639854(v=ws.10))  
      
  - [Проверка состояния миграции SYSVOL](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639789(v=ws.10))  
      
  - [Dfsrmig](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd641227(v=ws.10))  
      
  - [Действия средства миграции SYSVOL](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639712(v=ws.10))  
      

## <a name="additional-references"></a>Дополнительная справка

[Серия миграции SYSVOL. часть 1 — Введение в процесс миграции SYSVOL](https://go.microsoft.com/fwlink/?linkid=121756)

[Серия миграции SYSVOL: часть 2 — Dfsrmig. exe: средство миграции SYSVOL](https://go.microsoft.com/fwlink/?linkid=121757)

[Серия миграции SYSVOL: часть 3 — миграция в состояние "ПОДГОТОВЛЕНо"](https://go.microsoft.com/fwlink/?linkid=121758)

[Серия миграции SYSVOL: часть 4 — переход в состояние "перенаправлено"](https://go.microsoft.com/fwlink/?linkid=121759)

[Серия миграции SYSVOL: часть 5 — переход в состояние "удалено"](https://go.microsoft.com/fwlink/?linkid=121760)

[Пошаговое руководством для распределенных файловых систем в Windows Server 2008](https://go.microsoft.com/fwlink/?linkid=85231)

[Технический справочник по FRS](https://go.microsoft.com/fwlink/?linkid=121764)

