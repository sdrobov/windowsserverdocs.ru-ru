---
title: дфсдиаг Тестситес
description: Справочный раздел по дфсдиаг Тестситес, который проверяет конфигурацию сайтов доменных служб Active Directory (AD DS) путем проверки того, что серверы, действующие в качестве целевых объектов сервера пространства имен или папки (ссылки), имеют одинаковые связи сайтов на всех контроллерах домена.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39a0d415-7eb7-4a26-861b-7ff00c45dcda
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 68048699a812beac94fa121d6801da5f42e5393b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719553"
---
# <a name="dfsdiag-testsites"></a>дфсдиаг Тестситес

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию сайтов доменных служб Active Directory (AD DS), убедившись, что серверы, действующие как серверы пространства имен или целевые объекты папки (ссылки), имеют одинаковые связи сайтов на всех контроллерах домена.

## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestSites </Machine:<server name>| /DFSpath:<namespace root or DFS folder> [/Recurse]> [/Full]  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|\/Машине<server name>|Имя сервера, на котором необходимо проверить связь сайта.|  
|\/Дфспас:<namespace root or DFS folder>|Корневая папка пространства имен или распределенная файловая система (DFS) (ссылка) с целевыми объектами, для которых необходимо проверить связь сайта.|  
|\/Recurse|Перечисляет и проверяет связи сайтов для всех целевых объектов папки в указанном корне пространства имен.|  
|\/Полный|проверяет, что AD DS и реестр сервера содержат одинаковые сведения о взаимосвязи сайтов.|  
  
## <a name="examples"></a>Примеры  
  
```  
dfsdiag /TestSites /Machine:MyServer  
```  
 
```  
dfsdiag /TestSites /DFSpath:\\Contoso.com\Namespace1\Folder1 /Full  
```  
  
```  
dfsdiag /TestSites /DFSpath:\\Contoso.com\Namespace2 /Recurse /Full  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [дфсдиаг](dfsdiag.md)  
  

