---
title: дфсдиаг Тестдкс
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: abb915ab-23eb-45d7-9a2e-b6b9a5756a70
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a193e68b6f015b1535a98e20b52deb2a4a14034c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378441"
---
# <a name="dfsdiag-testdcs"></a>дфсдиаг Тестдкс

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию контроллеров домена, выполняя следующие тесты на каждом контроллере домена в указанном домене:  
  
-   проверяет, что распределенная файловая система \(служба пространства имен\) DFS запущена, а для ее типа запуска задано значение "автоматически".  
  
-   Проверяет поддержку веб-сайтов\-с затратами для NETLOGON и SYSvol.  
  
-   проверяет согласованность связи сайтов по имени узла и IP-адресу.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestDCs [/Domain:<Domain name>]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|Домен \/:<Domain name>|Домен, который требуется проверить.|  
  
## <a name="remarks"></a>Замечания  
\/Domain является необязательным параметром. Значение по умолчанию — локальный домен, к которому присоединен локальный узел.  
  
## <a name="BKMK_Examples"></a>Примеров  
Чтобы проверить конфигурацию контроллеров домена в домене Contoso.com, введите:  
  
```  
dfsdiag /TestDCs /Domain:Contoso.com  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [дфсдиаг](dfsdiag.md)  
  

