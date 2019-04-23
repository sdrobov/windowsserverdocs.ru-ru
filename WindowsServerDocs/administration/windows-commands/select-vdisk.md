---
title: Выберите виртуальный диск
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: a71a5c15c05a1e969d0720bc8e67e669d553f649
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852575"
---
# <a name="select-vdisk"></a>Выберите виртуальный диск

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Выбирает указанный виртуальный жесткий диск \(VHD\) и перемещает фокус на него.  
  
> [!NOTE]  
> Эта команда применяется только к Windows 7 и Windows Server 2008 R2.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
select vdisk file=<full path> [noerr]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|Файл\=<full path>|Указывает полный путь к файлу и имя существующего файла виртуального жесткого диска.|  
|успешного|Используется только для сценариев. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|  
  
## <a name="BKMK_examples"></a>Примеры  
Чтобы переместить фокус с именем Test.vhd виртуальный жесткий ДИСК, введите:  
  
```  
select vdisk file="c:\test\test.vhd"  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  
-   [подключить виртуальный диск](attach-vdisk.md)  
  
-   [сжать виртуальный диск](compact-vdisk.md)  
  
  
  
-   [Отсоединить виртуальный диск](detach-vdisk.md)  
  
-   [виртуальный диск данных](detail-vdisk.md)  
  
-   [Разверните виртуальный диск](expand-vdisk.md)  
  
-   [Слияние виртуальный диск](merge-vdisk.md)  
  
-   [list_1](list_1.md)  
  

