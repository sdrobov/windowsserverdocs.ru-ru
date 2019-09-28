---
title: bootcfg
description: Раздел команд Windows для **bootcfg** — настраивает, запрашивает или изменяет параметры файла Boot. ini.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3deb354c-5717-4066-bc79-b9323d559e44
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2d66296327a2221093e5434f69e15e7c55df1f6b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379853"
---
# <a name="bootcfg"></a>bootcfg

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Настраивает, запрашивает или изменяет параметры файла Boot. ini.  
## <a name="syntax"></a>Синтаксис  
```  
bootcfg <parameter> [arguments...]  
```  
## <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|[bootcfg addsw](bootcfg-addsw.md)|Добавляет параметры загрузки операционной системы для указанной записи операционной системы.|  
|[bootcfg copy](bootcfg-copy.md)|Создает копию существующей записи загрузки, в которую можно добавить параметры командной строки.|  
|[bootcfg dbg1394](bootcfg-dbg1394.md)|Настраивает отладку порта 1394 для указанной записи операционной системы.|  
|[bootcfg debug](bootcfg-debug.md)|Добавляет или изменяет параметры отладки для указанной записи операционной системы.|  
|[bootcfg default](bootcfg-default.md)|Указывает запись операционной системы, которую следует назначить по умолчанию.|  
|[bootcfg delete](bootcfg-delete.md)|Удаляет запись операционной системы в разделе **[Operating Systems]** файла Boot. ini.|  
|[bootcfg ems](bootcfg-ems.md)|Позволяет пользователю добавлять или изменять параметры перенаправления консоли служб аварийного управления на удаленный компьютер.|  
|[bootcfg query](bootcfg-query.md)|Запрашивает и отображает записи разделов [boot loader] и **[Operating Systems]** из Boot. ini.|  
|[bootcfg raw](bootcfg-raw.md)|Добавляет параметры загрузки операционной системы, указанные в виде строки, в запись операционной системы в разделе **[Operating Systems]** файла Boot. ini.|  
|[bootcfg rmsw](bootcfg-rmsw.md)|Удаляет параметры загрузки операционной системы для указанной записи операционной системы.|  
|[bootcfg timeout](bootcfg-timeout.md)|изменяет значение времени ожидания операционной системы.|  
