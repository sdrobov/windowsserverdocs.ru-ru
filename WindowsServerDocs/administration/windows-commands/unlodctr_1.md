---
title: unlodctr
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc8aa6f0-c1d9-47ea-937a-28152148e774
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 85a66b521f404358705962078f33af4bec1ebae5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363902"
---
# <a name="unlodctr"></a>unlodctr

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет имена счетчиков производительности и поясняющий текст для службы или драйвера устройства из системного реестра.   

## <a name="syntax"></a>Синтаксис  
```  
Unlodctr <DriverName>   
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|\<Имя_драйвера >|Удаляет параметры имени счетчика производительности и поясняющий текст для <DriverName> драйвера или службы из реестра Windows Server 2003.|  
|/?|Отображение справки в командной строке.|  

## <a name="remarks"></a>Замечания  
> [!WARNING]  
> Неправильное изменение реестра может серьезно повредить систему. Перед внесением изменений следует сделать резервную копию всех ценных данных на компьютере.  

Если предоставленные сведения содержат пробелы, заключите его в кавычки (например, "<DriverName>").  

## <a name="BKMK_Examples"></a>Примеров  
Чтобы удалить текущие параметры реестра производительности и текст объяснения счетчика для службы SMTP:  
```  
unlodctr SMTPSVC  
```  
## <a name="additional-references"></a>Дополнительная справка  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
