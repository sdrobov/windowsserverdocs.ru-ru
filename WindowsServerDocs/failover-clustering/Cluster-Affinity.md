---
title: Сходство кластера
ms.prod: windows-server-threshold
ms.manager: eldenc
ms.technology: failover-clustering
ms.topic: article
author: johnmarlin-msft
ms.date: 03/07/2019
description: В этой статье описаны уровни сходства и antiAffinity кластера отработки отказа
ms.openlocfilehash: a38d53f6aed1ca634d41822f4486779f6d279ec0
ms.sourcegitcommit: ed27ddbe316d543b7865bc10590b238290a2a1ad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476053"
---
# <a name="cluster-affinity"></a>Сходство кластера

> Относится к: Windows Server 2019, Windows Server 2016

Отказоустойчивый кластер может содержать множество ролей, которые можно перемещать между узлами и выполнения.  Бывают случаи, когда определенных ролей (т. е. виртуальные машины, группы ресурсов, и т.д.) не следует запускать на одном узле.  Это может быть вызвано потребление ресурсов, использование памяти и т. д.  Например существуют две виртуальные машины, которые являются загружать память и Процессор, и если две виртуальные машины запущены на одном узле, одно или несколько виртуальных машин может иметь влияние проблем с производительностью.  В этой статье объясняется кластера antiaffinity уровни и как их использовать.

## <a name="what-is-affinity-and-antiaffinity"></a>Что такое соответствие и AntiAffinity?

Сходство — которые можно настроить правило, которое устанавливает связь между двумя или более ролями (i, e, виртуальные машины, группы ресурсов, и т.д.) продолжать их друг с другом.  AntiAffinity одинаков, но используется попробовать и сохранить указанных ролей друг от друга.  Отказоустойчивые кластеры использовать AntiAffinity для ролей.  В частности [AntiAffinityClassNames](https://docs.microsoft.com/previous-versions/windows/desktop/mscs/groups-antiaffinityclassnames) параметра, определенного в роли, поэтому они не выполняются на одном узле.  

## <a name="antiaffinityclassnames"></a>AntiAffinityClassnames

При просмотре свойств группы, является параметром-AntiAffinityClassNames и раздел будет пустым по умолчанию.  В приведенных ниже примерах Group1 "и" Group2 должны быть отделены от запуска на одном узле.  Чтобы просмотреть свойства, будет команду PowerShell, а результат:

    PS> Get-ClusterGroup Group1 | fl AntiAffinityClassNames
    AntiAffinityClassNames : {}

    PS> Get-ClusterGroup Group2 | fl AntiAffinityClassNames
    AntiAffinityClassNames : {}

Так как AntiAffinityClassNames не определены по умолчанию, эти роли могут выполнения друг с другом или друг от друга.  Цель — продолжать их необходимости разделять.  Значение для AntiAffinityClassNames может быть все, что вы можете предоставить к ним, должны быть одинаковыми.  Предположим, что Group1 "и" Group2 являются контроллерами домена, работающих на виртуальных машинах, и они будут лучше всего работать работающих на разных узлах.  Так как они являются контроллерами домена, я буду использовать контроллер домена, имени класса.  Чтобы задать значение, будет команду PowerShell, а результаты:

    PS> $AntiAffinity = New-Object System.Collections.Specialized.StringCollection
    PS> $AntiAffinity.Add("DC")
    PS> (Get-ClusterGroup -Name "Group1").AntiAffinityClassNames = $AntiAffinity
    PS> (Get-ClusterGroup -Name "Group2").AntiAffinityClassNames = $AntiAffinity

    PS> Get-ClusterGroup "Group1" | fl AntiAffinityClassNames
    AntiAffinityClassNames : {DC}

    PS> Get-ClusterGroup "Group2" | fl AntiAffinityClassNames
    AntiAffinityClassNames : {DC}

Теперь, когда они заданы, отказоустойчивая кластеризация попытается оставить их друг от друга.  

Параметр AntiAffinityClassName является блоком «мягкий».  Это означает, что он попытается оставить их друг от друга, но если это невозможно, он по-прежнему сможет их выполнение на одном узле.  Например группы работают на отказоустойчивый кластер с двумя узлами.  Если один узел должен стать недоступной для обслуживания, это означает, обе группы будет запущен и работает на одном узле.  В этом случае было бы на этом компьютере.  Может оказаться самым эффективным, но обе машины virtial будут все еще выполняется в пределах приемлемой производительности.

## <a name="i-need-more"></a>Мне нужно нечто большее

Как уже упоминалось, AntiAffinityClassNames является Мягкая блокировка.  Но что делать, если требуется жесткую блокировку?  Виртуальные машины не может выполняться на он же узла; в противном случае — влияние на производительность, могут возникать и вызвать некоторых служб возможно выключиться.

В таких случаях имеется свойство дополнительной кластерной ClusterEnforcedAntiAffinity.  Этот уровень antiaffinity помешают любой ценой какие-либо же значения AntiAffinityClassNames выполняться на одном узле.

Чтобы просмотреть свойства и значения, будет команду PowerShell (и результат):

    PS> Get-Cluster | fl ClusterEnforcedAntiAffinity
    ClusterEnforcedAntiAffinity : 0

Значение «0» означает, что она отключена, а не применяться.  Значение «1» включает его и жесткая блокировка.  Чтобы включить этот жесткую блокировку, команда (и результат) является:

    PS> (Get-Cluster).ClusterEnforcedAntiAffinity = 1
    ClusterEnforcedAntiAffinity : 1

Если они заданы, группе сможет одновременно подключиться к сети.  Если они установлены на одном узле, это отображается в диспетчере отказоустойчивости кластеров.

![Сходство кластера](media\Cluster-Affinity\Cluster-Affinity-1.png)

В PowerShell групп списка, в котором будет видеть это:

    PS> Get-ClusterGroup

    Name       State
    ----       -----
    Group1     Offline(Anti-Affinity Conflict)
    Group2     Online

## <a name="additional-comments"></a>Дополнительные комментарии

- Убедитесь, что вы используете верную установку параметра AntiAffinity в зависимости от потребностей.
- Имейте в виду, что в сценарии с двумя узлами ClusterEnforcedAntiAffinity, если один узел не работает, обеих групп не будет запущен.  

- Использование предпочитаемые владельцы групп могут сочетаться с AntiAffinity в кластер с тремя или более узлами.
- Настройки AntiAffinityClassNames и ClusterEnforcedAntiAffinity будет только выполнено после перезагрузки ресурсов. Т. Е. можно установить их, но если обе группы находятся в оперативном режиме на одном узле при установке, они продолжат оставаться в сети.



