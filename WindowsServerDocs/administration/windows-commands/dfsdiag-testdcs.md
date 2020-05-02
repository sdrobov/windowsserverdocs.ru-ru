---
title: дфсдиаг Тестдкс
description: Справочный раздел по дфсдиаг Тестдкс, который проверяет конфигурацию контроллеров домена в указанном домене.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: abb915ab-23eb-45d7-9a2e-b6b9a5756a70
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6ac7fe1a7bae6a7b3dab9004b6212b7d93774ade
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719594"
---
# <a name="dfsdiag-testdcs"></a>дфсдиаг Тестдкс

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
|Поддомен`<domain_name>`|Домен, который требуется проверить.|  
  
## <a name="remarks"></a>Примечания  

/Domain — необязательный параметр. Значение по умолчанию — локальный домен, к которому присоединен локальный узел.  
  
## <a name="examples"></a>Примеры  
Чтобы проверить конфигурацию контроллеров домена в домене Contoso.com, введите:  
  
```  
dfsdiag /TestDCs /Domain:Contoso.com  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [дфсдиаг](dfsdiag.md)  
  

