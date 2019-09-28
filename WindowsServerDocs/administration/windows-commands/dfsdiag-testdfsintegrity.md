---
title: дфсдиаг Тестдфсинтегрити
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 7f344e2d1fecc542efc39688f20165fd3e39a04a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378428"
---
# <a name="dfsdiag-testdfsintegrity"></a>дфсдиаг Тестдфсинтегрити

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет целостность пространства имен распределенная файловая система \(DFS @ no__t-1, выполняя следующие тесты:  
  
-   Проверяет наличие повреждений метаданных DFS или несоответствий между контроллерами домена.  
  
-   Проверяет конфигурацию перечисления доступа @ no__t-0based, чтобы обеспечить согласованность между метаданными DFS и общим ресурсом сервера пространства имен.  
  
-   Обнаруживает перекрывающиеся папки DFS \(links @ no__t-1, дублирующиеся папки и папки с перекрывающимися целевыми объектами папок.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestDFSIntegrity /DFSRoot:<DFS root path> [/Recurse] [/Full]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|\/DFSRoot: <DFS root path>|Пространство имен DFS для диагностики.|  
|@no__t 0Recurse|Выполняет тестирование, включая взаимосвязи пространств имен.|  
|@no__t 0Full|проверяет согласованность общего ресурса и ACL NTFS и конфигурации клиента для всех целевых объектов папки. Он также проверяет, задано ли свойство Online.|  
  
## <a name="BKMK_Examples"></a>Примеров  
Для УТОЧНЕНия введите:  
  
```  
dfsdiag /TestDFSIntegrity /DFSRoot:\\Contoso.com\MyNamespace /Recurse /Full  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [дфсдиаг](dfsdiag.md)  
  

