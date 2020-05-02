---
title: дфсдиаг Тестдфсконфиг
description: Справочный раздел по дфсдиаг Тестдфсконфиг, который проверяет конфигурацию пространства имен распределенная файловая система (DFS).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 106aeeb9-ea79-4e6e-829c-eca06309bab2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 057b0662fddb7148837be16380d190cdb37382c5
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719588"
---
# <a name="dfsdiag-testdfsconfig"></a>дфсдиаг Тестдфсконфиг

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
  
## <a name="examples"></a>Примеры  
  
```  
dfsdiag /TestDFSConfig /DFSRoot:\\Contoso.com\MyNamespace  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [дфсдиаг](dfsdiag.md)  
  

