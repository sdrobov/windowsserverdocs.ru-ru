---
title: выбор Секции
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 9a186e2678fde64396a8b4b57a2d14e4b0b7bf26
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371073"
---
# <a name="select-partition"></a>выбор Секции

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

выбирает указанную секцию и перемещает фокус на нее. Эта команда также может использоваться для вывода раздела, который в данный момент находится на выбранном диске.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
select partition=<n>  
```  
  
## <a name="parameters"></a>Параметры  
  
|   Параметр    |                                                                                    Описание                                                                                    |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Partition @ no__t-0 @ no__t-1 | Номер секции, получающей фокус. Числа для всех разделов на диске, выбранных в данный момент, можно просмотреть с помощью команды **list partition** в DiskPart. |
  
## <a name="remarks"></a>Примечания  
  
-   Перед тем как выбрать раздел, необходимо сначала выбрать диск с помощью команды **Выбор диска** .  
  
-   Если номер секции не указан, эта команда отображает раздел, на котором в данный момент находится фокус на выбранном диске.  
  
-   Если выбран том с соответствующим разделом, раздел будет выбран автоматически.  
  
-   Если секция выбрана с соответствующим томом, том будет выбран автоматически.  
  
## <a name="BKMK_examples"></a>Примеров  
Чтобы переместить фокус на раздел 3, введите:  
  
```  
select partitition=3  
```  
  
Чтобы отобразить раздел, который в данный момент находится на выбранном диске, введите:  
  
```  
select partition  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  

  

