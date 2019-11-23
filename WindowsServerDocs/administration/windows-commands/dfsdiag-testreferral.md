---
title: дфсдиаг Тестреферрал
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 877c60dc-e993-4bd5-87dd-e892e3f98a1a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: af22520d2c89f9d9f9d91ea6f43a33f3ff9c57f1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378356"
---
# <a name="dfsdiag-testreferral"></a>дфсдиаг Тестреферрал

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет распределенная файловая система \(ссылок DFS\), выполняя следующие тесты:  
  
-   При использовании параметра Дфспас без аргументов эта команда проверяет, что список ссылок включает все доверенные домены.  
  
-   При указании домена команда выполняет проверку работоспособности контроллеров домена \(дфсдиаг \/тестдкс\) и проверяет связи сайтов и кэш домена локального узла.  
  
-   При указании домена и \\SYSvol или \\NETLOGON, помимо выполнения тех же проверок работоспособности, что и при указании домена, команда проверяет, что время жизни \(TTL\) для ссылок SYSvol или NETLOGON соответствует значению по умолчанию 900 секунд.  
  
-   При указании корня пространства имен в дополнение к выполнению тех же проверок работоспособности, что и при указании домена, команда выполняет проверку конфигурации DFS \(дфсдиаг \/Тестдфсконфиг\) и проверку целостности пространства имен \(дфсдиаг \/Тестдфсинтегрити\).  
  
-   При указании папки DFS \(ссылки\), помимо выполнения тех же проверок работоспособности, что и при указании корня пространства имен, команда проверяет конфигурацию сайта для целевых объектов папки \(дфсдиаг \/тестситес\) и проверяет связь сайта с локальным узлом.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestReferral /DFSpath:<DFS path for getting referrals> [/Full]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|\/Дфспас:<path for getting referrals>|Этот путь DFS может быть одним из следующих:<br /><br />-   \(пуст\): проверяет доверенные домены.<br />-   \\\\домен: ссылки на контроллеры домена.<br />-   \\\\домена\\SYSvol: ссылки SYSvol.<br />-   \\\\домена\\NETLOGON: ссылки NETLOGON.<br />-   \\\\<Domain or server>\\<Namespace Root>: ссылки на корневые папки пространств имен.<br />-   \\\\<Domain or server>\\<Namespace root>\\<DFS folder>: папка DFS \(ссылка\) ссылок.|  
|\/полный|Применяется только к корневым и доменным ссылкам. проверяет согласованность сведений о связи сайтов между реестром и доменными службами Active Directory \(AD DS\).|  
  
## <a name="BKMK_Examples"></a>Примеров  
Для УТОЧНЕНия введите:  
  
```  
dfsdiag /TestReferral /DFSpath:\\Contoso.com\MyNamespace  
```  
  
Для УТОЧНЕНия введите:  
  
```  
dfsdiag /TestReferral /DFSpath:  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  

