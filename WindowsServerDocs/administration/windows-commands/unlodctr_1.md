---
title: unlodctr
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: e1a662da10acc65b4ad2fd0d055cf9d46de603be
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59886655"
---
# <a name="unlodctr"></a>unlodctr

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет имена счетчиков производительности и текст описания для службы или драйвера устройства из системного реестра.   

## <a name="syntax"></a>Синтаксис  
```  
Unlodctr <DriverName>   
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|\<DriverName >|Удаляет производительности, счетчик параметры имени и текст для драйвера или службы, описания <DriverName> из реестра Windows Server 2003.|  
|/?|Отображение справки в командной строке.|  

## <a name="remarks"></a>Примечания  
> [!WARNING]  
> Неправильное изменение реестра может серьезно повредить систему. Перед внесением изменений следует сделать резервную копию всех ценных данных на компьютере.  

Если сведения, которые вы предоставляете содержит пробелы, используйте кавычки вокруг текста (например, "<DriverName>«).  

## <a name="BKMK_Examples"></a>Примеры  
Чтобы удалить текущие параметры реестра производительности и счетчиков текст описания для службы передачи протокола SMTP (Simple Mail):  
```  
unlodctr SMTPSVC  
```  
## <a name="additional-references"></a>Дополнительная справка  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  
