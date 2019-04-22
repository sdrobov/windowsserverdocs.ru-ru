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
ms.openlocfilehash: affb3c879275228fa0ec17f77ad77db6fc44d6ab
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814775"
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
  
|Параметр|Описание|  
|-------|--------|  
|\/DFSRoot:<namespace>|Пространство имен \(корень DFS\) для диагностики.|  
  
## <a name="BKMK_Examples"></a>Примеры  
Чтобы подлежит Уточнению введите:  
  
```  
dfsdiag /TestDFSConfig /DFSRoot:\\Contoso.com\MyNamespace  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  
-   [dfsdiag](dfsdiag.md)  
  

