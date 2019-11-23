---
title: дфсдиаг Тестдфсконфиг
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 106aeeb9-ea79-4e6e-829c-eca06309bab2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8008e02d588edaa6fe7700a331c43f9680d89431
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378418"
---
# <a name="dfsdiag-testdfsconfig"></a>дфсдиаг Тестдфсконфиг

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию распределенная файловая система \(пространства имен\) DFS, выполняя следующие действия.  
  
-   проверяет, что служба пространства имен DFS запущена и для нее задан тип запуска автоматически на всех серверах пространства имен.  
  
-   проверяет, является ли конфигурация реестра DFS согласованной между серверами пространства имен.  
  
-   Проверяет следующие зависимости на серверах кластеризованных пространств имен, работающих под Windows Server 2008 или более поздней версии:  
  
    -   Зависимость корневого ресурса пространства имен от ресурса сетевого имени.  
  
    -   Зависимость ресурса сетевого имени от ресурса IP-адреса.  
  
    -   Зависимость корневого ресурса пространства имен от ресурса физического диска.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestDFSConfig /DFSRoot:<namespace>  
```  
  
### <a name="parameters"></a>Параметры  
  
|       Параметр       |               Описание               |
|-----------------------|-----------------------------------------|
| \/Дфсрут:<namespace> | Пространство имен \(корневой\) DFS для диагностики. |
  
## <a name="BKMK_Examples"></a>Примеров  
Для УТОЧНЕНия введите:  
  
```  
dfsdiag /TestDFSConfig /DFSRoot:\\Contoso.com\MyNamespace  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [дфсдиаг](dfsdiag.md)  
  

