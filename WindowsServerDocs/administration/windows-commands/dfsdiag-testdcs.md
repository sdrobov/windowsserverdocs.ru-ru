---
title: дфсдиаг Тестдкс
description: Раздел команд Windows для дфсдиаг Тестдкс, который проверяет конфигурацию контроллеров домена в указанном домене.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: abb915ab-23eb-45d7-9a2e-b6b9a5756a70
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 092ce3710eb6d209f596683bd4ad054dadd11aa3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846325"
---
# <a name="dfsdiag-testdcs"></a>дфсдиаг Тестдкс

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет конфигурацию контроллеров домена, выполняя следующие тесты на каждом контроллере домена в указанном домене:  
  
-   Проверяет, запущена ли служба пространства имен распределенная файловая система (DFS), и имеет ли ее тип запуска значение "автоматически".  
  
-   Проверяет поддержку ссылок на веб-сайт для NETLOGON и SYSvol.  
  
-   Проверяет согласованность связи сайтов по имени узла и IP-адресу.

## <a name="syntax"></a>Синтаксис  
  
```  
dfsdiag /TestDCs [/Domain:<Domain name>]  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|/Domain:`<domain_name>`|Домен, который требуется проверить.|  
  
## <a name="remarks"></a>Примечания  

/Domain — необязательный параметр. Значение по умолчанию — локальный домен, к которому присоединен локальный узел.  
  
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Чтобы проверить конфигурацию контроллеров домена в домене Contoso.com, введите:  
  
```  
dfsdiag /TestDCs /Domain:Contoso.com  
```  
  
## <a name="additional-references"></a>Дополнительные материалы  
  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [дфсдиаг](dfsdiag.md)  
  

