---
title: Dfsdiag TestReferral
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: cd1b87befa8a9cfda5ea27a4ce5a5105ea1a1009
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59848025"
---
# <a name="dfsdiag-testreferral"></a>Dfsdiag TestReferral

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Распределенная файловая система проверяет \(DFS\) ссылок, выполняя следующие тесты:  
  
-   При использовании параметра DFSpath без аргументов, эта команда проверяет, что список ссылок включает всех доверенных доменов.  
  
-   Когда домен указан, команда выполняет проверку работоспособности контроллеров домена \(dfsdiag \/testdcs\) и проверяет связи с сайтами, а кэш домена локального узла.  
  
-   При указании домена и \\SYSvol или \\сетевого входа в СИСТЕМУ, а также выполнять же работоспособности проверяет, если домен указан, команда проверяет, что время жизни \(TTL\) отсылок SYSvol и NETLOGON соответствует значению по умолчанию 900 секунд.  
  
-   При указании корневого пространства имен, а также выполнять же работоспособности проверяет, когда домен указан, команда выполняет проверку конфигурации DFS \(dfsdiag \/TestDFSConfig\) и проверку целостности пространства имен \(dfsdiag \/TestDFSIntegrity\).  
  
-   При указании папки DFS \(ссылку\), а также выполнять проверки же работоспособности, как при указании корневого пространства имен, команда проверяет конфигурацию сайта на папки, \(dfsdiag \/ testsites\) и проверяет связь с сайтом локального узла.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestReferral /DFSpath:<DFS path for getting referrals> [/Full]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|\/DFSpath:<path for getting referrals>|Этот путь DFS может принимать одно из следующих:<br /><br />-   \(пустой\): Тесты доверенных доменов.<br />-   \\\\Домен: Отсылки контроллера домена.<br />-   \\\\Домен\\SYSvol: Отсылки SYSvol.<br />-   \\\\Домен\\сетевого входа в СИСТЕМУ: Отсылки NETLOGON.<br />-   \\\\<Domain or server>\\<Namespace Root>: Ссылки на корень пространства имен.<br />-   \\\\<Domain or server>\\<Namespace root>\\<DFS folder>: Папки DFS \(ссылку\) отсылки.|  
|\/Полный|Применить только к домена и корневых ссылок. Проверяет согласованность сведений о сайте ассоциации между реестра и доменных служб active directory \(AD DS\).|  
  
## <a name="BKMK_Examples"></a>Примеры  
Чтобы подлежит Уточнению введите:  
  
```  
dfsdiag /TestReferral /DFSpath:\\Contoso.com\MyNamespace  
```  
  
Чтобы подлежит Уточнению введите:  
  
```  
dfsdiag /TestReferral /DFSpath:  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  

