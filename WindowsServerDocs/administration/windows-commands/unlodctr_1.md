---
title: unlodctr
description: Справочный раздел по lodctr, в котором удаляются имена счетчиков производительности и поясняющий текст для службы или драйвера устройства из системного реестра.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fc8aa6f0-c1d9-47ea-937a-28152148e774
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 56b6310dd48537c1f68780666efef750e12daf7d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721173"
---
# <a name="unlodctr"></a>unlodctr

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет имена **счетчиков производительности** и **поясняющий** текст для службы или драйвера устройства из системного реестра.   

## <a name="syntax"></a>Синтаксис  
```  
Unlodctr <DriverName>   
```  
#### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|\<> Имя_драйвера|Удаляет параметры имени счетчика производительности и поясняющий текст для драйвера или <DriverName> службы из реестра Windows Server 2003.|  
|/?|Отображение справки в командной строке.|  

## <a name="remarks"></a>Примечания  
> [!WARNING]  
> Неправильное изменение реестра может серьезно повредить систему. Перед внесением изменений следует сделать резервную копию всех ценных данных на компьютере.  

Если предоставленные сведения содержат пробелы, заключите текст в кавычки (например, <DriverName>).  

## <a name="examples"></a>Примеры  
Чтобы удалить текущие параметры реестра производительности и текст объяснения счетчика для службы SMTP:  
```  
unlodctr SMTPSVC  
```  
## <a name="additional-references"></a>Дополнительная справка  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
