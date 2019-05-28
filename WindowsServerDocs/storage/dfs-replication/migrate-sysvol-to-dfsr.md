---
Title: Перенос репликации SYSVOL в репликацию DFS
ms.date: 07/02/2012
ms.prod: windows-server-threshold
ms.technology: storage
author: JasonGerend
manager: elizapo
ms.author: jgerend
ms.openlocfilehash: da581ee0c5ee05d5e169496908e1cf3bd1a7f5dc
ms.sourcegitcommit: 2977c707a299929c6ab0d1e0adab2e1c644b8306
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63738541"
---
# <a name="migrate-sysvol-replication-to-dfs-replication"></a>Перенос репликации SYSVOL в репликацию DFS


Обновлено: 25 августа 2010 г.

Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

Контроллеры домена используют специальные общей папке SYSVOL для репликации сценариев входа в систему, а также файлы объектов групповой политики на другие контроллеры домена. Windows 2000 Server и Windows Server 2003 используют службы репликации файлов (FRS) для репликации SYSVOL, в то время как Windows Server 2008 использует более новые службы репликации DFS в доменах, используйте режим работы домена Windows Server 2008 и FRS для доменов, Запустите старые режимы работы домена.

Использовать репликацию DFS для репликации папки SYSVOL, можно создать новый домен, который использует режим работы домена Windows Server 2008, или можно использовать процедуру, которая рассматривается в этом документе, для обновления существующего домена и переноса репликации Репликация DFS.

В этом документе предполагается, что у вас есть базовые знания о доменных службах Active Directory (AD DS), FRS и репликации распределенной файловой системы (репликация DFS). Дополнительные сведения см. в разделе [Обзор доменных служб Active Directory](http://go.microsoft.com/fwlink/?linkid=147787), [Обзор FRS](http://go.microsoft.com/fwlink/?linkid=121763), или [Общие сведения о репликации DFS](http://go.microsoft.com/fwlink/?linkid=121762)


> [!NOTE]
> Чтобы загрузить версия этого руководства, посетите <a href="http://go.microsoft.com/fwlink/?linkid=150375">руководство по миграции репликации SYSVOL: FRS на DFS</a> ()http://go.microsoft.com/fwlink/?LinkId=150375)
<br>


## <a name="in-this-guide"></a>В данном руководстве

[Общие сведения о миграции SYSVOL](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd640170(v=ws.10))

  - [SYSVOL состояниям миграции](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd641052(v=ws.10))  
      
  - [Обзор процедуры миграции SYSVOL](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639809(v=ws.10))  
      

[Процедуры миграции SYSVOL](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639860(v=ws.10))

  - [Миграция в состоянии подготовки](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd641193(v=ws.10))  
      
  - [Переход на перенаправленном состояние](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd641340(v=ws.10))  
      
  - [Переход на исключенные состояние](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd640254(v=ws.10))  
      

[Устранение неполадок при миграции SYSVOL](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd640395(v=ws.10))

  - [SYSVOL Устранение неполадок при миграции](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639976(v=ws.10))  
      
  - [Откат миграции SYSVOL в предыдущее состояние стабильная версия](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd640509(v=ws.10))  
      

[Справочные сведения миграции SYSVOL](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd640293(v=ws.10))

  - [SYSVOL поддерживаемых сценариев миграции](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639854(v=ws.10))  
      
  - [Проверка состояния миграции SYSVOL](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639789(v=ws.10))  
      
  - [DFSRMIG](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd641227(v=ws.10))  
      
  - [Действия средство миграции SYSVOL](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd639712(v=ws.10))  
      

## <a name="additional-references"></a>Дополнительная справка

[Серия миграции SYSVOL. Часть 1 — Введение в процесс миграции SYSVOL](http://go.microsoft.com/fwlink/?linkid=121756)

[Серия миграции SYSVOL. Часть 2—Dfsrmig.exe: Средство миграции SYSVOL](http://go.microsoft.com/fwlink/?linkid=121757)

[Серия миграции SYSVOL. Часть 3 — переход в состояние «ПОДГОТОВКА»](http://go.microsoft.com/fwlink/?linkid=121758)

[Серия миграции SYSVOL. Часть 4 — переход в состояние «ПЕРЕНАПРАВЛЕННЫЙ»](http://go.microsoft.com/fwlink/?linkid=121759)

[Серия миграции SYSVOL. Часть 5 — переход в состояние «Удалить»](http://go.microsoft.com/fwlink/?linkid=121760)

[Пошаговое руководство по распределенной файловой системы в Windows Server 2008](http://go.microsoft.com/fwlink/?linkid=85231)

[Техническое руководство по FRS](http://go.microsoft.com/fwlink/?linkid=121764)

