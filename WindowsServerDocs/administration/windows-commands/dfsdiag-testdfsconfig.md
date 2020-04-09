---
title: дфсдиаг Тестдфсконфиг
description: Раздел команд Windows для дфсдиаг Тестдфсконфиг, который проверяет конфигурацию пространства имен распределенная файловая система (DFS).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 106aeeb9-ea79-4e6e-829c-eca06309bab2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ffb75ba26b4ed90dbf5c8bfda80f4a81f986e46a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846337"
---
# <a name="dfsdiag-testdfsconfig"></a>дфсдиаг Тестдфсконфиг

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию пространства имен распределенная файловая система (DFS), выполняя следующие действия.  
  
-   Проверяет, что служба пространства имен DFS запущена и для нее задан тип запуска автоматически на всех серверах пространства имен.  
  
-   Проверяет, является ли конфигурация реестра DFS согласованной между серверами пространства имен.  
  
-   Проверяет следующие зависимости на серверах кластеризованных пространств имен, работающих под Windows Server 2008 или более поздней версии:  
  
    -   Зависимость корневого ресурса пространства имен от ресурса сетевого имени.  
  
    -   Зависимость ресурса сетевого имени от ресурса IP-адреса.  
  
    -   Зависимость корневого ресурса пространства имен от ресурса физического диска.

## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestDFSConfig /DFSRoot:<namespace>  
```  
  
#### <a name="parameters"></a>Параметры  
  
|       Параметр       |               Описание               |
|-----------------------|-----------------------------------------|
| /Дфсрут:`<namespace>` | Пространство имен (корень DFS) для диагностики. |
  
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
  
```  
dfsdiag /TestDFSConfig /DFSRoot:\\Contoso.com\MyNamespace  
```  
  
## <a name="additional-references"></a>Дополнительные материалы  
  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [дфсдиаг](dfsdiag.md)  
  

