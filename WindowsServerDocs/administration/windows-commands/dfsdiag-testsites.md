---
title: дфсдиаг Тестситес
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 39a0d415-7eb7-4a26-861b-7ff00c45dcda
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: af72da64dd20d4b37824355a494cb8f97f597b28
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378389"
---
# <a name="dfsdiag-testsites"></a>дфсдиаг Тестситес

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию доменных служб Active Directory \(AD DS сайтов\), проверяя, что серверы, действующие в качестве серверов пространства имен или папки \(ссылки\), имеют одинаковые связи сайтов на всех контроллерах домена.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestSites </Machine:<server name>| /DFSpath:<namespace root or DFS folder> [/Recurse]> [/Full]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|\/машины:<server name>|Имя сервера, на котором необходимо проверить связь сайта.|  
|\/Дфспас:<namespace root or DFS folder>|Корень пространства имен или распределенная файловая система \(папку\) DFS \(ссылку\) с целевыми объектами, для которых необходимо проверить связь сайта.|  
|\/рекурсия|Перечисляет и проверяет связи сайтов для всех целевых объектов папки в указанном корне пространства имен.|  
|\/полный|проверяет, что AD DS и реестр сервера содержат одинаковые сведения о взаимосвязи сайтов.|  
  
## <a name="BKMK_Examples"></a>Примеров  
Для УТОЧНЕНия введите:  
  
```  
dfsdiag /TestSites /Machine:MyServer  
```  
  
Для УТОЧНЕНия введите:  
  
```  
dfsdiag /TestSites /DFSpath:\\Contoso.com\Namespace1\Folder1 /Full  
```  
  
Для УТОЧНЕНия введите:  
  
```  
dfsdiag /TestSites /DFSpath:\\Contoso.com\Namespace2 /Recurse /Full  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [дфсдиаг](dfsdiag.md)  
  

