---
title: Выберите секцию
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 25f70083-b8f7-4a8e-9b34-4b3ffbe06670
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c7d5675aa6c33ddbe1e5e873e1a7cf7a2e8f8017
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59824965"
---
# <a name="select-partition"></a>Выберите секцию

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Выбирает указанный раздел и перемещает фокус на него. Эта команда также может использоваться для отображения раздела, который в данный момент имеет фокус в выбранный диск.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
select partition=<n>  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|секции\=<n>|Номер раздела, получающего фокус. Можно просмотреть номера для всех разделов на диске, выделенного с помощью **списка секции** в DiskPart.|  
  
## <a name="remarks"></a>Примечания  
  
-   Перед тем как выбрать секцию необходимо сначала выбрать диск с помощью **выберите диск** команды.  
  
-   Если номер секции не указан, эта команда отображает секцию, которая в данный момент имеет фокус в выбранный диск.  
  
-   Если том с соответствующей секции, секции выбирается автоматически.  
  
-   Если выбрана секция с соответствующим томом, том будет определяться автоматически.  
  
## <a name="BKMK_examples"></a>Примеры  
Чтобы переместить фокус раздел 3, введите:  
  
```  
select partitition=3  
```  
  
Чтобы отобразить секцию, которая в данный момент имеет фокус в выбранный диск, введите следующую команду:  
  
```  
select partition  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  

  

