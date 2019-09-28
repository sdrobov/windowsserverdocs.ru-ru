---
title: выбрать виртуальный диск
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8808872a-3523-4205-a6c6-83fa738ee37a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1bfa6450d1704cde1e5ff2a50a8e3b61a30d0766
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384192"
---
# <a name="select-vdisk"></a>выбрать виртуальный диск

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

выбирает указанный виртуальный жесткий диск \(VHD @ no__t-1 и перемещает фокус на него.  
  
> [!NOTE]  
> Эта команда применима только к Windows 7 и Windows Server 2008 R2.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
select vdisk file=<full path> [noerr]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|File @ no__t-0 @ no__t-1|Указывает полный путь и имя существующего файла виртуального жесткого диска.|  
|Noerr|Используется только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|  
  
## <a name="BKMK_examples"></a>Примеров  
Чтобы переместить фокус на виртуальный жесткий диск с именем Test. VHD, введите:  
  
```  
select vdisk file="c:\test\test.vhd"  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [подключить виртуальный диск](attach-vdisk.md)  
  
-   [Compact VDISK](compact-vdisk.md)  
  
  
  
-   [Отсоединить виртуальный диск](detach-vdisk.md)  
  
-   [подробные сведения VDISK](detail-vdisk.md)  
  
-   [развернуть виртуальный диск](expand-vdisk.md)  
  
-   [Слияние VDISK](merge-vdisk.md)  
  
-   [list_1](list_1.md)  
  

