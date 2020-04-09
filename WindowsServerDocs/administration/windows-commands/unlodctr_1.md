---
title: unlodctr
description: Раздел команд Windows для lodctr, который удаляет имена счетчиков производительности и поясняющий текст для службы или драйвера устройства из системного реестра.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fc8aa6f0-c1d9-47ea-937a-28152148e774
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fe7fc3c9eafefd59a5daab625e3af06b6addd292
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832261"
---
# <a name="unlodctr"></a>unlodctr

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет имена **счетчиков производительности** и **поясняющий** текст для службы или драйвера устройства из системного реестра.   

## <a name="syntax"></a>Синтаксис  
```  
Unlodctr <DriverName>   
```  
#### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|\<Имя_драйвера >|Удаляет параметры имени счетчика производительности и поясняющий текст для <DriverName> драйвера или службы из реестра Windows Server 2003.|  
|/?|Отображает справку в командной строке.|  

## <a name="remarks"></a>Примечания  
> [!WARNING]  
> Внесение неправильных изменений в реестр может нанести серьезный вред системе. Перед внесением изменений следует создать резервные копии всех важных данных, имеющихся на компьютере.  

Если предоставленные сведения содержат пробелы, заключите текст в кавычки (например, <DriverName>).  

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Чтобы удалить текущие параметры реестра производительности и текст объяснения счетчика для службы SMTP:  
```  
unlodctr SMTPSVC  
```  
## <a name="additional-references"></a>Дополнительная справка  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
