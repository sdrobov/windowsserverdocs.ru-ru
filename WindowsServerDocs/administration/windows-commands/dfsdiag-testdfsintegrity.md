---
title: dfsdiag TestDFSIntegrity
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 173ee832-26e1-4ec8-a23a-38a7d6229ac3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9a79e034f7c60be89266eb29dcd69e8f73b2aafe
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59837095"
---
# <a name="dfsdiag-testdfsintegrity"></a>dfsdiag TestDFSIntegrity

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет целостность распределенной файловой системы \(DFS\) пространства имен, выполняя следующие тесты:  
  
-   Проверяет наличие DFS повреждение метаданных или несоответствий между контроллерами домена.  
  
-   Проверяет конфигурацию доступа\-перечисление, чтобы обеспечить согласованность между DFS метаданные общего ресурса сервера имен на основе.  
  
-   Обнаруживает вложенные папки DFS \(ссылки\), повторяющиеся папки и папки с перекрывающимися целевым объектам папки.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestDFSIntegrity /DFSRoot:<DFS root path> [/Recurse] [/Full]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|\/DFSRoot:<DFS root path>|Пространство имен DFS для диагностики.|  
|\/Recurse|Выполняет тестирования, в том числе сцеплений пространства имен.|  
|\/Полный|Проверяет согласованность общего ресурса и конфигурация на стороне списки управления доступом NTFS и клиента на все целевые объекты папки. Он также проверяет, что online свойству.|  
  
## <a name="BKMK_Examples"></a>Примеры  
Чтобы подлежит Уточнению введите:  
  
```  
dfsdiag /TestDFSIntegrity /DFSRoot:\\Contoso.com\MyNamespace /Recurse /Full  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  
-   [dfsdiag](dfsdiag.md)  
  

