---
title: dfsdiag TestDFSConfig
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 922b78b87f3bb66765b87348a3bf136e14c9e837
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436132"
---
# <a name="dfsdiag-testdfsconfig"></a>dfsdiag TestDFSConfig

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию распределенной файловой системы \(DFS\) пространства имен, выполнив следующие действия:  
  
-   проверяет, что службу пространств имен DFS запущена и что тип запуска установлен Авто на всех серверах пространства имен.  
  
-   Проверяет согласованность между серверами пространства имен DFS конфигурации реестра.  
  
-   Проверяет следующие зависимости на кластеризованных пространство имен серверов, работающих под управлением Windows Server 2008 или более поздней версии:  
  
    -   Пространство имен корневого зависимости ресурса для ресурса сетевого имени.  
  
    -   Сети имя ресурса зависимость от ресурса IP-адреса.  
  
    -   Зависимости ресурса корневого пространства имен на ресурс физического диска.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestDFSConfig /DFSRoot:<namespace>  
```  
  
### <a name="parameters"></a>Параметры  
  
|       Параметр       |               Описание               |
|-----------------------|-----------------------------------------|
| \/DFSRoot:<namespace> | Пространство имен \(корень DFS\) для диагностики. |
  
## <a name="BKMK_Examples"></a>Примеры  
Чтобы подлежит Уточнению введите:  
  
```  
dfsdiag /TestDFSConfig /DFSRoot:\\Contoso.com\MyNamespace  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [dfsdiag](dfsdiag.md)  
  

