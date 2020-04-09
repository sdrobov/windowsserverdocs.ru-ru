---
title: дфсдиаг Тестситес
description: Команды Windows для дфсдиаг Тестситес, которые проверяют конфигурацию сайтов доменных служб Active Directory (AD DS), проверяя, что серверы, выполняющие роль серверов пространства имен или целевых объектов (ссылок), имеют одинаковые связи сайтов на всех контроллерах домена.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39a0d415-7eb7-4a26-861b-7ff00c45dcda
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 80cc9095748dafb030b204130bfa2ccb61ec69ea
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846227"
---
# <a name="dfsdiag-testsites"></a>дфсдиаг Тестситес

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию сайтов доменных служб Active Directory (AD DS), убедившись, что серверы, действующие как серверы пространства имен или целевые объекты папки (ссылки), имеют одинаковые связи сайтов на всех контроллерах домена.

## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestSites </Machine:<server name>| /DFSpath:<namespace root or DFS folder> [/Recurse]> [/Full]  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|\/машины:<server name>|Имя сервера, на котором необходимо проверить связь сайта.|  
|\/Дфспас:<namespace root or DFS folder>|Корневая папка пространства имен или распределенная файловая система (DFS) (ссылка) с целевыми объектами, для которых необходимо проверить связь сайта.|  
|\/рекурсия|Перечисляет и проверяет связи сайтов для всех целевых объектов папки в указанном корне пространства имен.|  
|\/полный|проверяет, что AD DS и реестр сервера содержат одинаковые сведения о взаимосвязи сайтов.|  
  
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
  
```  
dfsdiag /TestSites /Machine:MyServer  
```  
 
```  
dfsdiag /TestSites /DFSpath:\\Contoso.com\Namespace1\Folder1 /Full  
```  
  
```  
dfsdiag /TestSites /DFSpath:\\Contoso.com\Namespace2 /Recurse /Full  
```  
  
## <a name="additional-references"></a>Дополнительные материалы  
  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [дфсдиаг](dfsdiag.md)  
  

