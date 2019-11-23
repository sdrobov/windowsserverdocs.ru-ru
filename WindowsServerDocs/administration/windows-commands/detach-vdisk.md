---
title: Отсоединить виртуальный диск
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f01dcb8-9237-4564-ad94-8a8dd0fd0cca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4850f9f17218178f210820dd4c6ca96fd918accc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378690"
---
# <a name="detach-vdisk"></a>Отсоединить виртуальный диск

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Останавливает выбранный виртуальный жесткий диск \(\) VHD в качестве локального жесткого диска на главном компьютере. При отсоединении виртуального жесткого диска его можно скопировать в другие расположения.  
  
> [!NOTE]  
> Эта команда применима только к Windows 7 и Windows Server 2008 R2.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
detach vdisk [noerr]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|Noerr|Используется только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|  
  
## <a name="remarks"></a>Замечания  
  
-   Для выполнения этой операции необходимо выбрать и отсоединить виртуальный жесткий диск. Используйте команду **SELECT VDISK** , чтобы выбрать виртуальный жесткий диск и переместить фокус на него.  
  
## <a name="BKMK_Examples"></a>Примеров  
Чтобы отсоединить выбранный виртуальный жесткий диск, введите:  
  
```  
detach vdisk  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [подключить виртуальный диск](attach-vdisk.md)  
  
-   [Compact VDISK](compact-vdisk.md)  
  
  
  
-   [подробные сведения VDISK](detail-vdisk.md)  
  
-   [развернуть виртуальный диск](expand-vdisk.md)  
  
-   [Слияние VDISK](merge-vdisk.md)  
  
-   [выбрать виртуальный диск](select-vdisk.md)  
  
-   [list_1](list_1.md)  
  

