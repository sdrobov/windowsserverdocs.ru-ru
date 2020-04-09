---
title: выбрать виртуальный диск
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8808872a-3523-4205-a6c6-83fa738ee37a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 65e186413bebbf467cd4c2033d274badd1fbea80
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834747"
---
# <a name="select-vdisk"></a>выбрать виртуальный диск

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

выбирает указанный виртуальный жесткий диск \(VHD\) и перемещает фокус на него.  
  
> [!NOTE]  
> Эта команда применима только к Windows 7 и Windows Server 2008 R2.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
select vdisk file=<full path> [noerr]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|<full path>\=файлов|Указывает полный путь и имя существующего файла виртуального жесткого диска.|  
|Noerr|Используется только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|  
  
## <a name="examples"></a><a name=BKMK_examples></a>Примеров  
Чтобы переместить фокус на виртуальный жесткий диск с именем Test. VHD, введите:  
  
```  
select vdisk file=c:\test\test.vhd  
```  
  
## <a name="additional-references"></a>Дополнительные материалы  
  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [подключить виртуальный диск](attach-vdisk.md)  
  
-   [Compact VDISK](compact-vdisk.md)  
  
  
  
-   [Отсоединить виртуальный диск](detach-vdisk.md)  
  
-   [подробные сведения VDISK](detail-vdisk.md)  
  
-   [развернуть виртуальный диск](expand-vdisk.md)  
  
-   [Слияние VDISK](merge-vdisk.md)  
  
-   [list_1](list_1.md)  
  

