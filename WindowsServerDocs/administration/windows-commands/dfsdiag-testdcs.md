---
title: Dfsdiag TestDCs
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 62956ae65d2311939ac0db6a4b86950f21dba407
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59836605"
---
# <a name="dfsdiag-testdcs"></a>Dfsdiag TestDCs

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию контроллеров домена, выполняя следующие тесты на каждом контроллере домена в указанном домене:  
  
-   проверяет, что распределенная файловая система \(DFS\) пространства имен служба запущена, и установлен тип запуска Авто.  
  
-   Проверяет, для поддержки сайта\-оценена ссылки для входа в сеть и SYSvol.  
  
-   Проверяет согласованность связь с сайтом, имя узла и IP-адрес.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestDCs [/Domain:<Domain name>]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|\/Домен:<Domain name>|Домен, который требуется проверить.|  
  
## <a name="remarks"></a>Примечания  
\/Домен — необязательный параметр. Значение по умолчанию является локальным доменом, которому присоединен локальный узел.  
  
## <a name="BKMK_Examples"></a>Примеры  
Чтобы проверить конфигурацию контроллеров домена в домене Contoso.com, введите:  
  
```  
dfsdiag /TestDCs /Domain:Contoso.com  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  
-   [dfsdiag](dfsdiag.md)  
  

