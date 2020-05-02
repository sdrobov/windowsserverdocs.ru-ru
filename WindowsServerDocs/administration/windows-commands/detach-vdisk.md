---
title: отсоединить виртуальный диск
description: Справочный раздел по отсоединению виртуального жесткого диска (VHD), который останавливает выбранный виртуальный жесткий диск в качестве локального жесткого диска на главном компьютере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5f01dcb8-9237-4564-ad94-8a8dd0fd0cca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e5e64559650597eb8d15e28075f74704fdf338a6
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716670"
---
# <a name="detach-vdisk"></a>отсоединить виртуальный диск

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Останавливает отображение выбранного виртуального жесткого диска (VHD) в качестве локального жесткого диска на главном компьютере. При отсоединении виртуального жесткого диска его можно скопировать в другие расположения.  
  
> [!NOTE]  
> Эта команда применима только к Windows 7 и Windows Server 2008 R2.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
detach vdisk [noerr]  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|Noerr|Используется только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|  
  
## <a name="remarks"></a>Примечания  
  
-   Для выполнения этой операции необходимо выбрать и отсоединить виртуальный жесткий диск. Используйте команду **SELECT VDISK** , чтобы выбрать виртуальный жесткий диск и переместить фокус на него.  
  
## <a name="examples"></a>Примеры  
Чтобы отсоединить выбранный виртуальный жесткий диск, введите:  
  
```  
detach vdisk  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
-   [подключить виртуальный диск](attach-vdisk.md)  
  
-   [Compact VDISK](compact-vdisk.md)  

-   [подробные сведения VDISK](detail-vdisk.md)  
  
-   [развернуть виртуальный диск](expand-vdisk.md)  
  
-   [Слияние VDISK](merge-vdisk.md)  
  
-   [выбрать виртуальный диск](select-vdisk.md)  
  
-   [list_1](list_1.md)  
  

