---
title: dfsdiag TestSites
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 6486c79cfa58bb262fd3161ad0801e84185b6629
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873975"
---
# <a name="dfsdiag-testsites"></a>dfsdiag TestSites

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию доменных служб active directory \(AD DS\) узлов путем проверки, необходимые для сервера, которые действуют как серверы пространства имен или папке \(ссылку\) целевых объектов имеет те же связи сайта в домене все контроллеры.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestSites </Machine:<server name>| /DFSpath:<namespace root or DFS folder> [/Recurse]> [/Full]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|\/Компьютер:<server name>|Имя сервера, на котором проверить связь с сайтом.|  
|\/DFSpath:<namespace root or DFS folder>|Корень пространства имен или распределенной файловой системы \(DFS\) папку \(ссылку\) с целевыми объектами, для которого необходимо проверить связь с сайтом.|  
|\/Recurse|Перечисляет и проверяет, связи с сайтами для всех целевых объектов папку в корневом каталоге указанного пространства имен.|  
|\/Полный|проверяет, что AD DS и реестра сервера содержат те же сведения связи сайта.|  
  
## <a name="BKMK_Examples"></a>Примеры  
Чтобы подлежит Уточнению введите:  
  
```  
dfsdiag /TestSites /Machine:MyServer  
```  
  
Чтобы подлежит Уточнению введите:  
  
```  
dfsdiag /TestSites /DFSpath:\\Contoso.com\Namespace1\Folder1 /Full  
```  
  
Чтобы подлежит Уточнению введите:  
  
```  
dfsdiag /TestSites /DFSpath:\\Contoso.com\Namespace2 /Recurse /Full  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  
-   [dfsdiag](dfsdiag.md)  
  

