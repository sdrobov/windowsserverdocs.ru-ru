---
title: Восстановление
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f84f661-f3cd-48c8-bf08-87819cf626fe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 940b0931671d5f3c2137fafe4ae73b7cecd0160e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821195"
---
# <a name="repair"></a>Восстановление

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Восстанавливает RAID\-5 тома с фокусом, заменив области отказавшего диска на динамическом диске.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
repair disk=<n> [align=<n>] [noerr]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|диск\=<n>|Указывает динамический диск, который заменит неисправный раздел диска.|  
|Выравнивание\=<n>|Выравнивает все экстенты тома или раздела до ближайшей границы выравнивания. *n* число килобайт \(КБ\) с самого начала диска до ближайшей границы выравнивания.|  
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|  
  
## <a name="remarks"></a>Примечания  
  
-   Динамическом диске должно быть свободно не меньше общего размера области неисправный диск в RAID\-том RAID5.  
  
-   В томе RAID\-для выполнения данной операции необходимо выбрать 5 массива. Используйте **выберите том** команду, чтобы выбрать том и перетянуть внимание к нему.  
  
## <a name="BKMK_examples"></a>Примеры  
Чтобы заменить тома с фокусом, заменив его динамический диск 4, введите следующую команду:  
  
```  
repair disk=4  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  

  

