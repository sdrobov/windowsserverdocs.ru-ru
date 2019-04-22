---
title: Отсоединить виртуальный диск
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 0b6a1ecd3d787506c89f120bed204cc30e6d68d9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59822735"
---
# <a name="detach-vdisk"></a>Отсоединить виртуальный диск

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Останавливает выбранный виртуальный жесткий диск \(VHD\) фигурировало локальном жестком диске на главном компьютере. При отсоединении виртуального жесткого диска, его можно скопировать в другие расположения.  
  
> [!NOTE]  
> Эта команда применяется только к Windows 7 и Windows Server 2008 R2.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
detach vdisk [noerr]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|успешного|Используется только для сценариев. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|  
  
## <a name="remarks"></a>Примечания  
  
-   Виртуальный жесткий ДИСК должен быть выбран и отсоединить для выполнения данной операции. Используйте **выберите виртуальный диск** команду, чтобы выбрать виртуальный жесткий ДИСК и перетянуть внимание к нему.  
  
## <a name="BKMK_Examples"></a>Примеры  
Чтобы отключить выбранный VHD-ФАЙЛ, введите следующую команду:  
  
```  
detach vdisk  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  
-   [подключить виртуальный диск](attach-vdisk.md)  
  
-   [сжать виртуальный диск](compact-vdisk.md)  
  
  
  
-   [виртуальный диск данных](detail-vdisk.md)  
  
-   [Разверните виртуальный диск](expand-vdisk.md)  
  
-   [Слияние виртуальный диск](merge-vdisk.md)  
  
-   [Выберите виртуальный диск](select-vdisk.md)  
  
-   [list_1](list_1.md)  
  

